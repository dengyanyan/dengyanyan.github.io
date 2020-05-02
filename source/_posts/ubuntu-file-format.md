---
title: 文件格式
categories: 
- Ubuntu
tags: 
- Ubuntu
- File
toc: true
---


文件格式 
Windows <=> Ubuntu
<!-- more --> 

脚本windows复制到linux可能格式不一致,无法执行

```
// 安装vim
sudo apt-get install vim

// vim 查看文件，可以看到是dos格式
:set ff
// 修改文件格式
:set ff=unix
```
