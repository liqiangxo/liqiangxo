---
title: "Hugo"
date: 2020-07-07T00:09:24+08:00
slug: ""
description: ""
keywords: []
tags: ["hugo"]
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

# 2.[hugo语法](https://hugo.aiaide.com/post/hugo%E6%A8%A1%E6%9D%BF%E7%9A%84%E5%9F%BA%E6%9C%AC%E8%AF%AD%E6%B3%95/)

    1.{{.}}
    点`.`代表传递给模板的数据, 表示当前模板的上下文, 他可以是go语言中的任何类型, 如: 字符串, 数组, 结构体等.

    2.{{/* comment */}}
    注释

    2.{{/* comment */}}
    注释

    3.空格处理
    // 清除 pipeline 前后的空格
    {{- pipeline -}}

    // 清除 pipeline 前面的空格
    {{- pipeline }}

    // 清除 pipeline 后面的空格
    {{ pipeline -}}

    3.{{$变量名 := "值"}}
    变量


    4.{{$变量名 := "值"}}
    变量

