+++
title = 'UVa272 and UVa10082'
date = 2024-10-27T16:05:02+08:00
categories = []
tags = ["Bilibili", "算法竞赛", "UVa", "算法竞赛入门经典"]
+++

这两道题是整本书中出现的第一道和第二道 UVa 的题目。

- <https://onlinejudge.org/external/2/272.pdf>
- <https://onlinejudge.org/external/100/10082.pdf>

先看 UVa272，这里需要注意两点，

- getchar => 这里之所以使用 getchar，是因为如果使用 scanf 来读取输入的话，那么，像 TAB、空格这样的字符就会被当成分隔符而无法读入；
- EOF 是什么？EOF 表示一个文件的结束，如果是读取一个文件，那么，读取到文件尾时，就会读取到 EOF。更详细的内容可以看：<https://stackoverflow.com/questions/4358728/end-of-file-eof-in-c>。我们在使用命令行的时候，可以使用 Ctrl + D(在 Linux 系统下) 来手动触发 EOF。

额外说一句，第 46 页，

> 如果用“scanf("%d", &n)”读取整数 n，则要是在输入 123 后多加了一个空格，用 getchar 读取的将是这个空格，

这里的意思是先调用 scanf，然后调用 getchar，并不是上来就只调用 getchar。

再看 UVa10082，思路也是一样，毕竟是开篇的题目，所以比较简单。

好，那么这两道题所用到的知识点就是这个 `getchar` 了。

然后，下面是代码时间，写代码的时候，注意一下题目的输入数据的格式即可。


