---
layout: post
title: 轮子狂魔造引擎 第二章
category: Game
tags: Java, Game, Engine
keywords: Java,Game,Engine
description: make a game engine chapter 2
---


说话之前先扔几个链接：<br/>
[视频1，分两段，为刚做的时候的样子](http://www.bilibili.com/video/av5803264/)
[视频2，刚录的几个Demo演示](http://www.bilibili.com/video/av5844110/)

## 双缓冲
引擎的刷新率、fps等，这是很重要的！想必你也看到了，像上期博客讲的刷新方法是绝对不行的，那个闪屏太影响用户体验了，根本不能拿来用。所以本期我们就来解决这个问题。

本期不可避免会涉及许多代码，很抱歉这部分代码只有Kotlin版的，不过Java程序员也可以看，因为我使用的是几乎都是javax.swing和java.awt包下的东西。至于在别的平台工作的程序员们就只有自己去寻找符合描述的类库啦，或者自己造轮子也是可以的嘛。

## 闪屏原因
之所以之前的方法会闪屏是因为每次刷新时，JPanel（我采用的是一个Frame里面放一个JPanel的方法显示图像）会首先清空整个区域：

```java
g.clearRect(getWidth(), getHeight);
```

然后再挨个绘制要显示的图像。闪屏的出现就在这里，之所以会闪屏就是因为在清空区域之后、重新绘制之前，这块本来应该有图像的地方是还没来得及绘制的。所以你就看到了闪屏。

根据这个理论，我们就要使用一种叫双缓冲的技术。

## 双缓冲思想
顾名思义，首先你需要一个可以快速读写的缓冲区，在这个缓冲区放一个图像类。这个图像是一个二维矩阵，你可以很简单地操作它。通过Graphics类我们可以在这个图像里面画图片、几何图形、文字等。

然后刷新的时候，将这个图像作为一个单独的图像显示到屏幕上。

这样做的好处在于整个绘制过程都在内存中进行，而每次投影到屏幕上的都是绘制好了的图像，将原本出现闪屏的过程全部放到内存中。它没有本质地解决重绘的问题，它相当于是将所有闪屏的部分对用户**隐藏**起来了。并且这么做是完美的，因为它不是简单的**隐藏**，它是完美的回避。用户根本不可能看到闪屏！

## 双缓冲实现
首先实现一个BufferedImage，通过ImageIO.read(file: File)!! 获取。然后不停刷新这个BufferedImage，再在一个JPanel里面刷新那个Graphics。大概就是如下的过程：

```swift
while (true) if (!paused && !stopped) {
	try {
		onRefresh()
	} catch (ignored: Exception) { }
	timeListeners.forEach { it.check() }
	panel.repaint()
	Thread.sleep((1000.0 / refreshPerSecond).toLong())
}
```

这里解释一下refreshPerSecond这个变量，这个变量默认初始值是50，它的含义是每秒刷新次数。可以看到，隔这么长时间就刷新一次。非常清晰。

然后panel.repaint方法被重载，paint方法负责先绘制所有游戏对象到BufferedImage上，然后再将BufferedImage绘制到JPanel里。

```swift
inner class GamePanel : JPanel() {
override fun update(g: Graphics?) = paint(g)
override fun paint(g: Graphics) {
	TODO("draw BufferedImage buffer")
	g.drawImage(buffer, 0, 0, this)
}
```

非常简单，不是吗？

现在你的引擎是不是已经如丝般顺滑了？