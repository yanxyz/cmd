# bat 脚本

bat 脚本（batch file），文件扩展名为 `.bat` 或 `.cmd`，由 `cmd.exe` 解释执行。

脚本文件必须使用 Windows 断行符 (\r\n)。

脚本不区分大小写。

路径分隔符为 `\`, `/` 是开关标志。
如果路径包含空格，需要用双引号包裹。

## echo

脚本第一行通常是 `@echo off`。脚本默认 `echo on`，意思是在运行当前行时，先打印当前行，再打印当前行的输出。`echo off` 则从 `echo off` 下一行开始只打印当前行的输出。`@` 效果同 `echo off`，只对当前行有效，于是用来取消打印 `echo off` 所在行。

对于 `on|off` 之外的 argument，echo 将原样打印它。而 linux shell 会去掉引号。

```bat
echo "hello"
```

打印一个空行

```bat
echo.
```

## rem

```bat
rem 注释
:: 注释
```

`::` 是特殊的 label, 不建议使用。

## variables

- [set](utils/set.md)

### setlocal

setlocal 和 endlocal 是一对，类似于其它语言的语句块 `{}`，也可以嵌套。

```bat
@echo off

setlocal
set i=0

rem 嵌套
setlocal
set i=1
endlocal

echo %i%
```

### command line arguments

`%n`
第 n 个参数，n 从 1 到 9。

`%*`
所有的参数（最多 255 个）

[Parameter Extensions](http://ss64.com/nt/syntax-args.html)，以第一个参数 `%1` 为例

`%~dp0`
脚本所在的目录

### substring

提取子串 `%variable:~m,n%`

- `m` 是跳过的字符长度
- `n` 是保留的字符长度，可省略
- 两者都可以是负数，表示从后往前数

```bat
@echo off

set str=abcdefg

echo %str:~1,2%
rem bc

echo %str:~-1%
rem g
```

### replace

替换 `%variable:subStr=newStr%`

npm 自动生成的模块命令行脚本中有这么一行

```bat
@SET PATHEXT=%PATHEXT:;.JS;=;%
```

意思是将 `PATHEXT` 当中 `;.JS;` 替换为 `;`，避免搜索 js 文件。

## if

`if CONDITION command1 else command2`

多行命令放在 `()` 内

```bat
if exist test.txt (
    echo 删除文件
    del test.txt
) else (
    echo 未找到
)
```

当使用括号时可以写多行命令。

CONDITION 有这么几种：

`if [not] exist filename`
文件是否存在

`if [not] defined variable`
变量是否存在

`if [not] ERRORLEVEL number`
%ERRORLEVEL% 是否为 number

`if [/i] [not] item1==item2`
两者是否相等（字符串比较）

`if [/i] [not] item1 OPERATOR item2`
比较数字，OPERATOR 为

- equ(equal ==), neq(!=)
- lss(less than <), leq(<=)
- gtr(greater than >), geq(>=)

括号里只是说明，OPERATOR 为三个字符的关键字。

## for

`FOR %%parameter IN (set) DO command`


## goto

```bat
@echo off

goto :eof
echo hello

:eof
```

## call

```bat
call script.bat %var%
```

## 参考

- <https://ss64.com/>
