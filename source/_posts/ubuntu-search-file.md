---
title: 文件检索
categories: 
- 工具
- cmd
tags: 
- find
- locate
- which
toc: true
---

文件检索

<!-- more --> 

# 以文件名查找：

### find 命令

```
find pathname -options [-print -exec -ok] 
find / -name "filename"

pathname:查找路径
-option:主要选项如下：
-name:按照文件名称查找
-perm：按照文件权限查找
-prune：不在当前指定的路径查找。如果同时指定了-depth选项,则prune被忽略
-user:按照文件属主查找
-group:按照文件属组查找
-mtime -n +n：按照文件更改时间查找。-n 指距离现在时间n天以内；+n n天以外
-nogroup:查找无效属组文件
-nouser:查找无效属主文件
-newer file1 !file2：查找更改时间比file1新比file2旧的文件
-type:查找某一类型文件
    b:块设备文件
    d:目录
    c:字符设备文件
    P：管道文件
    l:符号链接文件
    f:普通文件
-size n[c]查找文件长度为n块的文件 有[c]表示文件长度以字节计
-depth:查找时，首先查找当前目录文件，然后再在其子目录查找
-fstype：查找位于某一类型文件系统中的文件，文件系统类型可在/etc/fstab中找到
-mount:查找文件不跨越文件系统mount点
-follow:如遇到链接文件，则跟踪至链接所指向文件
-cpio:对匹配的文件使用cpio命令，将文件备份到磁带设备中 
-print:将匹配的文件输出到标准输出
-exec:对匹配的文件执行所给的shell命令。形式为:command { } \;注意{ }和\;之间的空格
-ok：和-exec作用相同。只不过以一种更安全的模式执行该参数所给的shell命令。在执行每个命令之前，都会给出提示，让用户确定是否执行
```
目的：在根目录“/”开始搜被称为filename的文件，“filename”文件名可以包含通配符（*，？），注意：filename是文件名字符串，可以带双引号，也可不带find命令功能强大，它有很多选项让你以不同的方式搜索文件，例如，通过日期，文件大小，权限，拥有者等等。

### locate 命令

```
locate filename
```
发现包含字符串“filename”的文件名。这比find命令更容易。但是基于数据库（通常在夜间重建），所以你无法找到刚刚存到文件系统的文件。为了强制立即更新数据库，作为超级用户可以使用：updatedb& （中间没有空格）

### which命令

```
which executeable_name
```
查找可执行文件，根据可执行文件的文件名。
例如 which apache2 ， 返回/usr/sbin/apache2

# 以文件内容查找

- grep -n 字符串名字 /filepath/filename
    返回包含该字符串的该行，可以是多行。且包含行数。
    
    ```
    grep <字符串>|"<正则表达式>" [文件名]
    ```
    
- sudo gedit /filepath/filename
    用ctrl+F 去查找相应的字符串。
    
- vi或者less命令可以查找相应的内容
    例如 vi /filepath/filename而后，输入 “/字符串” ，按下字母“n”到下一个匹配的字符串
    
-  tail命令
    查看文件内容的特殊方法
    
    - 如果你只想看文件的前5行，可以使用head命令，如：
      
    ```
    head -5 /etc/passwd
    ```

    - 如果你想查看文件的后10行，可以使用tail命令，如：

    ```
    tail -20 /etc/passwd
    tail -f /var/log/messages 参数-f使tail不停地去读最新的内容，这样有实时监视的效果
    ```

-  where is <程序名称>
    查找软件的安装路径
    -b 只查找二进制文件
    -m 只查找帮助文件
    -s 只查找源代码
    -u 排除指定类型文件
    -f 只显示文件名
    -B <目录> 在指定目录下查找二进制文件
    -M <目录> 在指定目录下查找帮助文件
    -S <目录> 在指定目录下查找源代码
