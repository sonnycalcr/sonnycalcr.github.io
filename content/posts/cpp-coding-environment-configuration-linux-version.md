+++
title = 'Cpp Coding Environment Configuration Linux Version'
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

## neovim

首先，安装一些必要的软件，

```shell
nodejs
npm
```
