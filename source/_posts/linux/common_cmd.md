---
date:
---

#chmod

设置文件、文件夹权限

###首先了解一下linux下的文件权限
``` shell
drwxr-xr-x 2 root root 4096 10月 24 15:44 .
drwxr-xr-x 3 root root 4096 10月 24 15:38 ..
-rw-r--r-- 1 root root  109 10月 24 15:40 print.java
-rw-r--r-- 1 root root   21 10月 24 15:44 print.sh
```

![](common_cmd_chmod.gif)

这一块可以分成4个四个部分

1. 档案类型，`-`、`d`分表表示文件和目录
2. 所有者权限
3. 组权限
4. 其他人权限

其中的`rwx`分别表示读写执行，像用`vi`创建的`sh`脚本默认权限为`rw-`如果要执行就需要重新赋值权限

###命令格式
```shell
chmod 777 print.sh
#chmod 权限码 文件
```
权限码是怎么算出来的呢？

首先我们把`rwx`转换成数字，他的对应关系如下
```
r->4
w->2
x->1
```
加起来就是一个权限值，如`rwx`就等于7

有了单个权限值后，777又是怎么来的呢？

其实就是把所有者权限、组权限、其他人权限 这三个权限拼接起来，`rwxrwxrwx`变成了`777`

上面的例子可能比较抽象我们举几个栗子
```shell
drwxr-xr-x #目录权限，755，所有者可读可写可执行，其他人只能读取和执行
-rw-r--r-- #文件权限，644，所有者可读可写，其他人只能读
```

####参考文章
----
[Linux 的文件权限与目录配置](http://cn.linux.vbird.org/linux_basic/0210filepermission.php)
 
