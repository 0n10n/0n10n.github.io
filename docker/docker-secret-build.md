# Docker里怎么传递私密信息

## Squash方式

从 1.13 开始，引入了一个新的 `--squash` 参数。
parameter was added. It can be used to reduce the size of an image by removing files which are not present anymore, and reduce multiple layers to a single one between the origin and the latest stage. You’ll need to run the daemon with experimental features enabled to use it.

This has also the convenient side effect, of removing files which were created and then deleted. Handy to get rid of files containing secret information which you don’t want to have around anymore. You tell docker to squash away layers when executing docker build:

```
$ docker build --squash [...]
```

This approach works, but it has a few potential downsides. If you make a mistake and push an image without squashing it, you risk leaking the thing you wanted to keep private. You will still see ARG values when viewing the history of the image. Also, you’re not making use of Docker layer caching as much as you could. There is a more elegant way by now - multi-stage builds.

## 多阶段Build方式

When working with multi-stage builds, you are building multiple Docker images in a single Dockerfile, but only the last one is the real result. The other ones are there to support it. Anything but the final image don’t leave any traces.

This is really convenient for handling secrets! You simply provide your private SSH key to one of the intermediate images, use it to install dependencies, download the data or clone a Git repository, and pass directories containing that data into your final image build process, while leaving the secret credentials safe and sound in the intermediate image.

> As a sidenote: it’s a good idea to create dedicated SSH deploy keys for such tasks, which are disposable, can be disabled easily, only have read-access and don’t need a passphrase to unlock.

Here is an example of a multi-stage Dockerfile:

```
# this is our first build stage, it will not persist in the final image
FROM ubuntu as intermediate

# install git
RUN apt-get update
RUN apt-get install -y git

# add credentials on build
ARG SSH_PRIVATE_KEY
RUN mkdir /root/.ssh/
RUN echo "${SSH_PRIVATE_KEY}" > /root/.ssh/id_rsa

# make sure your domain is accepted
RUN touch /root/.ssh/known_hosts
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts

RUN git clone git@bitbucket.org:your-user/your-repo.git

FROM ubuntu
# copy the repository form the previous image
COPY --from=intermediate /your-repo /srv/your-repo
# ... actually use the repo :)
```

There are two images defined here. One of them is named “intermediate”, the final one doesn’t have a name. The “intermediate” image is referenced, and we’re copying the repository data over from it into the final image.

The `SSH_PRIVATE_KEY` is passed when issuing the build command with `--build-arg` or in the build block of your docker-compose.yml file. That ARG variable is not used in the final image, the value will not be available using the *history* command.

Using multi-stage builds also has the great side effect of **significantly** reducing the size of your final Docker images, as they don’t need to contain traces of Git and other build tools if used correctly.

## 用Docker BuildKit的secret 参数
用BuildKit方式build（https://docs.docker.com/develop/develop-images/build_enhancements/）:
```bash
$ DOCKER_BUILDKIT=1 docker build .
```
或者编辑` /etc/docker/daemon.json `，加入
```
{ "features": { "buildkit": true } }
```

```
export DOCKER_BUILDKIT=1
```

Docker BuildKit brought along cool new features. One of them, is the secret mount type can give a single RUN command access to one or multiple secrets without leaving behind traces inside of the file system if used right. You can specify a secret from a file when running your build command:

docker build --secret id=yoursecret,src=/host/secret/file/path
You can give single RUN instructions access to this secret. By default this creates a file inside of /run/secrets/secretid, but you can also specify a target path of your choice.

RUN --mount=type=secret,id=yoursecret ...
RUN --mount=type=secret,id=yoursecret,target=/target/path/to/secret ...
The file is created and cleaned up automatically so it won’t leave behind any traces in the final layer, unless you write the exact same data to disk yourself.