---
title: git配置
categories: 
- 工具
- git
tags: 
- git
toc: true
---

git配置,别名
<!-- more --> 

```
[user]
	name = username
	email = useremail@xxx.com
[color]
	ui = auto
[http]
	postBuffer = 200000000000
	sslVerify = false
	maxRequestBuffer = 100M
[core]
	compression = 0
	compression = -1
[alias]
	lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --decorate
    	st = status
    	add = add
    	br = branch
   	cm = commit
    	co = checkout
    	cob = checkout -b
```
