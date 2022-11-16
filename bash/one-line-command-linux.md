# Useful Command

### 查看TCP连接以及对应的程序
```
ss -t -p
```
查看所有连接：`ss -a`
只看监听状态的：`ss -l`
只看特定来源IP：`ss src 104.21.3.132`
只看特定目标IP：`ss dst 104.21.3.132`

### 修改终端文件夹背景颜色
```
LS_COLORS="ow=01;36;40" && export LS_COLORS
```
### git提交忽略文件

```bash
git config --global core.excludesfile ~/.gitignore
```

### 移动指定后缀到目录下

```bash
##{}代表前面一个命令的返回结果
find . -name "*.log" -exec mv {} ../test \;` `find ./ -name '*.log' | xargs cp -t test
```
### 获取几天/小时前/后的时间点
```bash
date --date="1 day ago" +"%Y-%m-%d %H:%M:%S " #一天前的时间
date --date="30 minutes ago" +"%Y-%m-%d %H:%M:%S "  #30分钟前
date --date="-1 day ago" +"%Y-%m-%d %H:%M:%S " #一天后的时间
```

### 网络防火墙开放端口

#### CentOS/RHEL 6

```bash
iptables -A INPUT -p tcp --dport 1521 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1521 -j ACCEPT
service iptables save
service iptables status
```

#### CentOS/RHEL 7/8
```bash
$ firewall-cmd --zone=public --permanent --add-port 5005/tcp
$ firewall-cmd --reload
$ firewall-cmd --list-all
```

#### Ubuntu

```bash
$ ufw allow 5005
$ ufw status
```