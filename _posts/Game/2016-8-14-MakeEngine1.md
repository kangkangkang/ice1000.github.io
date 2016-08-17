---
layout: post
title: 轮子狂魔造引擎 第一章
category: Game
tags: Java, Game, Engine
keywords: Java,Game,Engine
description: make a game engine chapter 1
---

### 文章其他地址：
- [知乎](https://zhuanlan.zhihu.com/p/22053395)
- [indienova](http://indienova.com/u/ice1000/blogread/1043)

边刷OI题边写博客，求不被老师发现 (￣ˇ￣)/ 

## 缘由
想去弄个游戏，本来勉强上手了Unity，却一直找不到合适的教程（估计是商业化太严重了），现在Unity也就是Hello World水平，不过还因此又装上了Project Rider EAP和Visual Studio 2015，两个都没怎么用。不过倒是见识了一下宇宙最强IDE，感觉没有我之前听到的那么糟糕，挺好的一个IDE。不过我心中的最强还是IntelliJ IDEA or Android Studio，哈哈。

呃又因为我最熟悉的语言都是JVM的，再加上之前使用[JustWeEngine](https://github.com/lfkdsk/JustWeEngine)开发[Android原生游戏](https://github.com/icela/StudioVSEclipse)的经历，让我产生了自己搞一个游戏引擎的想法。首先JVM平台资源丰富，而且有Write once, ~~debug~~ run everywhere的优点，再加上Java程序员多，我决定使用自己深爱的Kotlin来做一个这样的Game Engine。

## 说在前面
那些想说“没代码说个JB”的人，你们大可以去直接阅读我引擎的源码。前提是你要看得懂Kotlin。我不想在这个系列里面放太多代码，因为这样会导致我的文章变得Platform-dependent，就不适合非JVM工作者阅读了。我是希望.Net工作者、C++工作者、前端等各行各业的人士都能看懂我的这份自制引擎的博客。

## 第一件事
当然是起一个帅气的名字。。。

想起做引擎，第一件事就是把JVM圈内人士[@Eldath](https://github.com/lizhaohan001)拉过来，然后开了个组织，[icela](https://github.com/icela)，专门扔游戏开发相关，并且把Castle-game也扔了过去。

然后我就用我的名字和[@Eldath](https://github.com/lizhaohan001)的名字拼起来组成了这个引擎的名字，叫寒冰。英文名本来想的是直译——FrozeEngine，但是一搜，发现已经有个HTML5游戏引擎叫这个名字了，于是我就把元音和后面的辅音换了一个，FriceEngine。

## 第二件事
当然是构思整个框架。。。

我选择采用和 JustWeEngine 以及 Android 原生App一样的生命周期模式，不过我私以为 JustWeEngine 的设计是有问题的，而且文档很简陋。 据作者本人口述，他自己用的时候都要看源码。这就说明他的模式有问题。所以我要重新设计，尤其是动画和碰撞。

然而这么早想这些其实没卵用，先把框架搭起来。你需要一个Game基类，里面放一堆抽象的生命周期方法，然后在运行过程中分别调用他们。我设计了如下生命周期方法（内容摘自引擎帮助文档）：

Method|Usage
:---|---:
onInit()|初始化时调用
onExit()|用户按下退出键时调用
onRefresh()|尽可能多、快地调用，刷新方法
onClick(OnClickEvent)|鼠标点击时调用
onMouse(OnMouseEvent)|鼠标状态变化时调用
onLoseFocus(OnWindowEvent)|失去焦点时调用
onFocus(OnWindowEvent)|获得焦点时调用

是不是很简单呐？至于键盘事件，让开发者自己去注册好啦。反正又不复杂。我已经帮你节省了好多代码了诶。

然后我的Game类继承了Frame，以此为主窗口。你可能会问，你特么煞笔啊，有Swing的JFrame不用你去用awt的Frame，这不是落后于时代了吗？我只能说Naive，因为awt虽然扩展性不行，但是据说（仅仅是据说，我那本GUI书上说的，要是我说错了怪书），awt速度比Swing快。我这个几乎全是轮子的项目怎么可能需要使用GUI控件的扩展性呢？我只是需要仅仅是一个可以显示图片的空间而已。

不过显示图片我还是选择了Swing控件，扔了个JPanel进去。因为Panel实现双缓冲刷新失败了。

搭好框架了，下一步是什么呢？

## 第三件事
人人都会写的图像处理，读取图片刷进一个窗口。先不急着做双缓冲，先直接显示。双缓冲所谓的多占一点空间对现在的电脑来说完全没有问题，不要在意那么多。不过做这个之前，我们先让这个引擎跑起来。

## 第四件事
游戏肯定得刷新啊，于是我又学 JustWeEngine 让游戏基类实现了Runnable，然后重载了run方法，在构造方法最后一句Thread(this).start()，林抠死大头！

然后你需要在run里面不停调用onRefresh，然后刷新图片，然后再睡线程。为什么要睡线程？刷新太快你可以试试效果，谜之效果啊。闪瞎你的狗眼。我的做法是让开发者指定每秒刷新次数，然后Thread.sleep(1000.0 / refreshPerSecond)。

## 第五件事
完成插入图片。这我就不说了，方法多得是。

## 结语

最初话先写这么多，刚做完加速度系统，欢迎围观我家萌萌哒[寒冰引擎](https://github.com/icela/FriceEngine)！之后这个系列还会更新哦。



