+++
title = 'Linux 系统下的 C++ 编程环境配置'
date = 2024-09-02T03:54:59+08:00
categories = []
tags = ["Bilibili", "C++", "教程"]
+++

本文假定读者的 Linux 环境为 Arch Linux + KDE。

## Kitty

重要程度：**必装**。

直接命令行安装，

```shell
yay -S kitty
```

## fish

重要程度：**必装**。

直接命令行安装，

```shell
yay -S fish
```

kitty 和 fish 安装好之后，其实就基本可以使用了。

## gcc

重要程度：**必装**。

直接命令行安装，

```shell
yay -S gcc
```

## CMake

重要程度：**必装**。

直接命令行安装，

```shell
yay -S cmake
```

## VSCode

重要程度：**必装**。

直接命令行安装，

```shell
yay -S visual-studio-code-bin
```

安装好之后，安装几个插件，

- clangd
- CMake

然后，可以把 VSCode 的默认的 shell 设置成 fish。这个直接在 `settings.json` 配置文件中加一行配置即可，

```json
"terminal.integrated.defaultProfile.linux": "fish",
```

然后，就可以新建一个项目试一下使用了。

如果有遇到 cmake 插件让选择编译器的，记得选择 gcc，

![](https://i.postimg.cc/sfD3BqW9/Screenshot-20240902-093513.png)

## Neovim

首先，安装一些必要的软件，

```shell
yay -S nodejs
yay -S npm
yay -S p7zip
yay -S bottom
yay -S fastfetch
yay -S fd
yay -S gitui
yay -S grep
yay -S ripgrep
yay -S starship
```

然后，在命令行中复制我的 neovim 配置，

```shell
git clone https://github.com/fanlumaster/lazyvim-archlinux.git ~/.config/nvim
```

然后，运行 neovim，

```shell
nvim
```

然后，在 nvim 中使用 mason 安装 clangd，

```shell
:MasonInstall clangd
```

这样一来，环境差不多就配置好了。

对于 Linux 用户，我想对命令行应该都不陌生，所以，就不去讲配置 starship 这种比较简单的操作了。


