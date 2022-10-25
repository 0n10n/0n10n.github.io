## 编解码命令行使用

- 打印字符串的16进制编码：
```bash
# 用空格分隔
$ echo -n "Hello" | od -A n -t x1
#运行结果： 48 65 6c 6c 6f
```
```bash
# 不用空格分隔
$ echo -n "Hello" | od -A n -t x1 | sed 's/ //g'
#运行结果：48656c6c6f
```

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

- 把文件用16进制显示出来
```bash
$ xxd file_name
$ xxd file_name > file_name.dump #接着可以用文本编辑器随意修改文件内容
$ xxd -r file_name.dump > file_name.new #结合上一条命令，得到修改后的二进制文件
$ echo "436f6d7075746572486f70650a" | xxd -r -p > computerhope.txt #把一串16进制字符存成文件
$ echo -n "A" | xxd -p #打印出A字符的16进制表达
```
- 每隔两个字符，插入一个“%”符号
```bash
echo '10000000C988CBE0' | sed 's/../&:/g;s/:$//'
```

- 结合上面的xxd命令，可以得到一个对文件的url编码命令行
```bash
xxd -p gb2312.txt  |sed  's/../%&/g;s/:$//'
```
