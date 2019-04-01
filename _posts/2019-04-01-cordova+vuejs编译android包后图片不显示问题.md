---
layout:     post
title:      cordova+vuejs编译android包后图片不显示问题
subtitle:   
date:       2019-04-01
author:     admin
header-img: img/pa-bg-0401.png
catalog: true
tags:
    - cordova android
---

# cordova+vuejs编译android包后图片不显示问题

------

这个问题的解决办法非常简单，就是图片路径问题，例如：放在statics下面的a.png图片，则需要写成 :src="statics/a.png"   ，前面没什么/斜杠，也不需要加点。不知道网上怎么那么多不靠谱的答案。另外，vue绑定img的src经实际检验可以直接写成 :src，我看国外的几个专业的vue论坛好多人都遇到这个问题，说要写成v-artri什么的，不知道是不是真的实践过，有时很简单个问题不知道怎那么多不靠谱的答案。