五分钟带你了解啥是JWT
https://zhuanlan.zhihu.com/p/86937325

JSON Web Token 入门教程
http://www.ruanyifeng.com/blog/2018/07/json_web_token-tutorial.html

jwt token encode/decode tool
https://jwt.io/

离线工具：

```
#hashcat
hashcat -m 16500 -a 0 jwt.txt .\wordlists\rockyou.txt
#https://github.com/Sjord/jwtcrack
python crackjwt.py eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjoie1widXNlcm5hbWVcIjpcImFkbWluXCIsXCJyb2xlXCI6XCJhZG1pblwifSJ9.8R-KVuXe66y_DXVOVgrEqZEoadjBnpZMNbLGhM8YdAc /usr/share/wordlists/rockyou.txt
#John
john jwt.txt --wordlist=wordlists.txt --format=HMAC-SHA256
#https://github.com/ticarpi/jwt_tool
python3 jwt_tool.py -d wordlists.txt <JWT token>
#https://github.com/brendan-rius/c-jwt-cracker
./jwtcrack eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjoie1widXNlcm5hbWVcIjpcImFkbWluXCIsXCJyb2xlXCI6XCJhZG1pblwifSJ9.8R-KVuXe66y_DXVOVgrEqZEoadjBnpZMNbLGhM8YdAc 1234567890 8
#https://github.com/mazen160/jwt-pwn
python3 jwt-cracker.py -jwt eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJkYXRhIjoie1widXNlcm5hbWVcIjpcImFkbWluXCIsXCJyb2xlXCI6XCJhZG1pblwifSJ9.8R-KVuXe66y_DXVOVgrEqZEoadjBnpZMNbLGhM8YdAc -w wordlist.txt
#https://github.com/lmammino/jwt-cracker
jwt-cracker "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ" "abcdefghijklmnopqrstuwxyz" 6
```

JWT漏洞练习平台：https://github.com/mbouamama/myjwt/
上述平台的中文介绍：https://www.freebuf.com/sectool/262183.html

https://github.com/reykario/testing-jwt-vulnerability
100|Josefina Sipes II|[retta.rempel@hotmail.com](mailto:retta.rempel@hotmail.com)|$2y$10$HeDKUa77L70cRt6jykCGZejz2stRXFTx.y/.1czHBk1ytjJ4FJi0C|XpGEixL8M3|2020-12-21 10:04:38|2020-12-21 10:10:37