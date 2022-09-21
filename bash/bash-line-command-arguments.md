Here, we are going to see what are the special Parameters of the shell script. Before that first, let’s understand what is parameters in the shell. The parameter is the entity that stores the value. The **variables** are the parameters that are defined by the user to use in that specific shell script. And the **Special parameters** are the read-only variables that are predefined and maintained by the shell. Now let’s see what are the Special parameters in the bash shell.

| S.No | Special Parameters | Description                                                  |
| :--- | :----------------- | :----------------------------------------------------------- |
| 1    | **$#**             | This parameter represents the number of arguments passed to the shell script. |
| 2    | **$0**             | This parameter represents the script name.                   |
| 3    | **$i**             | This parameter represents the ith argument passed to the shell script like $1,$2 |
| 4    | **$\***            | This parameter gives all arguments passed to the shell script separated by the space. |
| 5    | **$!**             | This parameter gives PID of the last background running process. |
| 6    | **$?**             | This parameter represents the exit status of the last command that executed. The 0 code represents success and 1 represents failure. |
| 7    | **$_**             | This parameter gives the last argument provided to the previous command that executed. |
| 8    | **$$**             | This parameter gives the PID of the current shell.           |
| 9    | **$@**             | This parameter holds all argument passed to the script and treat them as an array. It is similar to the **$\*** parameter |
| 10   | **$-**             | This parameter represents the current flags set in your shell .**himBH** are the flags in bash shell.**Where:**H – histexpandm – monitorh – hashallB – braceexpandi – interactive |

**Now let’s see the script which demonstrates all Special Parameters.**

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

**Special variables in bash:**

```
$@- All arguments.
$#- Number of arguments.
$0- Filename.
$1, $2, $3, $4 ... - Specific arguments.
```

**Approach**

- If the number of arguments is 0, end the program.
- If not zero, then
  - Initialize a variable **maxEle** with first argument.
  - Loop over all the arguments. Compare each argument with **maxEle** and update it if the argument is greater.

```bash
#Check if the number of arguments passed is zero
if [ "$#" = 0 ]
then
    #Script exits if no
    #arguments passed
    echo "No arguments passed."
    exit 1
fi
  
#Initialize maxEle with 
#the first argument
maxEle=$1
  
#Loop that compares maxEle with the 
#passed arguments and updates it
for arg in "$@"
do
    if [ "$arg" -gt "$maxEle" ]
    then
        maxEle=$arg
    fi
done
echo "Largest value among the arguments passed is: $maxEle"
```