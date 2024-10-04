+++
title = '谷歌搜索屏蔽CSDN'
date = 2024-10-04T23:31:52+08:00
categories = []
tags = ["Bilibili", "小技巧"]
+++

思来想去，还是把 CSDN 直接屏蔽掉吧。

首先，安装 [ublacklist](https://chromewebstore.google.com/detail/ublacklist/pncfbmialoiaghdehhbnbhkkgmjanfhe)，

然后，找到 options(选项)，

![](https://i.postimg.cc/zB7B3QvD/image.png)

直接写一个模糊匹配的规则即可，

```txt
*://*.csdn.net/*
```


