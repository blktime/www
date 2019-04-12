---
layout:     post
title:      苹果电脑npm install cordova报无权限的解决方法，亲测有效
subtitle:   不光是安装cordova,安装任何东西报usr/local的权限问题都可以尝试此方法解决
date:       2019-04-02
author:     admin
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - ios
---

# 苹果电脑npm install cordova报无权限的解决方法，亲测有效

------

直接上方案：
> 1.重启按住cmd+R直至出现mac图标
> 2.打开终端输入 csrutil disable然后重启
![](https://www.blktime.com/img/675657090.jpg)
> 3.重启后输入 sudo chflags norestricted /usr/local && sudo chown -R $(whoami):admin /usr/local

然后输入sudo chown -R $(whoami):admin /usr/local就可以更改usr local目录的权限了，再安装cordova就没有任何错误啦。这里解释下，第1.2两步是关掉高版本Mac 的sip安全设置
然后才可以更改usr locar的权限，否则用root用户也没用，最后不光是安装cordorva,安装其他任何东西报没权限的错，都可以尝试下这个解决方法