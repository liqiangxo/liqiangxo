---
title: "Hugo"
date: 2020-07-07T00:09:24+08:00
slug: ""
description: ""
keywords: []
tags: []
math: false
toc: false
---

# 1.常用hugo命令

新建一个文件
```sh
hugo new coder/hilo.md
```
默认http://localhost:1313
如果开了多个端口会随机一个
```sh
hugo server --本地运行 
```
发布
```sh
hugo
```

2.hugo 中文tags 不支持？

3.hugo文件头的作用
draft 草稿 不会build到public

4.config.toml文件详解

重要的是baseurl、theme、themesDir

baseurl需要改成你的github pages的仓库名
theme、themesDir改成主题目录名和主题路径
