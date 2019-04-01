---
layout:     post
title:      你经常碰到的Gas estimation errored
subtitle:   你经常碰到的Gas estimation errored真的是gas error吗？
date:       2019-04-01
author:     admin
header-img: img/pabg-loi-may-photocopy-hai-phong.jpg
catalog: true
tags:
    - gas estimation error
---

# 你经常碰到的Gas estimation errored真的是gas error吗？

------

其实任何错误都会造成remix报这个错，例如：你的合约代码逻辑上的错误，甚至某个方法不是payable的但是你调用的时候发送了以太币也会报这个错。

![](https://www.blktime.com/img/pa-FZ2kr.png)

所以大部分时候这个提示没太大意义，那么遇到这个错误如何定位问题呢:
首先:看看是否对non-payable的函数发送了以太
其次:逐行检查出错的方法的代码逻辑，这样是一定可以找出问题来的。