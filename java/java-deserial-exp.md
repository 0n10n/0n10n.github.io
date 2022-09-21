## Apereo CAS RCE漏洞

- [Apereo CAS RCE漏洞复现](https://oopsdc.com/post/apereo-cas-rce%E6%BC%8F%E6%B4%9E%E5%A4%8D%E7%8E%B0/#:~:text=%E6%BC%8F%E6%B4%9E%E6%8F%8F%E8%BF%B0%20Apereo%20CAS%20%E6%98%AF2002%E5%B9%B4%E8%80%B6%E9%B2%81%E5%A4%A7%E5%AD%A6%E5%AE%9E%E9%AA%8C%E5%AE%A4%E6%8E%A8%E5%87%BA%E7%9A%84%E4%B8%80%E4%B8%AA%E5%BC%80%E6%BA%90%E7%BB%9F%E4%B8%80%E8%AE%A4%E8%AF%81%E6%9C%8D%E5%8A%A1%EF%BC%8C%20CAS%20%E5%8D%B3%20Central%20Authentication,Service%20%EF%BC%8C%E5%85%B6%E6%BC%8F%E6%B4%9E%E6%88%90%E5%9B%A0%E5%9C%A8%E4%BA%8E%20Webflow%20%E4%B8%AD%E4%BD%BF%E7%94%A8%E4%BA%86%E9%BB%98%E8%AE%A4%E5%AF%86%E9%92%A5%20changeit%20%EF%BC%8C%E6%94%BB%E5%87%BB%E8%80%85%E5%8F%AF%E9%80%9A%E8%BF%87%E9%BB%98%E8%AE%A4%E5%AF%86%E9%92%A5%E8%A7%A6%E5%8F%91%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96%E6%BC%8F%E6%B4%9E%EF%BC%8C%E5%AE%9E%E7%8E%B0%20RCE%20%E3%80%82)

- [Vulhub 漏洞学习之：Apereo CAS](https://www.cnblogs.com/f-carey/p/15889083.html)
- [五分钟复现apereo-cas反序列化命令执行](https://www.codeleading.com/article/86125398179/)
- [apereo CAS 4.1 deserialization Command Execution Vulnerability](https://chowdera.com/2021/12/202112291329324255.html)
- [Apereo-CAS 4.1.5 RCE漏洞复现](https://www.programminghunter.com/article/66932287013/)
- [Apereo Cas 4.1.x 反序列化命令执行漏洞](https://www.ol4three.com/2020/12/29/WEB/Exploit/Apereo-cas/Apereo-Cas-4-1-x-%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96%E5%91%BD%E4%BB%A4%E6%89%A7%E8%A1%8C%E6%BC%8F%E6%B4%9E/)
- 利用工具：https://github.com/vulhub/Apereo-CAS-Attack
- 利用工具：https://github.com/MrMeizhi/ysoserial-mangguogan 解码数据

https://github.com/apereo/cas  cas源代码
https://hub.docker.com/r/apereo/cas/tags docker

https://github.com/phith0n/zkar ZKar is a Java serialization protocol analysis tool implement in Go.