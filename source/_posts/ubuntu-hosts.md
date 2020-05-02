---
title: Ubuntu/Windows修改hosts
categories: 
- 系统
- Others
tags: 
- hosts
toc: true
---


Ubuntu/Windows修改hosts

<!-- more --> 

Ubuntu:
```
sudo gedit /etc/hosts

101.6.8.193 mirrors.tuna.tsinghua.edu.cn
218.104.71.170 mirrors.ustc.edu.cn

// 保存并重启网络
sudo /etc/init.d/networking restart
```

Windows:
```
/Windows/System32/drivers/etc/hosts
```

