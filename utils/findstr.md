# findstr

[findstr](https://technet.microsoft.com/en-us/library/bb490907.aspx)

```cmd
findstr /?
```

`findstr "hello there" myfile`
在 myfile 中搜索 "hello" 或 "there"。

`findstr /c:"hello there" myfile`
在 myfile 中搜索 "hello there"。注意与上例的不同。

`dir /b | findstr /i /r /c:"[mp]"`
搜索目录

- `/r` 使用正则表达式，只支持很少的语法


## 资料

- [Grep equivalent for Windows 7?](https://superuser.com/questions/300815/)
