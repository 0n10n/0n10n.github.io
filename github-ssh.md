# 用ssh协议访问Github Repo，规避网络连接问题

最近打算把github用起来，但你懂的，我们伟大的Wall处处是绊脚石啊！这段提示最近把我看吐了...

```
fatal: unable to access 'https://github.com/ineo6/hosts/': OpenSSL SSL_read: Connection was reset, errno 10054
```

虽说谁没个梯子啥的，但有时候用梯子确实有点不太方便，不是每个虚拟机环境都有梯子的。也根据网上各位大佬的经验，改过这些，但也不太管用啊。

>  git config --global http.postBuffer 1048576000  
> git config --global http.sslVerify false  
> git config --global core.compression -1   

最后发现，最好的办法还是改用ssh。不过这个就要给自己的git客户端配置ssh证书了。 简单记录一下方法，免得以后忘了。

执行：`ssh-keygen -o`，获得公钥文件 `id_rsa.pub` 和私钥文件`id_rsa` 。默认路径：`$HOME/.ssh` (Linux) 和 `%USERPROFILE%\.ssh` (Windows)。

用文本编辑器打开 `id_rsa.pub` ，把内容填入 https://github.com/settings/keys 的【New SSH Key】。

默认这样就可以了。如果私钥文件不在默认位置，可以通过以下命令设定一下：

>  git config --global core.sshCommand "ssh -i 'c:/Users/YourName/.ssh/id_rsa'"  
>  \# 再确认一下：  
>  git config -l

再修改自己本地库的 `.git/config` 文件，把远程库的路径，从这种格式：

```
[remote "origin"]
	url = https://github.com/ineo6/hosts
	fetch = +refs/heads/*:refs/remotes/origin/*
```

改为：

```
[remote "origin"]
	url = git@github.com:/ineo6/hosts
	fetch = +refs/heads/*:refs/remotes/origin/*
```

然后就一切顺畅了！“Connection reset” Byebye！