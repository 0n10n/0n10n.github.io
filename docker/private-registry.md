# 部署自己的私有化仓库



## 1，安装docker-compose
```
$ mkdir -p ~/.docker/cli-plugins/
$ curl -SL https://github.com/docker/compose/releases/download/v2.18.1/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
$ chmod +x ~/.docker/cli-plugins/docker-compose
# 确认版本
$ docker compose version

```

## 2，基本部署步骤：
https://docs.docker.com/registry/deploying/

docker-compose.yaml文件：
```
version: "3"

services:
  registry:
    restart: always
    image: registry:2
    ports:
      - 5000:5000
    environment:
      REGISTRY_HTTP_TLS_CERTIFICATE: /certs/cert.pem
      REGISTRY_HTTP_TLS_KEY: /certs/privkey.pem
      REGISTRY_AUTH: htpasswd
      REGISTRY_AUTH_HTPASSWD_PATH: /auth/htpasswd
      REGISTRY_AUTH_HTPASSWD_REALM: Registry Realm

    volumes:
      - /docker/data:/var/lib/registry
      - /docker/certs:/certs
      - /docker/auth:/auth
```
```
# 创建用户身份校验文件
$ cd /docker/auth
$ htpasswd -Bc htpasswd admin
```
### 调试命令：

```
#查看日志
docker compose logs
```
## 3，客户端解决证书报警的问题

#### 做法1：设置docker客户端无需校验证书：

编辑  /etc/docker/daemon.json，加入

```
{
  "insecure-registries" : ["https://aws.debagua.com:5000"]
}
```

 systemctl restart docker

#### 做法2：把自己的CA证书导入到系统里。

先获得服务器端的CA证书：


  ```
  openssl s_client -showcerts -connect [registry_address]:[registry_port] < /dev/null | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ca.crt
  ```

- 如果是CentOS/Redhat系列，把上面的证书放到：/etc/pki/ca-trust/source/anchors，然后执行 `update-ca-trust`

- 如果是Ubuntu系列：

```
sudo cp ca.crt /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

重启docker服务： `systemctl restart docker`

#### 查看系统支持的CA
```
$ locate .pem | grep "\.pem$" | xargs -I{} openssl x509 -issuer -enddate -noout -in {}
$ trust list --filter=ca-anchors
```


## 使用私有库
```
$ docker pull ubuntu:16.04
$ docker tag ubuntu:16.04 aws.debagua.com:5000/my-ubuntu
$ docker push aws.debagua.com:5000/my-ubuntu
$ docker pull aws.debagua.com:5000/my-ubuntu
```
