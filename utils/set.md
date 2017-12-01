# set

`set` 没有参数则显示当前 session 全部变量。
有参数时设置变量

```bat
rem 注意 `=` 左右没有空格
set name=Yan
rem 显示变量和它的值
set name
rem 显示变量的值
echo %name%
```

如果变量值有空格

```bat
set "name=Ivan Yan"
set name
echo %name%
```

删除变量

```bat
set name=
set name
echo %name%
```

上面设置的变量存在于当前 session，关闭 console 之后就不存在了。
