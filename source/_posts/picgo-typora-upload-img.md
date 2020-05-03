---
title: PicGo搭建图床
categories: 
- 工具
- Hexo
tags: 
- PicGo
- Hexo
- Gitee
- Typora
- AppImage
toc: true
---

PicGo搭建图床，完善个人博客

<!-- more --> 
# PicGo搭建图床

- hexo-github(action)

  - 搭建博客

  - 稳定

  - 自动构建,部署

- gitee-picgo

  - 搭建图床

  - 国内快

[PicGo官网](https://github.com/Molunerfinn/PicGo/releases)

PicGo是一款非常优秀的图床上传工具。它支持强大的粘贴板上传和各种上传方式。

# PicGo安装

下载太慢了，百度网盘地址。

Linux：链接: https://pan.baidu.com/s/1F62_0AwxcfNxrLQaADUiRQ 提取码: h3ae

Windows：链接: https://pan.baidu.com/s/1oJIOKK2NIFNLjcFSJT8ZSA 提取码: 3tdq

```

Linux--AppImage

AppImage是一种在Linux系统中用于分发便携式软件而不需要超级用户权限来安装它们的格式。它还试图允许Linux的上游开发者来分发他们的程序而不用考虑不同Linux发行版间的区别。
在2004年，它以klik的名字发布。自那时起，它就被不断地开发，并在2011年被重命名为PortableLinuxApps，在2013年被重命名为AppImage。
--WikiPedia
```

- 为了方便运行，我先把下载下来的程序放到`系统变量`下。

```
echo $PATH
```

- 简单粗暴，丢进去

```
sudo cp ~/Downloads/picgo-2.1.2-x86_64.AppImage /usr/local/bin/PicGo
sudo +x /usr/local/bin/PicGo
PicGo
```

- 安装依赖，虽然PicGo已经开始运行了，可是有些功能需要依赖其他程序来实现。在程序内实现粘贴板上传需要用到`xclip`，不装的话会报这样的错误.

```
sudo apt-get install xclip -y
```

# 准备工作

1. 依赖安装`node.js` / `npm`。最好先安装，不然有蜜汁报错。[nodejs官网](https://nodejs.org/en/)

   ```
   # 解压到 /opt/下
   
   # 安装npm，使用淘宝源
   npm config set registry https://registry.npm.taobao.org
   
   # 验证安装
   node -v
   npm -v
   
   # 配置nodejs环境变量
   export NODE_HOME=/opt/node-v14.1.0-linux-x64
   export PATH=$NODE_HOME/bin:$PATH
   ```

2. gitee账号

3. 创建仓库，公开，初始化（带master分支）

4. token，个人主页-个人设置-私人令牌（可以使用giteeAPI）

5. 配置gitee图床
   - repo：用户名/仓库名
   - branch : master
   - token：填入码云的私人令牌 
   - path：路径，一般写上img 

![](https://gitee.com/dyyan1993/img-ol/raw/master/img/20200503210842.png)



# Typora 设置

File - Preferences - image

![](https://gitee.com/dyyan1993/img-ol/raw/master/img/20200503213314.png)



# Markdown使用

可以直接粘出来给markdown使用的图片地址。

![](https://gitee.com/dyyan1993/img-ol/raw/master/img/20200503214953.png)