# Hello World
```sh
echo Hello, world!
```

# Pipelines
* 管道操作符`|&`可以重定向错误输出，功能和`2>&1`一样
* 命令以`&`结尾可异步执行

# Looping Constructs
* for in words
```sh
for i in Sun Mon Tue Wed Thu Fri Sat; do
    echo $i
done
```
* for in array
```sh
ARRAY=(Sun Mon Tue Wed Thu Fri Sat)
for i in ${ARRAY[@]}; do
    echo $i
done
```
* for in count
```sh
for ((i = 1; i <= 5; ++i))
do
    echo $i
done
```

# Conditional Constructs
```sh
if [[ -d /tmp ]]; then
    echo Exist /tmp directory
else
    echo Does not exist /tmp directory
fi
```

# Shell Functions
```sh
func1() {
    echo func1
}

func2() {
    func1
    echo func2
    echo $1
    echo $2
}

func2 para1 para2
```

# Special Parameters
* `$*`参数列表，`"$*" -> "$1c$2c…"`
* `$@`参数列表，`"$@" -> "$1" "$2" …`
* `$#`参数个数
* `$?`最近的退出码
* `$$`Shell的进程ID
* `$!`最近的后台进程ID
* `$0`Shell名或者脚本名
* `$_`初始化为脚本绝对路径，执行命令后为最近一个命令的最后一个参数

# Brace Expansion
```sh
echo a{d,c,b}e
```

# Shell Parameter Expansion
* String
```sh
STRING=01234567890abcdefgh
echo ${STRING:7:2}
```
* Array
```sh
ARRAY=(0 1 2 3 4 5 6 7 8 9 0 a b c d e f g h)
echo ${ARRAY[@]:7:2}
```

# Bash Builtin Commands
* 读取输入
```sh
read -a INPUT
echo ${INPUT[0]}
```

# The Set Builtin
* 显示执行的命令
```sh
set -x
```

# Invoking Bash
* 命令作为参数传入执行
```sh
bash -c 'echo Hello World!'
```

# Readline Bare Essentials
* `C-b`向后移动一个字符
* `C-f`向前移动一个字符
* `C-u`删除光标所在字符

# Readline Movement Commands
* `C-a`移动到行首
* `C-e`移动到行尾

# Readline Killing Commands
* `C-k`剪切光标至行尾的字符
* `C-w`剪切光标与前面空白字符之间的字符
* `C-y`粘贴最近剪切的
