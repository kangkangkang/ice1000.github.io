---
layout: post
title: 轮子狂魔造引擎 第三章
category: Game
tags: Java, Game, Engine
keywords: Java,Game,Engine
description: make a game engine chapter 3
---

// 今天是长者生日，作为OIer我要说声生日快乐。
// 苟利国家生死以，岂因祸福避趋之。
// 顺便因为写了粒子，就去写了个膜蛤射击小游戏作为粒子效果和键盘监听的demo。将会和0.3.3的release一起发布。

## 引擎的设计
游戏引擎也得遵守基本法啊，当然是生命周期+OOP的设计。你要将整个引擎封装到，用户（即使用引擎的开发者）需要做的事情几乎就是写DSL。并且你的引擎的游戏设计思路要符合常规思维，用起来才会舒服。程序员都是为用户服务的，像我这种写游戏引擎的就应该为程序员服务。

希望我的游戏引擎用起来就像JetBrains系列IDE一样顺手。虽然一个是框架一个是IDE，但是都存在一个用户体验的问题。

本文主要大致讲解寒冰引擎的设计思路。本文会涉及到编程相关的东西，不过涉及到的都是OOP通用的概念，不需要会Java，你会Python之类的语言也能看的。

## 生命周期模式
第一篇博客就提到了这个概念——生命周期模式，并介绍了几个方法，当时我是把这些方法做成抽象方法的。后来发现这是一个错误的决定，有两个原因。<br/>
+ 本来有些时候不需要重载相应的生命周期方法，强制要求重载会增加完全不必要的代码量。不然我就没有“65行代码实现简易Flappy bird”这句广告词了。
+ 我之前是计划让这个东西支持Ruby的——通过JRuby做一套接口来完成。昨天和前天晚上我都在尝试使用JRuby调用我的Game类，一直报错，说找不到构造。我当时就懵逼了，我的构造方法明明是public的，然后我就很气愤地在commit message里面写了一句“Fuck JRuby”。我曾经去栈溢出和谷歌找，找了半天，搜出很多结果，不过都和我的不一样。当然我也试了试百度和bing，bing搜出来两个结果，百度首页放眼望去就是广告，mdzz。当时我的Game类是抽象的，后来经过JRuby项目的一位维护人员（嗯，你没有看错，JRuby项目）看到了我的commit记录，上面写了个“Fuck JRuby”，然后就过来给我comment了一个，跟我解释了一下可能的问题。其中提到，JRuby的Ruby类并不是Java类，它没有Java的构造方法等专属的东西，所以建议我不要把Game做成抽象的。当时我去改了一下，Game在不是抽象的情况下，那个诡异的报错就消失了。。。我当时极其崩溃，明明自己的问题还Fuck JRuby，结果引来了JRuby维护者来查水表。嗯，这算是真正意义上的查水表了。。。但是人家还是很友善的。出于礼貌，我回复的时候专门说了，Sorry for my commit message。。虽然是网上的交流但是感觉自己Low到爆啊。以后涨姿势了，JRuby不能继承Java的抽象类。

跑偏了。

所以说生命周期方法不能抽象！最好是做成空大括号。

那么寒冰的生命周期又是怎样的呢？大概是这个流程：

1 构造、初始化 -> 2 onInit() -> 3 初始化JPanel和BufferedImage -> 4 开线程 -> 5 计算坐标并绘制所有对象 -> 6 onRefresh() -> 7 睡线程 ->  8 回到5 -> 9 onExit()

其中，在死循环中又有这样的调用过程：

- 用户点击 -> onClick(e: OnKeyEvent)
- 鼠标事件 -> onMouse(e: OnMouseEvent)
- 失去焦点 -> onLoseFocus()
- 得到焦点 -> onFocus()

以上一共这么几个生命周期方法：
onInit(), onClick(), onRefresh(), onFocus(), onLoseFocus(), onMouse(), onExit()

这样用户就能很好地把控刷新的问题了。

## 提供API
为了简化用户操作，我还封装了提供以下功能的API：<br/>
截屏、增加对象、批量增加对象、删除对象、批量删除对象、重载鼠标、设置刷新率、设置键盘监听等。

其中我认为最有意思的是截屏，调用之后返回当前屏幕状态。

## 游戏引擎主体结构
下面说说寒冰的主体结构。

前文一直提到的“对象”这个概念，到底什么是对象呢？其实就是我们平时所说的“精灵(Spirit)”，我记得Unity里面貌似就叫这个。不过在代码中，这东西被称为gameObject。我在这里沿用了Object这个称呼，不过为了和JVM基类Object区分开，我就将这个对象接口命名为FObject。F是FriceEngine的意思。

然后我设计了三个类/抽象类/接口来实现FObject，分别是ShapeObject，ImageObject和ParticleEffect。最后一个是刚刚才完成的粒子效果，以一个对象的形式呈现。ShapeObject是指定一个形状和颜色的Object，ImageObject是指定一个图片的Object。他们分别需要一个叫做FResource的资源类，通过这个类保存、传输资源。

FResource的继承关系就比较复杂了，FResource的子类有ColorResource、ImageResource和ParticleResource，分别对应上面的三个Object。而ImageObject的子类又有FileImageResource、WebImageResource、FrameImageResource、PartImageResource。顾名思义，一个从文件构造，一个从URL构造，一个是逐帧播放图片的Resource（即不同时刻返回的图片不同，一直刷新会看到逐帧动画的效果），一个是通过别的Object的一部分来构造自己的Resource。

这里就看到我的逐帧动画实现了，我认为逐帧动画和属性动画应该严格区分开。属性动画我是单独作为动画支持的，而逐帧动画却是一种图片的形式呈现。用户可以把逐帧动画想象成是gif图片，然后通过构造这个逐帧动画FrameImageResource来实现逐帧动画的播放。






