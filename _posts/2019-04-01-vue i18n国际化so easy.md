---
layout:     post
title:      vue i18n国际化so easy
subtitle:   
date:       2019-04-01
author:     admin
header-img: img/pa-bg-working-with-internationalization.png
catalog: true
tags:
    - vue i18n
---

# vue i18n国际化so easy

------

直接进入正题——quasar国际化：
## 第一步：
没添加的需要手动添加下，不过这里建议大家用quasar cli创建工程的时候，选上i18n和axios，就是用quasar create 你的项目的时候，有个步骤会让你选择是否添加i18n axios组件，这个两个东西对大部分项目来说，我觉得都是需要的。没添加的后面也可以对照quasar官网add plug里面的步骤添加下。

## 第二步：
在i18n文件夹下面添加对应的语言文件，比如：zh-cn，如下图所示：
![](https://www.blktime.com/img/pa-Snipaste_2019-03-11_21-36-23.png)

## 第三步：
在vue组件里面使用html标签里面通过$t('test')  ,js代码里面通过this.$t('test')  ,test为你显示的字符的名称，注意这里不是$t('message.test') ,网上好多都是这样说的，我实践了下不好使，至少quasar不需要代message.是不是so easy。接下来重点来了，就是如何切换语言，这个也很简单，只需在你需要切换的地方设置下this.$i18n.locale的值就可以了，比如：this.$i18n.locale='zh-cn'最后还有一个经常遇到的问题就是，设置完后下次再进来又变成之前的语言了，讲话应该记住用户上一次的设置，这个怎么做呢，其实用localforage保存一下上一次设置的记录就好了，然后在初始化的地方获取上次存储的值，如下图：
![](https://www.blktime.com/img/pa-Snipaste_2019-03-11_21-43-21.png)

就ok，关于i18n就给大家分享到这里，对了，localforage是一个localstorage,indexdb等的一个封装，非常好用，本站也有介绍，大家可以搜搜之前的贴。