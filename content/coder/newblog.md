---
title: "文件软连接和硬链接 link"
date: 2020-06-25T17:28:15+08:00
slug: "link"
keywords: ["link", "mklink", "拒绝访问"]
draft: false
tags: ["link"]
math: false
toc: false
---

今天遇到一个问题，就是为了不影响线上玩家，把我们的gm目录分成了两个svn，线上web目录和gmweb目录。
但是存在一个问题，就是线上和后台可能遇到修改和获取一个文件。

比如运营修改了gmweb目录的文件
玩家需要获取这个文件但是只能获取到线上web目录的文件

那么这个时候就可以用到硬链接了。

用到就学到

[什么是link文件？](https://www.cnblogs.com/shamao/p/11169229.html)

[如何操作？](https://www.cnblogs.com/Akkuman/p/9688311.html)

你可能遇到的问题

[问题1 mklink 拒绝访问](https://zhidao.baidu.com/question/987213623704074699.html)

问题2 查问题的时候看到js右键特效就想自己用，于是浪费了一堆时间 去玩js
```javascript
<script type="text/javascript">
/* 鼠标特效 */
var a_idx = 0;
jQuery(document).ready(function($) {
$("body").click(function(e) {
var a = new Array("❤富强❤","❤民主❤","❤文明❤","❤和谐❤","❤自由❤","❤平等❤","❤公正❤","❤法治❤","❤爱国❤","❤敬业❤","❤诚信❤","❤友善❤");
var $i = $("<span></span>").text(a[a_idx]);
a_idx = (a_idx + 1) % a.length;
var x = e.pageX,
y = e.pageY;
$i.css({
"z-index": 999999999999999999999999999999999999999999999999999999999999999999999,
"top": y - 20,
"left": x,
"position": "absolute",
"font-weight": "bold",
"color": "rgb("+~~(255*Math.random())+","+~~(255*Math.random())+","+~~(255*Math.random())+")"
});
$("body").append($i);
$i.animate({
"top": y - 180,
"opacity": 0
},
1500,
function() {
$i.remove();
});
});
});
</script>
```

好了回去写代码咯