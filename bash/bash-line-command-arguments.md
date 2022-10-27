# Bash 命令行相关的特殊参数

收集一下Bash命令行相关的常见变量。几个名词解释：

- 参数（parameter）是存放数值的实体；
- 变量（variables）是特定shell脚本里，由用户定义的参数。
- 特殊参数（Special parameters）是由shell预定义和维护的只读变量。

| 序号 | 特殊参数名称 | 描述                                                         |
| :--- | :---------: | :------------------------------------------ |
| 1    | $#       | 代表传给shell脚本的参数数量                                  |
| 2    | $0       | 代表shell脚本的文件名                                        |
| 3    | $i       | 代表传给shell的第几个参数：$1,$2                             |
| 4    | $\*      | 代表传给脚本的全部参数                                       |
| 5    | $!       | 代表在背景运行的最后一个程序的 PID                           |
| 6    | $?       | 最后一条命令运行后的退出状态码。0代表成功；1代表失败         |
| 7    | $_       | 上一条命令使用的最后一个参数                                 |
| 8    | $$       | 当前脚本的 PID                                               |
| 9    | $@       | 当前收到的所有参数的数组形式。类似 `$*`                      |
| 10   | $-       | 当前set命令设置的选项值。具体参见：https://www.gnu.org/software/bash/manual/bash.html#The-Set-Builtin 里的每个 `-选项` 。如 ` set -e && echo $- ` 会打印出 `ehB`。 `e`就来自 `-e`，`hB`来自默认值，代表的含义见上面的文档。 |

包含上述各种特殊参数的脚本示例：

```
#!/bin/bash

echo "Number of argument passed: $#"
echo "Script name is $0"
echo "The 2nd argument passed is: $2"
echo "Arguments passed to script are: $*"
echo "Exit status of last command that executed:$?" #This is the previous command for $_
echo "Last argument provide to previous command:$_"
echo "PID of current shell is: $$"
echo "Flags are set in the shell: $-"
```

![](https://media.geeksforgeeks.org/wp-content/uploads/20210418152230/202104181521.png)


#### 应用举例

- 如果参数的数量是 0，结束程序。
- 如果不是0
  - 把第一个参数的值给 maxEle
  - 循环所有的参数。每个参数都和 `maxEle`对比大小，如果该参数更大，就替换掉 `maxEle` 的值。

```bash
# 检查传进来的参数个数是否为0
if [ "$#" = 0 ]
then
    #如果没有参数，退出程序
    echo "No arguments passed."
    exit 1
fi
  
#用第一个参数初始化maxEle的值

maxEle=$1
  
#挨个循环各个参数，把大的数字赋给 maxEle 
for arg in "$@"
do
    if [ "$arg" -gt "$maxEle" ]
    then
        maxEle=$arg
    fi
done
echo "Largest value among the arguments passed is: $maxEle"
```