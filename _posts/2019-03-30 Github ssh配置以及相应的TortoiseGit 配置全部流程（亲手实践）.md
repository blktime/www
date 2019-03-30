---
layout:     post
title:      Github ssh配置以及相应的TortoiseGit 配置全部流程（亲手实践）
subtitle:   Github ssh配置以及相应的TortoiseGit 配置全部流程（亲手实践，OK 可行）
date:       2019-03-30
author:     admin
header-img: img/post-bg-git.jpg
catalog: true
tags:
    - github ssh配置
---

# Github ssh配置以及相应的TortoiseGit 配置全部流程（亲手实践）

------

## 一. 生成SSH key

### 1.生成密钥

打开gib bash,没有的装一个，网上大把
输入命令：
ssh-keygen -t rsa -C "youemail@email.com"

连续3个回车。如果不需要密码的话。
最后得到了两个文件：id_rsa和id_rsa.pub。

![](https://www.blktime.com/img/post-article-git1.png)

如果不是第一次，就选择overwrite.

![](https://www.blktime.com/img/post-article-gitbVlgpi)

### 2.添加密钥到ssh-agent  本人亲自实践注意这个必不可少否则后面链接github会不成功

输入命令：
eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_rsa

![](https://www.blktime.com/img/post-article-git3.png)

OK ,到目前为止，你本地的SSH配置完了

## 二.github上配置ssh key
### 1.github上添加ssh public key这个简单。

登陆你的github,在右上角你图标出，点击进入setting

![](https://www.blktime.com/img/pa193304.png)