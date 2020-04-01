---
title: Hexo+GitHub搭建博客网站
date: 2020-03-28 03:13:02
tags: Hexo
categories: [工具,Hexo]
thumbnail:
toc: true
---

利用Hexo+GitHub搭建博客网站

小窝~

​	积累~

​		分享~

​			个人站~

<!-- more --> 


# 系统环境配置：

> Hexo+Nodejs+Git
1. 安装 node.js

  node -v 版本信息

2. 安装 git
    git --version 版本信息

3. 注册 github账号

#  git 连接github配置：
1. 配置SSH key:
```
	ssh-keygen -t rsa -C "邮件地址"
```
2. 测试是否成功:
```
  ssh -T git@github.com  # 注意邮箱地址不用改
```
3. github配置:
```
  git config --global user.name "hadoopBeginner" #你的github用户名，非昵称
  git config --global user.email "xxx@qq.com" #填写你的github注册邮箱
```


# 搭建个人博客

安装 hexo：
1. 安装淘宝源的cnpm
选装cnpm。由于npm速度有时候令人堪忧，所以建议安装淘宝源的cnpm，在git bash中输入
```
	alias cnpm="npm --registry=https://registry.npm.taobao.org \
	--cache=$HOME/.npm/.cache/cnpm \
	--disturl=https://npm.taobao.org/dist \
	--userconfig=$HOME/.cnpmrc"
```
安装完之后验证，输入：cnpm info express,若出现一大堆信息则表明成功了。

2. 安装 hexo 命令
```
	cnpm install -g hexo
```
在这里会有 一段时间等待，请稍等

3. 安装个人博客
进入到 你本地的博客存放路径，例如 F:\hexo\blog

```
	// 进入本地博客存放目录
	cd f:
	cd hexo/blog/
	// 初始化 个人博客
	hexo init #等待一段时间
```
初始化完成以后，会自动生成目录.
```
hexo g    // 生成静态网页
hexo s    // 执行完以后，打开 http://localhost:4000/  ,查看预览效果.
```

修改主题：
https://github.com/yelog/hexo-theme-3-hexo

下载主题：
```
	hexo clean
	git clone https://github.com/yelog/hexo-theme-3-hexo.git themes/3-hexo  
```
修改hexo根目录的`_config.yml`，如下

```
	theme: 3-hexo
```



# 部署到GitHub上：
修改站点目录的` _config.yml `文件，在最后添加
```
	deploy:
	  type: git
	  repo: https://github.com/xxx/xxx.github.io.git  #填github地址
	  branch: master
```

然后在命令行中执行
```
	// 提交到github
	hexo d
	// 注意需要提前安装一个扩展：
	cnpm install hexo-deployer-git --save
```

到此，基本就搭建完毕。





# 开始写作

新建文章，输入以下命令即可

```
	hexo new '文章标题'

```

执行完成后可以在 `/source/_posts `下看到一个“文章标题.md”的文章。是 Markdown 格式的文件.



再执行一下以下命令

```
	hexo g
	hexo s
```

可以在 http://localhost:4000 预览文章.



最后，只要部署到你的 Github 上就可以了！

```
	hexo clean
	hexo g -d
```

部署前最好能先执行一下 hexo clean 命令，清除缓存文件 (db.json) 和已生成的静态文件 (public)。在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

另外，如果你的文章暂时不发布可以先保存在草稿里面。生成草稿的方法和文章差不多 hexo new draft "文章标题"，生成后会在 /source/_drafts 里看到你的草稿文章。当你想发布时只要执行 publish 命令即可发布到博客。

```
	hexo publish [layout] <filename>
```