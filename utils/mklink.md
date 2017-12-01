# mklink

CMD 提供一个内置命令 mklink 来创建链接。

## 链接类型

- 硬链接（hard link），链接目标为同一个 NTFS 分区上的文件。
- junction link，链接目标为到本地电脑上的目录。
- 符号链接（symbolic link），链接目标为文件或目录。Vista 开始支持，需要管理员权限。

[Understanding NTFS Hard Links, Junctions and Symbolic Links](http://www.2brightsparks.com/resources/articles/NTFS-Hard-Links-Junctions-and-Symbolic-Links.pdf)

## 用法

```bat
> mklink /?
MKLINK [[/D] | [/H] | [/J]] Link Target
```

- `/d` 创建目录符号链接。
- `/h` 创建硬链接。
- `/j` 创建 junction 链接。

mklink 在创建 symbolic link 时：

- 需要管理员权限。Win10 开发者模式不需要。
- 如果是目录链接（Target 是目录）则需要开关 "/D"
- 如果 Target 是相对路径，是相对于 Link 而不是当前工作目录！

删除链接

- `del link` 删除文件链接（HardLink 或 file SymbolicLink）
- `rmdir link` 删除目录链接（Junction 或 folder SymbolicLink）

注意：`del link`, 如果 link 是目录链接，不会删除 link, 而会删除 link target 下的文件，这通常不是我们想要的。应该用 rmdir 删除目录链接。

如何判断链接的类型以及链接的目标？建议用 [PowerShell](/powershell/tasks/symlink.md)，CMD 不好做。


## 资料

[files - How do I create a symbolic link in Windows? - Server Fault](https://serverfault.com/questions/7109/how-do-i-create-a-symbolic-link-in-windows)
