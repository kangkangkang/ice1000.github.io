---
layout: post
title: IDEA for beginners 4, Integrated Version Control System(Chinese)
category: Java, IDEA
tags: Java, IntelliJ IDEA
keywords: Java,IDEA, PhpStorm,WebStorm,PyCharm,Rider,RubyMine,CLion,Android Studio,Git,GitHub
description: IDEA for beginners chapter 4
---

本篇主要讲述IntelliJ IDEA的集成版本控制系统。由于集成版本控制系统是基于JetBrains产品平台本身，因此本文同样适用于JetBrains其它产品，包括但不仅限于PhpStorm,WebStorm,PyCharm,Rider,RubyMine,CLion,Android Studio。

版本控制对于程序员来说是一个非常重要的概念。不了解版本控制的话你就孤陋寡闻了，请先使用搜索引擎，了解一下版本控制这个东西吧。

目前最常用的版本控制工具应该是Git，然后还有SVN、CVS、Mercurial、Perforce、Subversion等，这些比较流行的版本控制系统IntelliJ IDEA都有对应的插件支持。这些插件都可以在IntelliJ IDEA插件搜索器里找到。我个人使用的是IntelliJ IDEA Ultimate（帮人家贡献了一点点中文官网的翻译，人家送了我一年订阅），里面都有内置的这些插件。在安装IntelliJ IDEA时，它会问你要安装哪些版本控制插件。我个人平时使用Git，所以就只勾选了Git和GitHub。

至于为什么要选GitHub，原因你懂的。程序员约架、同性交友、膜蛤圣地。

## 依赖

- Git（本教程中是2.7.0）
- GitHub账号一个
- IntelliJ IDEA

## 基本配置

首先你需要安装Git工具，请前往官网下载。我就不作更多说明了。下载安装之后记住你安装的位置。

然后打开IntelliJ IDEA，并转到Settings界面。如下图所示，确保你已经开启了这两个插件。

<p><img src="/../../../assets/images/java/idea4/1.png" align="center"></p>

请忽略我诡异的线条……之前都是用的QQ截图，今天学校把机房的网断了，我就只有用Windows自带的截图工具，那东西比较猥琐，博客的push和commit都是靠的手机……心疼流量。




