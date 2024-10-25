+++
title = 'Linux 配置 VSCode + CMake + C/C++ 开发环境'
date = 2024-10-25T10:31:41+08:00
categories = []
tags = ["Bilibili", "环境", "Coding", "C", "C++"]
+++

这里以 Arch Linux 为例。

这里只介绍比较通用的搭配：VSCode + 微软的 C/C++ 插件 + CMake 插件。虽然我平时更多用 clangd 和 Neovim。

这个可以写的东西不多，就直接看视频吧。

插件：

- C/C++
- CMake Tools
- CMake(LSP)

首先，我们先手动地配置一个 C/C++ 项目。

全手动。即，从命令行编译一个 C++ 文件。

然后，如果你想省事儿，那么，可以试一下我的模板，

<https://github.com/fanlumaster/LinuxCppTemplate>

不过呢，我建议每个人还是自己给自己建立一个模板，这样用起来才放心、熟悉。

最后，如果大家想更多从实际上手的角度来理解 CMake 的使用，我斗胆推荐一下这本 [Modern CMake for C++](https://book.douban.com/subject/37000914/)，刚好前段时间刚出了第二版，很新。如果仅仅是想入个门，那么，读一下第一章也可以有不少收获。

下下期视频(大概率)，我将带大家看一个真实的世界中使用 VSCode + C/C++ 插件 + CMake 插件大型项目：Hyprland。


