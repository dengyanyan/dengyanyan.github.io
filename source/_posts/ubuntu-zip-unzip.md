---
title: Ubuntu 常用解压与压缩命令
categories:
- Liunx
- cmd
tags: 
- zip
- unzip
toc: true
---

.tar

.gz

.tar.gz

.zip

.rar

<!-- more --> 

# .tar

```
# 仅打包，并非压缩
tar -xvf FileName.tar         # 解包
tar -cvf FileName.tar DirName # 将DirName和其下所有文件（夹）打包
```

# .gz

```
# .gz
gunzip FileName.gz  # 解压1
gzip -d FileName.gz # 解压2
gzip FileName       # 压缩，只能压缩文件
```

# .tar.gz  / .tgz

```
# .tar.gz 和 .tgz
tar -zxvf FileName.tar.gz               # 解压
tar -zcvf FileName.tar.gz DirName       # 将DirName和其下所有文件（夹）压缩
tar -C DesDirName -zxvf FileName.tar.gz # 解压到目标路径
```

# .zip

```
# 感觉.zip占用空间比.tar.gz大
unzip FileName.zip          # 解压
zip FileName.zip DirName    # 将DirName本身压缩
zip -r FileName.zip DirName # 压缩，递归处理，将指定目录下的所有文件和子目录一并压缩
```

# .rar

```
# mac和linux并没有自带rar，需要去下载
rar x FileName.rar      # 解压
rar a FileName.rar DirName # 压缩
```



.tar是打包，.tar.gz才是压缩过的文件,  .tar.gz常见于unix系统，在ubuntu或macos可以直接解压，而.zip常见于windows系统,但在windows系统中用WinRar工具同样可以解压缩tar.gz格式的


zip流行于windows系统上的压缩文件（其他系统也可以打开）。zip格式开放而且免费。zip支持分卷压缩，128/256-bit AES加密算法等功能。zip的含义是速度，其目标就是为顶替ARC而诞生的“职业”压缩软件。

tar是“tape archive”(磁带存档)的简称，它出现在还没有软盘驱动器、硬盘和光盘驱动器的计算机早期阶段，随着时间的推移， tar命令逐渐变为一个将很多文件进行存档的工具，目前许多用于Linux操作系统的程序就是打包为tar档案文件的形式。 在Linux里面，tar一般和其他没有文件管理的压缩算法文件结合使用，用tar打包整个文件目录结构成一个文件，再用gz，bzip等压缩算法压缩成一次。也是Linux常见的压缩归档的处理方法。