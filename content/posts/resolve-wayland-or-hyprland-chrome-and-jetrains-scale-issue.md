+++
title = '解决 Hyprland/Wayland 下 Chrome/Chromium 系列软件和 Jetbrains 系列软件的缩放和输入法使用的问题'
date = 2024-11-05T02:16:07+08:00
categories = []
tags = []
+++

很多朋友在使用 Hyprland/Wayland 的时候，可能会遇到这样一个问题，那就是 Chrome、VSCode 和 Obsidian 这类基于 chromium 的软件的界面字体和 UI 比较模糊，不够 sharp 和清晰。那么，我这里简要介绍我常用的两种方法。

一种是像 VSCode/Chrome 这种可以直接加 flags 的，那么，我们直接在在配置目录中新建一个 `code-flags.conf` 然后加上一些启动参数即可，

```yaml
--ozone-platform-hint=wayland
--enable-wayland-ime
```

对于 Chrome，我们则需要写一个 `chrome-flags.conf`，

```yaml
--enable-features=UseOzonePlatform
--ozone-platform=wayland
--enable-wayland-ime
```

然后是一些我们不知道其 flags 文件怎么命名的软件，比如，Obsidian 和 Jetbrains 家的软件，那么，我们可以直接自制一份我们自己的 desktop file 来覆盖系统默认的，这里拿 Obsidian 举例，我们去 `/usr/share/applications` 下去复制一份 obsidian.desktop 文件到 `~/.local/share/applications/` 下面，然后在 Exec 那一行加一些启动参数即可，

```yaml
Exec=/usr/bin/obsidian %U --enable-features=UseOzonePlatform --ozone-platform=wayland --enable-wayland-ime
```

Jetbrains 家的软件也是一样，加一下它们提供的 wayland 相关的参数即可，

```yaml
Exec=intellij-idea-ultimate-edition %u -Dawt.toolkit.name=WLToolkit
```


