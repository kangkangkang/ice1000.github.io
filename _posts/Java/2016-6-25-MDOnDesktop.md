---
layout: post
title: Material Design for JavaFX(Chinese)
category: Java
tags: Essay
keywords: Java,JavaFX,MaterialDesign
description: Use Material Design on desktop
---

我曾经一直思考，如何在JavaFX桌面开发中进行Material Design。作为一个懒惰的程序员，当时我是希望能找到一些既成的轮子来做这些事情。

在经历了接近4个小时的搜寻之后，我终于找到了一个非常优秀的开源项目——JFoenix。

说实话虽然这货既有官网又有文档，我作为一个JavaFX初学者折腾这玩意的时候还是非常辛苦的，文档和Demo说实话真的是一团糟，非常典型的那种开源项目。最终我也搞定了，功夫不负有心人。

于是就在这里写一篇教程，希望大家少走弯路。

现在就让我们开心地在JavaFX中使用Material Design控件吧！

## 依赖

+ [JFoenix](https://github.com/jfoenixadmin/JFoenix)
+ JavaFX Gesture Builder
+ IntelliJ IDEA the Java IDE
+ JDK

考虑到部分同学不知道啥是GitHub，我就把JFoenix的链接贴出来了。剩下几个就自己找咯～

## 准备

1. 首先，安装JDK、JavaFX Gesture Builder,两者均可在Oracle官网找到下载链接。
1. 如果你还没有非常熟悉的Java IDE，那么请下载安装IntelliJ IDEA，这个过程我已经在另一篇博客中说明。
1. 下载JFoenix的jar包。

下载提示：打开上文中JFeonix的链接，并找到这里。

<center>
    <p><img src="/../../../assets/images/java/javafx1/0.png" align="center"></p>
</center>

## 开始

+ 打开自家神器IntelliJ IDEA(你也可以使用你自己平时用的IDE)，创建一个JavaFX项目。萌萌哒IDEA已经为我们创建好了必须的代码咯。
<center>
    <p><img src="/../../../assets/images/java/javafx1/1.png" align="center"></p>
</center>
+ 打开JavaFX Gesture Builder，按下快捷键*Ctrl+O*并打开你创建工程文件的地方选择Sample.fxml，并打开它。
<center>
    <p><img src="/../../../assets/images/java/javafx1/3.png" align="center"></p>
</center>
+ 另外看到这个小可爱了吗？点击它，选择 import JAR/FXML file... 这个选项，接下来找到你之前下载的jfeonix.jar，双击打开。
<center>
    <p><img src="/../../../assets/images/java/javafx1/4.png" align="center"></p>
</center>

## 进行中
+ 从左边的控件列表中选择container中的AnchorPane，拖拽到中间的灰色界面处。你会看到一个白色的大框框出现在中间。
<center>
    <p><img src="/../../../assets/images/java/javafx1/5.png" align="center"></p>
</center>
+ 再选择Custom中的JFXButton

