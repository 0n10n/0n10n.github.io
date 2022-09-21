# Redis

## 参考

文档：

命令：https://redis.io/commands/

协议简介：：https://redis.io/docs/reference/protocol-spec/
RESP



## 常用命令



把redis服务器设置为从服务器，为它指定一个主服务器

```
REPLICAOF host port
```

关掉从服务器身份
```
REPLICAOF  no one
```

