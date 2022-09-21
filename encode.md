## 编解码命令行使用

- 把一个图片（其实任何文件都可以啦！）编码成Base64字符串：
```bash
$ base64 -w 0 $pic_file
```
- Base64解码和编码图片文件：
```bash
$ base64 -w 0 $pic_file >base64.txt
$ cat base64.txt |base64 -d > new$pic_file
```
- 对文件的每一行单独做base64编码：
```bash
$ while IFS= read -r line; do echo $line|base64 -w 0 - && echo  ; done < /etc/passwd
```
- 对文件的每一行做base64解码：

```bash
$ while IFS= read -r line; do echo $line|base64 -d - ; done <  ./encodefile.txt
```

- url编解码（python方式）：

```bash
$ alias urldecode='python3 -c "import sys, urllib.parse as ul; \
    print(ul.unquote_plus(sys.argv[1]))"'

$ alias urlencode='python3 -c "import sys, urllib.parse as ul; \
    print (ul.quote_plus(sys.argv[1]))"'
```