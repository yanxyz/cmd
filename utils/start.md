# start

start 启动程序。

```cmd
> start /?
REM start "title" [switches] program [parameters]

> start "" /d "%P" /wait notepad hello.txt
```

## program

program 包括空格，要用引号包裹

```cmd
start "" "c:\Program Files\nodejs\node.exe"
```

program 是 cmd 内部命令或 bat 文件，则以 `cmd /k` 运行

```cmd
start dir
```

program 是 url, 则以默认浏览器打开。

```cmd
start https://yanxyz.github.io/note/
```

注意 `http://` 不可少，不然就当作本地文件了。

program 不是 executable，比如 document, script 等，则以关联程序打开

```cmd
start hello.txt
```

## switches

`/b` 不创建新窗口。 对 GUI 程序无效。

```cmd
start cmd
start /b cmd
start /b notepad
```

`/d` 指定程序的工作目录

```cmd
start /d C:\Users cmd
```

`/wait` 等待程序关闭。如果是 GUI 程序，需要 GUI 程序支持。有的

```cmd
> start /wait cmd
REM 等待

> start /wait notepad
REM 等待

> start /wait explorer
REM 返回
```
