---
layout: post
title: 今天又和 NavigationView 互相伤害
category: Android
tags: Android, java, NavigationView
keywords: java, Android, NavigationView
description: NavigationView really hurts me
---

今天真是太郁闷了……

今天我又和一个Android开发中的事物互相伤害了，这次不是Kotlin也不是anko，是平时一直很老实的NavigationView……

这混蛋来自v7的Design包，是Google的Material Design支持包中的控件之一。启动一个NavigationView需要在外面套一个DrawerLayout。本来是一个很好看的侧滑菜单啊……为什么呢……

我以前有不少项目是使用了NavigationView的，比如[AIAndroid](https://github.com/ice1000/AIAndroid)，比如早期版本的PLasticApp，都是使用 NavigationView 作为导航控件的，怎知今天友谊的小船说翻就翻。

这谜之错误信息：

```
java.lang.RuntimeException: Unable to start activity  ComponentInfo{com.ais.cherry/com.ais.cherry.activity.FirstActivity}:    android.view.InflateException: Binary XML file line #35: Error inflating    class android.support.design.widget.NavigationView

Caused by: android.view.InflateException: Binary XML file line #35: Error inflating class android.support.design.widget.NavigationView

Caused by: java.lang.reflect.InvocationTargetException
```

我当时的内心就是崩溃的。

然后我开始bing，翻遍了 StackOverflow ，翻遍了各种博客，找到的方法都没用……

比如有的人说，把你的Build.gradle的Support包和Design包的版本改为一致。我当时还以为找到救星了，结果我看了看我的Gradle脚本：

```
dependencies {
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile "org.jetbrains.anko:anko-common:$anko_version"
    compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
    compile 'com.android.support:appcompat-v7:24.0.0'
    compile 'com.android.support:recyclerview-v7:24.0.0'
    compile 'com.android.support:cardview-v7:24.0.0'
    compile 'com.android.support:design:24.0.0'
    compile 'com.android.support:support-v13:24.0.0'
    compile 'com.android.support.constraint:constraint-layout:1.0.0-alpha3'
}
```

我的眼泪掉下来……

当时我看的最久的是这篇 [来自 StackOverflow 的恶意](http://stackoverflow.com/questions/30709419/error-inflating-class-android-support-design-widget-navigationview)，结果还是没能解决自己的问题。

最后，我决定，和 NavigationView 友尽，说再见。

原本的导航栏：

<p><img src="/../../../assets/images/andr/nav/1.png" align="center"></p>

看起来还是比较正常……

当时我的怨念极其强烈，简直要冲破机房的天花板了……

每次commit我都要诅咒 NavigationView……

<p><img src="/../../../assets/images/andr/nav/2.png" align="center"></p>

再看看[GitHub上的commit记录](https://github.com/ice1000/PlasticApp/commits/master)，我简直要被我的怨念给腐蚀了……

最后我把UI换成了在Toolbar里面放导航内容：

<p><img src="/../../../assets/images/andr/nav/3.png" align="center"></p>

整体颜色也换成了更Geek的黑色。看起来，感觉还是不错的。

今天一整天都这么不顺……真是的，Studio也这么浮躁，让我很是担忧的电脑的内存……

<p><img src="/../../../assets/images/andr/nav/0.png" align="center"></p>

不过今天还是有好消息的，那就是我的Kotlin插件不知道为什么，Kotlin1.0.3 Build成功了！

```
buildscript {
    ext.kotlin_version = '1.0.3'
    ext.anko_version = '0.8.3'
    repositories {
        mavenCentral()
    }
    dependencies {
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
    }
}
```

其实事情是这样的，我上次解决问题之后，今天我的 1.0.2 再次出现了同样的错误——

<p><img src="/../../../assets/images/java/kt2/1.png" align="center"></p>

[摔桌]

然后我改成1.0.3……居然就成功了！

看来不是版本的问题啊……

第二件好消息是新的PLastic完成了！


## 你学到了什么

+ 如何用Toolbar代替 NavigationView
+ 上次的Kotlin编译器内部报错，原因其实是长得丑
