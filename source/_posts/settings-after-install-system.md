---
title: 系统重装后优化设置和常用应用
toc: true
date: 2020-03-28 20:41:18
categories: 
- 系统
- Win10
tags: 
- Win10
thumbnail:
---
系统重装后，优化设置和常用应用安装。
<!-- more --> 

1. 系统激活。

   TPYNC-4J6KF-4B4GP-2HD89-7XMP6

2. 应用安装位置。

   1、打开注册表编辑器，win + R， 输入regedit。

   2、找到注册表项HKEY_LOCAL_MACHINE/SOFTWARE/Microsoft/Windows/CurrentVersion

   3、在右侧你可以找到数值名称为ProgramFilesDir的项目，里面的默认数值数据为“C:Program Files”，将这个值修改为你所需要设定的路径，比如“D:/SoftWare”，然后确定，退出注册表编辑器。

   更改应用安装位置后，只有新应用会被安装到新位置，已安装应用不会被自动转移。

3. 桌面位置移动

   1、我们打开“**此电脑**”，在左侧栏中，**右键“桌面”选项，点击“属性”**。

   2、在弹出的桌面属性中，选择“**位置**”选项卡，我们可以发现其默认位置是在**C:\Users\用户名\Desktop**目录。

   3、如果我们需要修改到非系统盘，只需要点击“**移动**”按钮，**在弹出的对话框内选择一个你想设置的磁盘文件夹位置**，如"D:/Desktop"，点击“是”即可。

4. 常用应用

   - clover
   - everything
   - notepad++
   - snipaste
   - typora
   - beyond compare
   - chrome
   - git
   - sogo
   - ...

5. 工作环境

   - JDK
   - Android
   - SDK
   - git

移动桌面位置后，AS弹窗桌面图标不可用了，还是不要移动了，经常做文件整理吧。
