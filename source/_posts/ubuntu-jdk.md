---
title: Ubuntu JDK
categories: 
- Android
tags: 
- jdk
toc: true
---


Ubuntu JDK安装

<!-- more --> 
# Oracle JDK

- 下载jdk [Oracle JDK](https://www.oracle.com/java/technologies/javase-jdk8-downloads.html) 

- 解压到指定目录`/usr/lib/jvm`

```
// 创建目录
sudo mkdir /usr/lib/jvm
// 解压
sudo tar -zxvf jdk-8u144-linux-x64.tar.gz -C /usr/lib/jvm/
```

- 使用update-alternatives进行配置

```
// 400 优先级
 sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_251/bin/java 400
 sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_251/bin/javac 400
 sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/jdk1.8.0_251/bin/jar 400
 sudo update-alternatives --install /usr/bin/javah javah /usr/lib/jvm/jdk1.8.0_251/bin/javah 400
 sudo update-alternatives --install /usr/bin/javap javap /usr/lib/jvm/jdk1.8.0_251/bin/javap 400
```

- 验证

```
java -version
javac -version
javap -version
javah -version
```

# OpenJDK-8

```
sudo apt-get update
sudo apt-get install openjdk-8-jdk
```


# 使用update-alternatives多版本切换
```
// 切换
sudo update-alternatives --config java
```

# 环境变量配置

```
sudo gedit ~/.bashrc

export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_251
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

source ~/.bashrc
```



# 卸载JDK

```
sudo apt-get remove openjdk*
```

