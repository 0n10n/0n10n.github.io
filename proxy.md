## GO Proxy相关
### 1，GO编译时使用代理

可以用的代理：

```
goproxy
https://goproxy.io/zh/

Qi Niuyun
https://goproxy.cn

Ali Cloud
https://mirrors.aliyun.com/goproxy/
```

**配置使用代理（Bash)**

```shell
# 配置 GOPROXY 环境变量
export GOPROXY=https://proxy.golang.com.cn,direct
export GO111MODULE=on
# 还可以设置不走 proxy 的私有仓库或组，多个用逗号相隔（可选）
export GOPRIVATE=git.mycompany.com,github.com/my/private
```

**配置使用代理 PowerShell (Windows)**

```shell
# 配置 GOPROXY 环境变量
$env:GOPROXY = "https://proxy.golang.com.cn,direct"
# 还可以设置不走 proxy 的私有仓库或组，多个用逗号相隔（可选）
$env:GOPRIVATE = "git.mycompany.com,github.com/my/private"
```

### 2，proxify的证书问题

用openssl查看站点https信息：

> openssl s_client -connect $host-ip:443

> \# 查看https站点对各种算法的支持程度
> $ gotlsscan -host www.domain.name
> \# 查出https站点支持的算法
> $ gotlsscan -host www.domain.name | grep -v NOT

编辑：`~/.bash_profile`(个人) 或 `/etc/environment`(全局)，加入`代理服务器IP:端口`设置。

> export http_proxy=localhost:8888
> export https_proxy=localhost:8888
> #exprot no_proxy=localhost, 127.0.0.1, *.my.lan
> curl --cacert /root/.config/proxify/cacert.pem --tlsv1.1  https://www.baidu.com

## mitmproxy 

App 爬虫神器！Mitmproxy 快速带你入坑 https://zhuanlan.zhihu.com/p/142231209