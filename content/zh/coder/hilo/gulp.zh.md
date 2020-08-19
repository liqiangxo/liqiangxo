---
title: "Gulp"
date: 2020-07-13T13:32:05+08:00
slug: ""
description: ""
keywords: []
tags: ["gulp"]
math: false
toc: false
---

因为之前一直报错
```sh
AssertionError [ERR_ASSERTION]: Task function must be specified
```
mac windows 都一样 报错这个错无赖  跑过来研究研究看看到底gulp 是什么鬼

原来gulp是一个node自动构建工具
```
https://v3.gulpjs.com.cn/docs/getting-started/
```
根据入门我发现我闲的版本和是用的这个老的api

然后我gulp -v总是是新的api

我就纳闷了我的不管是package.json 里面还是我自己专门去选定的版本都是3.9.1
怎么结果还是4.0.2了呢？

最后发现问题是每次npm install执行结束之后
有一个npm audit fix 搞的鬼

npm audit fix 真不能乱用

这个东西自动把我的gulp版本搞成了新版本。吐血啊。

最后我在hilo里面直接根据文档里面的命令顺序  完美生成新项目。

```sh
 npm install
 gulp

```

总结：所以命令都有弄清楚原理再执行，就不会有这么多奇怪的问题了。