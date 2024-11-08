+++
title = '在你开始之前'
date = 2024-11-06T17:53:22+08:00
categories = ["Android", "Jetpack Compose"]
tags = ["Android", "Jetpack Compose", "Bilibili"]
+++

配套的书是这本：<

> 如何看自己当前的 Kotlin 的版本？

在 build.gradle.kts 中，

```kotlin
// Top-level build file where you can add configuration options common to all sub-projects/modules.
plugins {
    alias(libs.plugins.android.application) apply false
    alias(libs.plugins.kotlin.android) apply false
    alias(libs.plugins.kotlin.compose) apply false
}
```

我们点进第二行的版本中去查看即可。现在 Kotlin 的版本为 2.0.0.

> 如何看 Jetpack Compose 的版本？

<https://developer.android.com/develop/ui/compose/compiler>

也是类似的道理，现在 Jetpack Compose 的版本为 2.0.0.

> 书上是建议我们使用 Jetpack Compose v1.2.1，这里我们不听他的，我们直接用最新版，遇到不兼容的地方，就直接去解决就行。

我们这里可以先把代码 clone 一份下来备用，

```shell
git clone https://github.com/kodecocodes/jet-materials.git
```

> 如何阅读这本书？

直接从开头然后按照顺序读下去即可。

> 开发环境的搭建。

安装 Android Studio 即可。

对于测试的设备，直接使用手头的安卓手机。


