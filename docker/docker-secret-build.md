# Docker里怎么传递私密（私钥）信息

前情提要看这里“《[用ssh协议访问Github Repo，规避网络连接问题](github-ssh.md)》”。ssh方式访问github真是比https方式稳定好用多了（当然是在咱们这国情下）。自己机器里这么用特别方便，但这几天在热衷搞Dockerfile，就发现要在Docker里用ssh私钥就没那么方便了，毕竟搞Docker都是为了方便分享，总不能把私钥也打包进去吧，就琢磨了一下这事情：怎么在Docker里传递私密信息。

从直觉上来说，在Docker里打包私密文件，好像可以先ADD私密文件，之后再执行删除，比如这样地写（留意最后一行删除文件的动作）：
```bash
FROM alpine:latest

RUN apk add --update \
  ca-certificates \
  coreutils \
  curl \
  git \
  openssl \
  openssh \
  openssh-client-common

RUN mkdir /root/.ssh/
ADD id_rsa  /root/.ssh/id_rsa

RUN chmod 0600 /root/.ssh/id_rsa \
&& touch /root/.ssh/known_hosts \
&& ssh-keyscan github.com >> /root/.ssh/known_hosts

RUN git clone git@github.com:/0n10n/d0ckfile
RUN rm /root/.ssh/id_rsa
```

但这样得到的镜像，用如下命令：`docker history --no-trunc $image_name | tac | tr -s ' ' | cut -d " " -f 5- | sed 's,^/bin/sh -c #(nop) ,,g' | sed 's,^/bin/sh -c,RUN,g' | sed 's, && ,\n & ,g' | sed 's,\s*[0-9]*[\.]*[0-9]*\s*[kMG]*B\s*$,,g' | head -n -1`  能得到具体的每一步骤。

使用以下命令，就能从Docker的文件系统中，把这个曾经删掉的文件再捞回来：

```bash
$ cd /var/lib/docker && find . |grep id_rsa

./overlay2/999919b1e89a62d4f130fc48edb44ba16545d31e35dec718f04ea7f61065ae5c/diff/root/.ssh/id_rsa
./overlay2/1d65d5d719697625f73351b528ff9e4d22ea85f704b6de6a63372377f0a686b6/diff/root/.ssh/id_rsa
./overlay2/81f193a5e10ce357abb17b219aae1d68dd8ed0ecfe94b07f73377cd604c3a1fa/diff/root/.ssh/id_rsa
```

所以这种方式是不可靠的！只要是曾经被添加过的文件，依然还是会保存在Docker的文件系统里。

## 多阶段Build方式

多阶段build的方式，是在 Dockerfile 里设定多个Docker镜像，但只有最后一个镜像才是真正的Build成果。其他的镜像都是支撑最后一个镜像的，编译完成后前面的镜像就不再用了，在最终镜像里并不会留有前面镜像的印记。

这种机制就非常适合保存私密信息。譬如把私钥在支撑用的镜像里，从github里下载完需要的数据和仓库，安装完需要的依赖程序后，把需要的内容复制到最后的镜像里，这样放在过渡用的镜像里的隐私信息如私钥就可以不用管啦。

比如下面的例子，用私钥通过ssh方式克隆一个仓库，编译完后，把得到的执行文件复制到最终的镜像里。第一个镜像里放入私钥，完成依赖环境的准备以及程序的编译；第二个镜像只需要获得编译出来的程序即可，不需要关心私钥的事情了。

```dockerfile
FROM golang:alpine3.16 as builder
RUN apk add --update \
  ca-certificates \
  curl \
  git \
  openssl \
  openssh \
  openssh-client-common

RUN mkdir /root/.ssh/
ADD id_rsa  /root/.ssh/id_rsa

RUN chmod 0600 /root/.ssh/id_rsa \
&& touch /root/.ssh/known_hosts \
&& ssh-keyscan github.com >> /root/.ssh/known_hosts

RUN git clone git@github.com:/jaeles-project/gospider@latest
RUN cd gospider && export GOPROXY=https://proxy.golang.com.cn,direct && GO111MODULE=on go build .

FROM alpine:3.16
RUN apk --no-cache add bash
COPY --from=builder /gospider/gospider  /usr/local/bin/gospider

ENTRYPOINT ["gospider"]
CMD ["-h"]
```

Dockerfile里有两个镜像`golang:alpine3.16`和`alpine:3.16`。在`golang:alpine3.16`里做编译，再通过`alias`别名`builder`的引用，把gospider程序复制添加到最终需要的镜像里。

上面例子里是直接复制了一个私钥文件，也可以通过 `--build-arg` 参数的方式，把私钥信息赋给用作编译环境的镜像。
```dockerfile
ARG SSH_PRIVATE_KEY
RUN echo "${SSH_PRIVATE_KEY}" > /root/.ssh/id_rsa
```
使用多阶段编译的另外一个好处，能极大地缩小了最后真正使用的镜像的体积。

想知道这个中间文件到底是否存在，可以执行：
```bash
$ sudo find  /var/lib/docker -name id_rsa
```
如果搜出来的结果还有，说明中间镜像还存在。需要先执行 `docker rmi 中间镜像id` 后再搜索文件。


## 用Docker BuildKit的secret 参数

另一种是用Docker BuildKit方式。

关于Docker BuildKit详见： https://docs.docker.com/develop/develop-images/build_enhancements/ 。

启用BuildKit的方式：

```bash
$ DOCKER_BUILDKIT=1 docker build .
```
或者编辑` /etc/docker/daemon.json `，加入
```json
{ "features": { "buildkit": true } }
```
Buildkit 给docker build命令新增了一个叫 `--secret` 的参数。用  `--secret`  引用的资源，会以`tmpfs` 文件系统格式，挂载成位于 `/run/secrets` 目录下的一个临时文件，文件名就是指定的`id`,且这个临时文件，只存在于当前这个文件层 layer。
```dockerfile
FROM alpine:latest

RUN apk add --update ca-certificates curl
  
RUN --mount=type=secret,id=little_secret cat /run/secrets/little_secret

```

然后在执行build命令的时候，就要对应地给这个设定的`id`，提供一个对应的文件（`src`），如：

```bash
$ DOCKER_BUILDKIT=1 docker build --secret id=little_secret,src=/host/secret/file/path .
```

可见，在Dockerfile和build命令里，要使用一直的配套的`id` 设定，把宿主机上包含隐秘信息的`src`文件，用安全的方式，临时地提供给某个容器的文件层使用。在容器里，还可以用`target`，把这个文件指定为特定目录下的文件。

```dockerfile
RUN --mount=type=secret,id=little_secret ...
RUN --mount=type=secret,id=little_secret,target=/target/path/to/secret ...
```

这种文件在容器里的创建和清理都是自动的。

