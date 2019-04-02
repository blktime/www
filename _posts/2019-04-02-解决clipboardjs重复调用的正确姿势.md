---
layout:     post
title:      解决clipboardjs重复调用的正确姿势
subtitle:   clipboardjs是一个非常好用的跨端（pc端，手机端）复制粘贴js库
date:       2019-04-02
author:     admin
header-img: img/post-bg-desk.jpg
catalog: true
tags:
    - clipboardjs
---

# 解决clipboardjs重复调用的正确姿势

------

clipboardjs是一个很好的游览器复制插件，使用该js库可以在各种游览器复制你想要复制的内容，包括各种手机的游览器，但是有个问题：
<pre>const clipboard = new Clipboard(".copy-address");
    clipboard.on("success", function(e) {
      // console.log("1");
      toast("地址已复制");
    });
    clipboard.on("error", function(e) {});
</pre>
在第一次点击后，后续每次点击都会带出前面的结果，其实就是clipboard.on("success")被重复调用了，通过console.log打印就可以看出来。那么如何解决呢？我看了下segmentfault上面有人回答：在上面代码之前加上
<pre>if(clipboard)
  clipboard.destroy();
</pre>
避免出现多次事件绑定。我试了下并不管用，on("success")还是会被调用多次。然后我在vue组件中声明了一个全局的clipboard，然后在vue组件生命周期的destroyed中调用
<pre>clipboard.destroy();</pre>
便很好地解决了该问题。当你退出当前vue组件再重新进来，点击复制按钮时不会出现之前地结果了。