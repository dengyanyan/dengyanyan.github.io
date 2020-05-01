---
title: git多用户配置
toc: true
date: 2020-03-28 19:10:01
categories: 
- 工具
- git
tags: 
- git
thumbnail: 
---

git多账号配置。公司，github

<!-- more --> 
# 1. 生成对应的私钥公钥

```
# github
ssh-keygen -t rsa -C xxx@163.com -f ~/.ssh/github/id_rsa
# 公司
ssh-keygen -t rsa -C xxx@xxx.cn -f ~/.ssh/xxx/id_rsa
```

# 2. github/gerrit上配置ssh-key
# 3. config文件配置，~/.ssh/config
```
# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile /home/andy/.ssh/github/id_rsa
User username
# gerrit

```
# 4. 修改权限600，
```
sudo chmod 600 ~/.ssh/config
sudo chmod 600 /home/andy/.ssh/github/id_rsa
```
# 5. ssh -T 校验
```
ssh -T git@github.com
如果成功会显示如下:
Hi xxxxxx! You've successfully authenticated, but GitHub does not provide shell access.
```


