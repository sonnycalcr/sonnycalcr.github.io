+++
title = '终端和 Shell 的使用之 Windows 篇'
date = 2024-08-16T21:50:45+08:00
categories = ["工必利其器"]
tags = ["Bilibili", "随笔", "软件测评"]
+++

这篇博客主要来聊一聊我在 Windows 端使用的终端和 Shell 软件。

按：本篇博客大致上只是一个提纲，更详细的内容和使用体验在我的 B 站视频中，毕竟这东西不如直接用视频的形式展示出来比较直观。

## 终端

- Windows Terminal.
- Alacritty，这个之前使用过，后来放弃了。

## Shell

Windows 平台下也就是 pwsh7 这个软件了。其实也没什么太多好讲的，就简单介绍一下我目前使用的一些和终端相关的软件吧。

- PowerShell 7.0+
- $PROFILE
- starship
- fastfetch
- scoop
- Neovim，关于 Neovim 的配置相关后面的视频中会讲，当前只是讲一下它的使用。

一些常用的命令。

```powershell
ls
cls
cd
cp
tree
Get-Command
```

如果想要一些快捷的命令的话，那么，可以去定制 pwsh 的配置文件，比如，去定制一些命令别名、函数之类。

然后，还有一个小技巧，就是在 Neovim 中使用 pwsh，比较方便我们去复制一些内容。


