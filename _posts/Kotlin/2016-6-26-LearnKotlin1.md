---
layout: post
title: 如何让孩子爱上Kotlin第一章：环境搭建
category: Kotlin
tags: Kotlin
keywords: Kotlin
description: The way to learn kotlin
---

很早以前就打算写Kotlin的教程了。明天期末考试，今晚就先写一篇关于学习路线的博客吧。❤(ӦｖӦ｡)

本文主要内容是学习路线，为初学者指明一条清晰的学习路线。你并不会在本文看到关于Kotlin这门语言的具体信息，这些内容会在之后的博客中出现。

不要想太多，本文完全原创。我蹲在宿舍里面写的。(*´ڡ`●)

## 冰封是怎么认识Kotlin的

冰封作为一个JetBrains的脑残粉，时常拜访JetBrains的官网，偶尔会在一些神秘的角落发现一些很有趣的东西。ლ(´ڡ`ლ)

首页的“Language”选项卡下就有两个选项，我都有涉猎，MPS是一个比较复杂的系统，以后的博客有一定概率会讲到。而Kotlin就是本文的主角了。

## Kotlin是什么

Kotlin是一门基于JVM的编程语言，支持编译成Java平台的.class目标文件和JavaScript文件。支持Java字节码是因为这门语言本身基于Java，不过为了方便web开发和独立于JVM的运行，Kotlin团队也引入了JavaScript的编译。

那么，Kotlin作为一门编程语言，有哪些特点呢？（；^ω^）

首先，它是一门面向对象(Object-Oriented )的语言。它和它的亲爸爸Java除了反射(Reflection)之外完美地兼容。也就是说，如果你曾经使用Java编写过一个工具类，不过你现在却更喜欢使用Kotlin编程，那么你完全可以在Kotlin里面像调用一个Kotlin类那样调用你曾经写过的Java类。反过来，你也可以让你那些仍然在使用Java的同事直接调用你通过Kotlin编写的类。

至于Kotlin和Java所不那么友好的地方，大概有以下几处：

+ 反射机制不同。
+ Kotlin支持把函数直接写在文件里(就如C语言一样)，而Java的一切的一切都在类中。
+ Kotlin没有静态方法这个概念，却引入了object class和companion的概念。不过可以用单例模式来解决这个语言不兼容的问题。
+ Kotlin目标文件的运行需要一个单独的jar包的支持，叫kotlin-runtime.jar，不过这个不大，体积不到1MB。而如果要使用反射的话，还需要包含另一个jar包，叫kotlin-reflection.jar，这个就比较大了，2MB左右。

不过就如Java8引入了lambda一样，这门语言同样注重对于函数式编程的支持。它的优点是向下兼容到Java6，也就是说Kotlin目标文件可以直接在原生的mac电脑上运行(OS X预装JDK6)，并且你可以在里面使用lambda。

它和Swift一样，拥有空指针保护(Null-Safety)的特性。每个变量必须保证时刻为非Null，否则需要用问号来标记。在与Java的互相继承中，Kotlin中被声明为非Null的变量在Java的参数表里会有@NotNull标记。

插一句，Kotlin的语法和Swift其实特别像。只不过Swift的原生API的啰嗦程度又把原本的简洁给破坏了。。。这只是我个人观点。抛开鄙视链不谈我还是很喜欢Swift的。

Kotlin也是一门开源的语言，源代码可以在[JetBrains对应的GitHub仓库](https://github.com/JetBrains/Kotlin)找到。

另外，Scala是什么？(；一_一)

## 适用人群

这个是按照推荐程度排序的。越前面的人群，越推荐他们使用Kotlin。

不要为排名所误解，任何在此列出的人群都非常适合学习Kotlin！

1. Android开发者(这是目前Kotlin的主战场)
1. J2EE后端开发者
1. 跨平台桌面应用开发者
1. 数据库程序员
1. 厌倦Java啰嗦的人
1. 想学习新技术的JVM工作者
1. 认为冰封可爱的人
1. JetBrains的粉丝

另外，十分建议在学习Kotlin之前先学习Java。

## 环境搭建

Kotlin团队为用户考虑得非常周到，不仅仅出品了IDEA插件，还为Eclipse用户提供了对应的插件。不过平心而论，IDEA插件的体验比Eclipse体验真的好太多了。

独立编译器是为命令行爱好者提供的，不过其实冰封个人认为最良心的是免费的[web IDE]( http://try.kotlinlang.org)，他们称之为“try kotlin”。这个web IDE是开源的，也可以在GitHub上面找到。

而JetBrains出品的IntelliJ IDEA从15开始就原生支持Kotlin。至于业界公认最强大的IDE，IDEA提供的编程环境自然是有着非常好的体验。关于如何安装IDEA我已在另一篇博客中说明。

下载链接官网都有提供，下文有链接，请随意点击。

## 为什么选择Kotlin

它是一门非常复杂的语言，拥有非常多的语法糖。这让它的语法变得非常简洁，写起代码来代码量也是少得可怜，比起Java那一言不合就上千行的毛病，Kotlin要好得多。如果你对Kotlin足够熟练，那么你可以将更多精力放在实现逻辑上，而不是具体的“写代码”上，从而提高你的工作效率。

## 如何让孩子爱上Kotlin

首先，了解任何东西都应该先跑到人家[华丽丽的官网]( http://kotlinlang.org)逛一逛。你可以在这里找到一些关于Kotlin的基本信息，以及前文所提到的编译器下载，还有说明文档和web IDE的传送门。

官网有一个非常漂亮的Hello World程序。

然后就是这篇[官方教程](http://kotlinlang.org/docs/reference)了，说实话我感觉我再怎么写教程也写不过这篇官方的。。

当你看完官方教程之后，再去写一些自娱自乐的小程序来继续熟悉这门语言，就像你曾经学别的编程语言那样。

这时候你的Kotlin水平已经和我很接近了，差不多可以将这门语言投入你的生产了。＼(^o^)／

## 进阶学习与拓展阅读

接下来推荐大家通过这篇[来自白俄罗斯的awesome-kotlin](https://github.com/KotlinBy/awesome-kotlin)以及他们提供的一个[awesome-kotlin搜索器]( http://kotlin.link)来了解这个世界上的程序员们使用Kotlin编写的程序，以及一些很有趣很厉害的library，比如NoSQL数据库工具、Web开发框架、Android开发框架等。

顺带一提，我的项目[Dekoder]( https://github.com/ice1000/Dekoder)也被收录其中。(*´ڡ`●)

另外，我知道有很多英语困难的朋友们，贴心的小可爱冰封也为你们准备了一个[经过自己一节计算机课粗糙翻译的awesome-kotlin](https://github.com/KotlinCN/awesome-kotlin)，目前还在翻译中，不过我有多懒你是知道的，况且我还有太多别的坑，所以欢迎志愿者参与维护，以及协助翻译。

冰封期待你的pull request。

另外欢迎大家参考[我的知乎回答: Android开发Kotlin你目前遇到过哪些坑？](http://www.zhihu.com/question/36735834/answer/105409238)，里面有着冰封的血泪史，希望大家不要重蹈冰封的覆辙｡･ﾟ･(ﾉД`)･ﾟ･｡

最后啰嗦一句：anko是真的黑科技！