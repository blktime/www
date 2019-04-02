---
layout:     post
title:      Solidity Stack too deep 的根本原因和解决方案
subtitle:   
date:       2019-04-02
author:     admin
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - solidity
---

# Solidity Stack too deep 的根本原因和解决方案

------

在编写以太坊智能合约的时候我们经常会遇到<span style="color: #ff0000;">Stack too deep, try removing local variables</span>的错误提示，当它在有入参或者返回参数的地方提示这个，大部分时候我们知道，就是在说，局部变量用的太多了，需要减少下。但是有的时候它也会在其他看上去不想关的地方报出这个错误，比如下面的情况：

<img class="alignnone size-full wp-image-1930" src="https://www.blktime.com/img/Snipaste_2019-01-11_14-24-13.png" alt="" width="777" height="112" />

提示说这个数组的id造成了这个错误，其实根本原因跟这个数组的id没有关系，还是由于你的方法里面使用的局部变量超限。总的来说一个函数里面使用的local variables不能超过16个，这是以太坊虚拟机的限制，其中这16个包括:入参，返回参数和其他局部变量。那么遇到该问题的解决的办法目前只有将你的函数进行拆分来避开该限制。

关于这个问题的更多介绍可以参考<a href="https://web.archive.org/web/20161015173410/http://james.carlyle.space/2015/07/22/solidity-stack-too-deep/">https://web.archive.org/web/20161015173410/http://james.carlyle.space/2015/07/22/solidity-stack-too-deep/</a>这篇文章