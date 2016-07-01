---
layout: post
title: Anko's bug really hurts me a lot(Chinese)
category: Kotlin
tags: Essay
keywords: Kotlin, anko, Android Studio
description: I met a greate bug of anko
---

本文比较特殊，不是一般的博客。

## 怨念

怎么说呢。

这篇讲Kotlin+anko的bug的博客，本来已经写了接近一千字了。谁知造化弄人，我边写博客边构建我的项目，结果。

**啪！**

我的电脑就这么关机了。

是的，一瞬间断电。然后我的博客就没有了。

当我感到一股深深地绝望时，我重启电脑，结果特么Windows又开始更新，果然视窗都是辣鸡，进度一瞬间到100%，然后就一直不动了。我非常无奈，于是换了台电脑刷题……

等这家伙终于搞定了，我重新打开电脑，发现Notepad++的备份全都没了。千字的博客就这么付诸东流，换了任何人想必都不好受。

我真的不知道我到底造了什么孽，难道说这次期末考试的原因？

我真的没有心情再去重写这篇博客了。先是Kotlin工具链报错，我都写了很多东西了，结果给我来个断电关机！？简直和秋寒的PhpStorm一样！

不过既然写了博客，图片也截了，这里还是补一补内容吧。

本文主要内容是讲解遇到Kotlin编译报错的解决方案。

## 遇到问题

在我刚开始构建我的项目的时候，我遇到了飞来横祸。

我的Kotlin编译器，发生了内部错误。

<p><img src="/../../../assets/images/java/kt2/1.png" align="center"></p>

这对于任何程序员来说，都是一个巨大的打击。我开始让自己保持冷静，不要慌张。遇到这种情况应该想办法，而不是自暴自弃。就算是帝球那样的聚聚也有编译失败的时候。~~当然，C++编译失败是很正常的事情。~~ 不过要是Java或者Kotlin编译失败，就有点离奇了。Java或者Kotlin本身工具链是很稳定的，要是出事了我猜十有八九是anko的锅。

强大的代价，就是不稳定啦。

周围的学NOIP的同学们都一脸看智障的眼神看我，我心中也默默诅咒他们的minGW，他们的DEV C++出车祸。

当然，写OI的话，一般都不会出事。

我的脑子开始飞快地旋转，寻找解决方案。

## 方案一

更新我的Kotlin插件。今早上在IntelliJ IDEA里更新了我的Kotlin插件，不过还没更新Android Studio的。万一更新了就没问题了呢？抱着这样的心态，我开始寄希望于更新上。

首先挂上Lantern，下载插件自然是需要科学上网的，咳咳。中国真是啥都排斥，连RubyGems都排斥，我真是无语了。

<p><img src="/../../../assets/images/java/kt2/2.png" align="center"></p>

看图不说话，你们懂。

<p><img src="/../../../assets/images/java/kt2/3.png" align="center"></p>

我这都出车祸了，哪还敢选Early Access Program。只有老老实实选Stable。不过我平时倒是有选EAP的习惯，我的Android Studio、Android SDK和IntelliJ IDEA都是EAP。所以出车祸是必不可少的，因此也经常遇到问题。不过这次这个问题几乎是无解的，因为Kotlin本身就是小众的技术，要想找到哪个冷门bug的帮助，恐怕是难上加难啊。

在科学上网的帮助下，我顺利下载了1.0.3版本的Kotlin编译器，顺手打开了Genymotion准备在编译之后顺利运行。

看到提示重启Studio以使用插件，我兴高采烈地重启了Android Studio。

<p><img src="/../../../assets/images/java/kt2/4.png" align="center"></p>

接下来发生了什么，我都已经在开头说明了。可以猜到，此时我真的是生无可恋。我坐在电脑面前唉声叹气，诅咒着别人的minGW……

<p><img src="/../../../assets/images/java/kt2/5.png" align="center"></p>

就是它带来了这场灾祸。看着那熟悉的启动界面，真是又爱又恨。

于是我重启电脑之后再次编译，再次打开Genymotion，默默摩擦起了双手，满眼放光地看着电脑。

此时我的心情，既有一点点兴奋，也有一点点激动，不知道该说什么好。毕竟，这是我第一次独立解决编译工具链的问题。之前都是上StackOverflow搜索问题，然后各种围观聚聚，找到答案之后各种兴奋，不过这次，我要自己当一回聚聚了。虽然只是更新插件版本的问题，可这也是在和别的程序员所造成的bug作抗争，这本身就是一件很伟大的事情。

期待着更新后的插件能够编译成功，并在虚拟机上运行——

<p><img src="/../../../assets/images/java/kt2/1.png" align="center"></p>

[摔桌]

启动方案二。

## 方案二

作为一个激进的程序员，任何工具出故障第一反应就是更新。那么，如果更新解决不了的话，那就只有反更新了——改回旧版本。

将全局的build.gradle中的常量 ext.kotlin-version ，从1.0.3改成1.0.2。这里说一句，我出车祸的版本是1.0.2-1，新版是1.0.3 ，我改回了一个更旧的版本。

```ruby
buildscript {
    ext.kotlin_version = '1.0.2'
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.1.2'
        classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"

        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}
```

修改后的build.gradle。

希望不要再打脸了，编译运行。我已经在电脑面前划起了十字。Amon。

## 成功

<p><img src="/../../../assets/images/java/kt2/6.png" align="center"></p>

我几乎要从电脑面前跳起来了。

> 还有谁！！！！！！还有谁！！！！

熟悉的Instance Run，熟悉的Log，都回来了！

## 结论

没有征服不了的编译器，只有懒得思考、懒得动手的失败者。

## 你学到了什么
1. 遇到工具的问题的解决问题的思路
1. 关于Kotlin编译器内部错误的解决方案
1. 遇到报错，保持冷静
1. 任何情况下你的工具应该是最新版本的
1. 也就是上文的结论。没有征服不了的编译器，只有懒得思考、懒得动手的失败者。

冰封与大家共勉。