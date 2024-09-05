+++
title = 'Windows 系统下的 C++ 编程环境配置'
date = 2024-09-02T03:54:51+08:00
categories = []
tags = ["Bilibili", "C++", "教程"]
+++

## Windows Terminal

重要程度：**必装**。

到微软的应用商店中找到 Windows Terminal 和 Windows Terminal Perivew(预览版) 任意选择一个即可。

![](https://i.postimg.cc/VmjKSpKC/image.png)

## Powershell7.0+

重要程度：**必装**。

下载地址：<https://github.com/PowerShell/PowerShell/releases/tag/v7.4.5>

选择这个 msi 文件进行下载，然后安装，一路默认下一步即可,

![](https://i.postimg.cc/85zg6gq8/image.png)

安装好了之后，可以在 Windows Terminal 中设置一下默认启动 powershell7。

## CMake

重要程度：**必装**。

前提：解决了网络的问题。

首先，通过 scoop 安装 cmake。

如果还没有安装 scoop，请先到 scoop 的[官网](https://scoop.sh/)安装。

然后，执行安装命令，

```shell
scoop install cmake
```

## Visual Studio 篇

重要程度：**必装**。

![](https://i.postimg.cc/dstvhG2b/image.png)

因为是需要 C++ 编译套件，所以把`使用C++的桌面开发`勾选上即可。需要勾选的选项，直接看我下面的截图，

![](https://i.postimg.cc/vYM7fZDF/image.png)

Visual Studio 直接在初始界面创建 CMake 项目即可。

## VSCode 篇

重要程度：**选装**。

来到[VSCode官网界面](https://code.visualstudio.com/download)进行下载。

下载好之后，直接一路下一步，全部按默认的来，因为现在已经 2024 年了，大家的 C 盘没有 1T 也至少 512GB 起步了，不差空间。

安装好之后，安装几个插件，

- C/C++
- CMake

然后，可以把 VSCode 的默认的 shell 设置成 powershell7。 

安装好之后，就可以写简单的 C++ 程序测试一下了。

```cpp
#include <iostream>

int main(int, char**){
    std::cout << "哟西！" << "\n";
}
```

## CLion 篇

重要程度：**选装**。

来到[官网](https://www.jetbrains.com/clion/download/#section=windows)下载安装。

大家可以自行使用破解或者试用。

之后新建一个项目就可以开始编写代码了。

## Neovim 篇

重要程度：**选装**。

安装 Neovim，

```shell
scoop install neovim
```

安装一些常用的软件，

```shell
scoop install neovide     
scoop install 7zip        
scoop install bottom      
scoop install btop        
scoop install fastfetch   
scoop install fd          
scoop install gitui       
scoop install grep        
scoop install gsudo       
scoop install make        
scoop install nodejs      
scoop install ripgrep     
scoop install starship    
scoop install vcredist2022
scoop install which       
```

然后到 pwsh(即 powershell)复制我的 neovim 配置，

```shell
git clone https://github.com/fanlumaster/FanyLazyvim.git $env:LOCALAPPDATA\nvim
```

然后，打开 neovim 等待其自动下载插件，配置一会儿即可，

```shell
nvim
```

然后，在 nvim 中使用 mason 安装 clangd，

```shell
:MasonInstall clangd
```

这样一来，环境差不多就配置好了。

然后，还可以稍微配置一下 powershell，这里就简单设置一下 starship，

```shell
nvim $PROFILE
```

```shell
Invoke-Expression (&starship init powershell)
```

----------

参考：

1、<https://www.lazyvim.org/installation>


