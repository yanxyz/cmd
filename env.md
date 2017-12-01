# Windows 环境变量

Windows 环境变量（Environment Variables）

## 引用

在 cmd.exe 中

- `set` 会显示所有的环境变量，包括应用动态添加的变量。
- `%Path%` 引用环境变量 `Path`，变量名字不区分大小写

在 git-bash 中

- `env` 会显示所有的环境变量，包括应用动态添加的变量。
- `$PATH` 引用环境变量 `Path`，变量名字区分大小写

## Path

在 CMD 中使用外部命令时，`Path` 指定在哪里查找命令，`PATHEXT` 指定查找哪些扩展名，找到了即停止查找。

`Path` 的值为 System Path 和 User Path 的合集。注意 System Path 在前 User Path 在后，即先搜索 System Path 再搜索 User Path。

与 Linux shell 不一样，cmd

```bat
> script.bat
```

会在 Path 中搜索 script.bat，而不是先从当前目录中搜索，，因此通常指定路径

```bat
> .\script.bat
```

## 编辑

Win10, 在 Cortana 中输入 env，

- “编辑账户的环境变量”，不需要管理员权限
- “编辑系统的环境变量”

推荐用 [RapidEE](http://www.rapidee.com/en/download) 编辑环境变量。

## 参考

- <https://ss64.com/nt/syntax-variables.html>
