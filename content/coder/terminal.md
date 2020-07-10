---
title: "命令行常见问题记录"
date: 2020-06-25T17:28:15+08:00
slug: "terminal"
keywords: ["terminal", "命令行","中文乱码"]
draft: false
tags: ["link"]
math: false
toc: false
---


#命令行常见问题记录（***第一次***_用>markdown_）

###1. 命令行中文乱码问题
1. 缩进一 解决问题：直接在命令行输入如下内容也行能解决问题
```sh
>chcp 65001
Active code page: 65001
```
2. 你还可以通过chcp命令查看cmd的编码设置
GBK2312的代码页编号是936，然后改成utf-8的编码即可，utf-8对应的代码页编号是65001，
所以执行chcp 65001就可以把cmd的编码设置成uft-8了，这样就解决了乱码问题
```sh
>   chcp
Active code page: 936
```
***