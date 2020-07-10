---
title: "Hilo"
date: 2020-07-06T23:34:50+08:00
draft: false
---

本文用于记录在hilo学习过程

#### 1.根据<a href="https://github.com/hiloteam/Hilo/blob/dev/README_ZH.md" target="_blank">hilo文档</a>搭建环境


#### 2.遇到没有npm 就去百度怎么npm 然后装node等等

#### 3.有了npm 终于开始了npm install
结束的时候提示 npm audit fix 和 npm audit fix --force 然后一堆警告

然后 执行 gulp

```sh
H:\gitlib\Hilo-dev> gulp
AssertionError [ERR_ASSERTION]: Task function must be specified
    at Gulp.set [as _setTask] (H:\gitlib\Hilo-dev\node_modules\undertaker\lib\set-task.js:10:3)
    at Gulp.task (H:\gitlib\Hilo-dev\node_modules\undertaker\lib\task.js:13:8)
    at createBuildFormatTask (H:\gitlib\Hilo-dev\gulpfile.js:52:10)
    at H:\gitlib\Hilo-dev\gulpfile.js:126:5
    at Array.forEach (<anonymous>)
    at Object.<anonymous> (H:\gitlib\Hilo-dev\gulpfile.js:125:13)
    at Module._compile (internal/modules/cjs/loader.js:1138:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1158:10)
    at Module.load (internal/modules/cjs/loader.js:986:32)
    at Function.Module._load (internal/modules/cjs/loader.js:879:14) {
  generatedMessage: false,
  code: 'ERR_ASSERTION',
  actual: false,
  expected: true,
  operator: '=='
}
```
网上说这是因为 gulp 版本不一致导致
```sh
H:\gitlib\Hilo-dev> gulp -v
CLI version: 2.3.0
Local version: 4.0.2
```

于是 卸载本地版本
```sh
npm uninstall --save-dev gulp
```
按照一致的版本
全局安装
```sh
npm install -g gulp@2.3.0
```
本地安装
```sh
npm install gulp@2.3.0
```
再看
```sh
H:\gitlib\Hilo-dev> gulp -v
[gulp] CLI version 2.3.0
[gulp] Local version 2.3.0
```

