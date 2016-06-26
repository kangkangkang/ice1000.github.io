---
layout: post
title: Material Design for JavaFX 1 (Chinese)
category: Java
tags: Essay
keywords: Java,JavaFX,MaterialDesign
description: Use Material Design on desktop
---

我曾经一直思考，如何在JavaFX桌面开发中进行Material Design。作为一个懒惰的程序员，当时我是希望能找到一些既成的轮子来做这些事情。

在经历了接近4个小时的搜寻之后，我终于找到了一个非常优秀的开源项目——JFoenix。

说实话虽然这货既有官网又有文档，我作为一个JavaFX初学者折腾这玩意的时候还是非常辛苦的，文档和Demo说实话真的是一团糟，非常典型的那种开源项目。最终我也搞定了，功夫不负有心人。

于是就在这里写一篇教程，希望大家少走弯路。这是上篇，接下来可能还会有一篇进阶内容。敬请期待冰封放暑假。

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

+ 打开自家神器IntelliJ IDEA(你也可以使用你自己平时用的IDE)，创建一个JavaFX项目。萌萌哒IDEA已经为我们创建好了必须的代码咯。内容应该有：一个Controller.java，一个sample.fxml，一个Main.java。记住这个sample.java，咱们待会还要用。
<center>
    <p><img src="/../../../assets/images/java/javafx1/1.png" align="center"></p>    <p><img src="/../../../assets/images/java/javafx1/2.png" align="center"></p>
</center>
+ 打开JavaFX Gesture Builder，按下快捷键*Ctrl+O*并打开你刚刚在IDEA中创建工程文件的地方，找到src目录，并打开，选择刚刚你已经看到了的、IDEA自动生成的Sample.fxml，并打开它。
<center>
    <p><img src="/../../../assets/images/java/javafx1/3.png" align="center"></p>
</center>
+ 另外看到这个小可爱了吗？点击它，选择弹出的菜单中的 import JAR/FXML file... 这个选项，接下来找到你之前下载的jfeonix.jar，双击打开。由于我无法截得完整的弹出菜单的图片，就只有委屈读者自行解决了。
<center>
    <p><img src="/../../../assets/images/java/javafx1/4.png" align="center"></p>
</center>

## 进行中
+ 从左边的控件列表中选择container中的AnchorPane，拖拽到中间的灰色界面处。你会看到一个白色的大框框出现在中间。 这个白色的大框框就是我们的GUI界面了。它现在还是空的，让我们给它添加一些东西。下面以一个简单的、Material Design的按钮为例子。
<center>
    <p><img src="/../../../assets/images/java/javafx1/5.png" align="center"></p>
</center>
+ 再选择Custom中的JFXButton，拖拽到那个白色大框框里面。你现在可以看到，在这个白色的大框框里面有一个按钮。你现在把按钮拖进去，就相当于在我们的GUI界面里面添加了这个控件。
<center>
    <p><img src="/../../../assets/images/java/javafx1/6.png" align="center"></p>
</center>
是不是一股中国高中教材里的Visual basic的感觉。。

+ *Ctrl+S* 保存。现在我们转移到IDEA。Gesture Builder先别忙关掉，留着我们待会还要用。

## 小成果

还记得IntelliJ IDEA是怎么运行一个项目的吗？

+ 找到之前IDEA自动生成的Main.java，这是一个带有Main方法的类。我们找到这个
类。
<center>
    <p><img src="/../../../assets/images/java/javafx1/2.png" align="center"></p>
</center>
可以看到，
```java
public class Main extends 
```
一行和
```
public static void main(String[] args)
```
一行，两行的最左边(如果有行号的话，应该在行号的左边)有一个绿色的小箭头。

+ 点击这个小箭头，弹出一个菜单。选择Run开头的那个选项。

你就能看到一个窗口了。在这个窗口中间就是你刚刚添加的按钮，那个叫JFXButtom的按钮。点击它，看到熟悉的Android 5.0 的浮动效果了吗？

你成功了。

以此类推，你可以拖拽更多的控件到这个窗口中。

在以后的博客中，冰封会讲到更多关于设置属性、父子控件、、业务逻辑绑定、CSS等~~本来该在这篇讲的~~内容。

enjoy!

P.S. 写这段博客的时候在上学的路上，写完发现地铁坐过站了。。我的内心几乎是崩溃的。
