---
title: "Mygit"
date: 2020-07-06T23:41:21+08:00
draft: false
---

本文用于记录自己git使用过程中的问题

1.windows 下面拉取不下来子模块
需要勾上

2.git更新慢
解决方法：
   在网站 https://www.ipaddress.com/ 分别搜索找出对应的ip：
      github.global.ssl.fastly.net 
      github.com
  在hosts文件末尾添加两行(对应上面查到的ip)
      199.232.5.194  github.global-ssl.fastly.net
      140.82.114.4  github.com

    我靠改了之后简直神速啊
3.Windows host
/windows/system32/drivers/etc
