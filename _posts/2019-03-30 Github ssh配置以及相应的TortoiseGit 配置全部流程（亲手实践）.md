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

选择SSH

![](https://www.blktime.com/img/pa193305.png)

然后New SSH key

![](https://www.blktime.com/img/pa193306.png)

title随便填
key即为你在第一步生成的id_rsa.pub文件的内容，用notepad打开复制即可 。这个文件一般在你的电脑C:\Users\Administrator\.ssh目录下面

![](https://www.blktime.com/img/pa193307.png)

然后点击Add按钮，即可。

### 2.测试github链接

还是在git bash里面输入命令 
ssh -T git@github.com

如果看到Hi后面是你的用户名，就说明成功了。
Hi youname! You've successfully authenticated, but GitHub does not provide shell access.

到此位置github的ssh key就配置完成了

## 三. 接下来讲讲如何配置TortoiseGit
### 1.首先生成ppk:

因为TortoiseGit不能直接用ssh key，需要先将上面生成的ssh key转换成ppk

找到TortoiseGit的安装目录下面的bin文件
以我的为例在C:\Program Files\TortoiseGit\bin下面的
puttygen.exe文件点击打开，点击load key 选择你在第一步生成的id_rsa，然后点击save private key，自己命个名称保存起来，记得保存的位置，一会TortoiseGit中添加要用到这个文件。

### 2.配置TortoiseGit
新建文件夹，先初始化下版本库

![](https://www.blktime.com/img/pa193308.png)

然后点击设置

![](https://www.blktime.com/img/pa193309.png)

![](https://www.blktime.com/img/pa1933010.png)

点击git 选择此版本库，红框后面的勾统统去掉。填上你的名称和email.这个你提交代码成功后会显示在github上。

这里有个比较重要的点就是，git的配置是分层级的，为了对当前版本库的配置不影响其他版本库，所以我们选择此版本库进行配置，而非全局。

![](https://www.blktime.com/img/pa1933011.png)

然后在两个url处填你github版本库的ssh地址，在这里复制

![](https://www.blktime.com/img/pa1933012.png)

如果你看到的是https 点击use ssh切换

重要的来了，在Putty密钥处选择，你上面保存的ppk文件，说到这里整个配置过程确实有点负责，一环套一环，所以大家需要点耐心看，幸运的是这整个过程作者都亲身检验过，绝对靠谱。作者在写之前也是在网上搜索了大量资料，在开始配置之前也是望而却步，想找有没有简单的方法，可惜没找到，又因为网上的资料比较零散，不全，
最后不得不一步步实践，然后总结出这个全流程来。

上面的url，putty密钥填完后就点击应用，保存即可，一般填完url就会提示你拉去远程库，按提示拉取即可。

到这里所有流程就结束了，剩下的就跟之前一样使用TortoiseGit即可。

拉取如果遇到以下报错

![](https://www.blktime.com/img/pa1933013.png)

选择合并非相关历史即可。

至于TortoiseGit的commit push等常用用法不知道的同学去网上搜搜即可，这个非常简单。

最后，补充一点的就是不同的respository不能添加同样的key，所以新建一个respository，需要重新生成一对ssh key，然后重复上面的流程即可。
