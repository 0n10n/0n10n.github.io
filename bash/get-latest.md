#### 获得docker-compose 最新版本号：

```bash
$ curl https://github.com/docker/compose/releases|grep -E  \/v.*?\/docker-compose-linux |head -1 |awk -F/ '{ print $6}'

```

#### 获得 docker-php-extension-installer 最新版本号
```bash
 curl https://github.com/mlocati/docker-php-extension-installer/releases |grep -Eo 'v[0-9]+\.[0-9]+\.[0-9]+' |head -1
```