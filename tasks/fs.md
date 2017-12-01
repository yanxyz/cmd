# 文件和目录的基本操作

文中 Shell 指的是 Unix Shell, 如 bash。

### cd

`cd`
显示当前目录。

`cd .\a\b\c`
改变当前目录。

`cd /d d:\a\b\c`
改变当前驱动器与当前目录。注意加上开关 "/d" 才能改变当前驱动器。

### dir

`dir`
列出当前目录的文件列表。

`dir %USERPROFILE%`
列出指定目录的文件列表。

`tree`
以树形列出当前目录的结构。不能指定目录深度。
[Shell tree](../linux/shell/commands.md)。

### mkdir

`mkdir a`
创建目录，如果目录存在则打印一条错误消息。

`mkdir a\b\c`
创建多级目录。Shell: `mkdir -p a\b\c`。

`mkdir a b`
创建多个目录。

### copy

复制命令有多个。

#### copy

copy 只能复制文件，不能复制目录。

`copy file1 file2`
复制文件，然后打印复制结果。`/y` 取消覆盖确认。

`copy file1+file2 .\test`
将多个文件合并到第一个文件，然后复制它。注意换行符。

`copy *.txt dest`

- 如果 dest 是目录则复制到它下面
- 如果 dest 是文件则合并要复制的文件并覆盖它
- 如果 dest 不存在则合并要复制的文件为 dest 文件！

`copy dir1 dir2`
相当于 `copy dir1\* dir2`。

#### xcopy

`xcopy file1 file2`
复制的时候会问目标是文件还是目录。可以这样：`echo f | xcopy file1 file2`

`xcopy /e /i /y source destination`
复制目录和它的子目录。

- `/s` 复制子目录，但不复制空目录。
- `/e` 复制子目录，包括空的子目录。
- `/i` 目标不存在时，假定它是目录。

#### robocopy

Vista 及之后的系统还可以用 robocopy。

`robocopy a c /s > nul`
复制的过程中有比较多的信息。

### move

`move file1 file2`
移动文件，即重命名。`/y` 取消覆盖确认。

`move dir1 dir2`
移动目录，若目标目录不存在则移动到它的位置，若存在则移动到它下面。

### rmdir

`rmdir dir`
删除空目录，如果目录不是空的则删除失败。
如果目录不存在或者不是目录则报错。

`rmdir /s /q dir`
删除目录及它下面所有子目录和文件，`/q` 取消删除确认。

`rmdir dir1 dir2`
删除多个空目录。

### del

只删除文件，不删除目录。
如果通配符匹配的文件，删除之前要确认。

`del file`
删除文件。没这么简单！
如果 file 是文件，则删除这个文件。
如果 file 是目录：

```bat
> del file
F:\test\test-bat\file\*, 是否确认(Y/N)?

rem 相当于
> del file\*
```

意思变成删除 file 目录下的文件。

`del /q a`
删除 a 目录（包含它的子目录） 下面所有的文件。/Q 取消删除确认。

`del file1 file2`
删除多个文件。

`del /a:r file`
删除只读文件。del 默认不能删除只读文件。

### type

`type long-text-file | more`

### attrib

查看与修改文件属性。
