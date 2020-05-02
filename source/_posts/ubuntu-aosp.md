---
title: Android源码编译
categories: 
- Android
tags: 
- aosp
toc: true
---

Android源码编译

<!-- more --> 

# Android 源码编译

源码下载

下载地址：[每月更新的初始化包](https://mirrors.tuna.tsinghua.edu.cn/aosp-monthly/aosp-latest.tar)

切换分支，同步代码。解压后的AOSP目录，此时为master分支。

```
.repo/manifest # 进此目录，可以使用git命令

git branch -a # 查看所有分支

repo init -u https://aosp.tuna.tsinghua.edu.cn/platform/manifest -b android-7.1.1_r9  # 清华源

repo init -u git://mirrors.ustc.edu.cn/aosp/platform/manifest -b android-7.1.1_r9  # 中科大源

    repo常见的3个参数
    -u 整个AOSP的manifest的git的地址
    -b 同步完成后要切换到的分支
    -g 同步指定的分组(group)
    因为同步的时候，repo是把所有的子项目的git仓库都同步下来了，所以才可以这样切换分支。

repo sync # 同步
```



安装git repo

```
curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
chmod +x repo
```

使用清华tuna的镜像源进行更新，可以将如下内容复制到~/.bashrc

```
gedit ~/.bashrc
```

```
export REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo/'

# repo 报错
# Clone failed
# RPC failed; curl 56 GnuTLS recv error (-54): Error in the pull function.
# The remote end hung up unexpectedly
# early EOF
# index-pack failed
# 

# RPC failed; curl 56 GnuTLS recv error (-9): A TLS packet with unexpected length was received.

export GIT_TRACE_PACKET=1
export GIT_TRACE=1
export GIT_CURL_VERBOSE=1
```

```
source ~/.bashrc
```

代码同步 sync.sh

```
#!/bin/bash
echo "====== repo sync ======"
echo "try repo sync-->" >> ~/bin/sync.log

repo sync -j8 -qc
while [ $? == 1 ]; do
    echo "====== sync failed, re-sync again ======"
    sleep 30
    echo "try repo sync again-->" >> ~/bin/sync.log
    repo sync -j8 -qc
done 
```



依赖设置

- JDK安装
- 其他依赖

```
sudo apt-get install libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-dev g++-multilib  sudo apt-get install -y git flex bison gperf build-essential libncurses5-dev:i386 
sudo apt-get install tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386  sudo apt-get install dpkg-dev libsdl1.2-dev libesd0-dev 
sudo apt-get install git-core gnupg flex bison gperf build-essential 
sudo apt-get install zip curl zlib1g-dev gcc-multilib g++-multilib 
sudo apt-get install libc6-dev-i386 
sudo apt-get install lib32ncurses5-dev x11proto-core-dev libx11-dev 
sudo apt-get install libgl1-mesa-dev libxml2-utils xsltproc unzip m4 
sudo apt-get install lib32z-dev ccache

```

依赖设置中有可能会出现“无法定位软件包 libesd0-dev” 这个问题

```
解决方案： 在etc/apt   的sources.list 添加镜像源 

deb http://archive.ubuntu.com/ubuntu/ trusty main universe restricted multiverse 

然后 sudo apt-get update  接着继续使用该命令安装就可以了
```

编译,build.sh

```
source build/envsetup.sh
lunch aosp_x86_64.eng
make -j8
```

模拟器运行,emulator.sh

```
emulator -partition-size 1024
```

清除编译文件, out/* , clean.sh

```
make clean
```



踩坑记!!!

