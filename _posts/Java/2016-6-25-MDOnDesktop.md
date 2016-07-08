---
layout: post
title: 在JavaFX中进行Material Design：第一章
category: Java
tags: Java
keywords: Java,JavaFX,MaterialDesign
description: Use Material Design on desktop
---

我曾经一直思考，如何在JavaFX桌面开发中进行Material Design。作为一个懒惰的程序员，当时我是希望能找到一些既成的轮子来做这些事情。在经历了接近4个小时的苦苦搜寻之后，我终于找到了一个非常优秀的开源项目——JFoenix。

简直是，众里寻他千百度，蓦然回首，那开源项目却在，GitHub角落处。

说实话虽然这货既有官网又有文档，我作为一个JavaFX初学者折腾这玩意的时候还是非常辛苦的，文档和Demo说实话真的是一团糟，非常典型的那种开源项目。最终我也搞定了，功夫不负有心人。

于是就在这里写一篇教程，希望大家少走弯路。这是上篇，接下来可能还会有一篇进阶内容。敬请期待冰封放暑假。

现在就让我们开心地在JavaFX中使用Material Design控件吧！

## 依赖

+ **[JFoenix](https://github.com/jfoenixadmin/JFoenix)**
+ **[JavaFX Scene Builder2.0](http://www.oracle.com/technetwork/java/javafxscenebuilder-1x-archive-2199384.html)**
+ IntelliJ IDEA the Java IDE
+ JDK

考虑到部分同学不知道啥是GitHub，我就把JFoenix的链接贴出来了。剩下几个就自己找咯～

## 准备

1. 首先，安装JDK、JavaFX Scene Builder,两者均可在Oracle官网找到下载链接。
1. 如果你还没有非常熟悉的Java IDE，那么请下载安装IntelliJ IDEA，这个过程我已经在另一篇博客中说明。
1. 下载JFoenix的jar包。

出于一位朋友的反馈，再加上我自己之前的失误，我又去Oracle那纯HTML般的官网逛了一圈，把JavaFX Scene Builder2.0的下载链接找了过来。

下载提示：打开上文中JFeonix的链接，并找到这里。

<center>
    <p><img src="/../../../assets/images/java/javafx1/0.png" align="center"></p>
</center>

## 开始

+ 打开自家神器IntelliJ IDEA(你也可以使用你自己平时用的IDE)，创建一个JavaFX项目。萌萌哒IDEA已经为我们创建好了必须的代码咯。内容应该有：一个Controller.java，一个sample.fxml，一个Main.java。记住这个sample.java，咱们待会还要用。
<center>
    <p><img src="/../../../assets/images/java/javafx1/1.png" align="center"></p>    <p><img src="/../../../assets/images/java/javafx1/2.png" align="center"></p>
</center>
+ 打开JavaFX Scene Builder，按下快捷键**Ctrl+O**并打开你刚刚在IDEA中创建工程文件的地方，找到src目录，并打开，选择刚刚你已经看到了的、IDEA自动生成的Sample.fxml，并打开它。
<center>
    <p><img src="/../../../assets/images/java/javafx1/3.png" align="center"></p>
</center>
+ 另外看到这个小可爱了吗？点击它，选择弹出的菜单中的 import JAR/FXML file... 这个选项，接下来找到你之前下载的jfeonix.jar，双击打开。由于我无法截得完整的弹出菜单的图片，就只有委屈读者自行解决了。
<center>
    <p><img src="/../../../assets/images/java/javafx1/4.png" align="center"></p>
</center>
+ 这里提一句，有可能IDEA会在为你自动创建项目时在这个fxml里面加入一些控件，于是我们这种初学者当然是要把它们删掉的了，比如冰封在创建项目的时候，就看到了这个叫做GridPane的东西。处理办法：点击这个东西，然后按键盘上的Delete键。然后它就没有了。
<center>
    <p><img src="/../../../assets/images/java/javafx1/7.png" align="center"></p>
</center>

## 进行中
+ 从左边的控件列表中选择container中的AnchorPane，拖拽到中间的灰色界面处。你会看到一个白色的大框框出现在中间。 这个白色的大框框就是我们的GUI界面了。它现在还是空的，让我们给它添加一些东西。下面以一个简单的、Material Design的按钮为例子。
<center>
    <p><img src="/../../../assets/images/java/javafx1/5.png" align="center"></p>
</center>
+ 再选择Custom中的JFXButton，拖拽到那个白色大框框里面。你现在可以看到，在这个白色的大框框里面有一个按钮。你现在把按钮拖进去，就相当于在我们的GUI界面里面添加了这个控件。这里要注意一个问题，一定要把这个按钮拖得靠近左上角一点，先别管为啥，你就只管拖就行。
<center>
    <p><img src="/../../../assets/images/java/javafx1/6.png" align="center"></p>
</center>
是不是一股中国高中教材里的Visual basic的感觉。没错，这个非常类似VB，不过基于Java让它拥有更大的能量。

+ **Ctrl+S** 保存。现在我们转移到IntelliJ IDEA。Scene Builder先别忙关掉，留着我们待会还要用。

## 小成果

+ **Ctrl+Shift+Alt+S**，打开项目设置(Project Structure)，选择这个绿色的”+“符号。
<center>
    <p><img src="/../../../assets/images/java/javafx1/10.png" align="center"></p>
</center>
然后弹出一个窗口，让你选择添加的文件的路径。还记得刚才把jfoenix.jar放在哪了吗？找到它，然后一路OK下去。冰封的路径和你们的不一样，请根据自己的情况进行选择！
<center>
    <p><img src="/../../../assets/images/java/javafx1/11.png" align="center"></p>
</center>
添加完成了吗？那么下一步。

+ 找到之前IDEA自动生成的Main.java，这是一个带有Main方法的类。我们找到这个类。
<center>
    <p><img src="/../../../assets/images/java/javafx1/8.png" align="center"></p>
</center>
可以看到，Main.java在文件树中的图标有一点点不同——它是一个蓝色的”C“，旁边还有一个绿色三角形。这表明这个类是可以直接运行的。

+ 把你的视线移到右上角，看到那个绿色的小箭头了吗？点击这个小箭头。这个小箭头是”运行“的意思。
<center>
    <p><img src="/../../../assets/images/java/javafx1/9.png" align="center"></p>
</center>

这时IDEA会开始进入一个加载的过程，这个过程实际上就是编译整个工程。等它编译完毕，你就能看到一个弹出的窗口了。这个窗口就是你刚才在Gesture Builder里面弄出来的窗口。
可是这时候你会产生疑问了，我刚刚拖的按钮呢！？

别急，我已经料到了。（不要打我）这时重新打开你的Gesture Builder。

+ 按照下图中”step 1“ -> ”step 2“ -> ”step 3“的顺序依次点击，也就是分别点击那个JFXButton、右上角的Properties、以及点击Properties之后出现的菜单中的”Text“选项、随便输入一段文字，如果你同意图中的话的话，就和我写一样的文字吧。输入完了之后回车一下。
<center>
    <p><img src="/../../../assets/images/java/javafx1/12.png" align="center"></p>
</center>

+ 按照上面的步骤重新运行。

在这个窗口中间就是你刚刚添加的按钮，那个叫JFXButtom的按钮。点击它，看到熟悉的Android 5.0 的浮动效果了吗？
<center>
    <p><img src="/../../../assets/images/java/javafx1/13.png" align="center"></p>
</center>

（话说这个截图截得好辛苦，每次都错过）

你成功了。

以此类推，你可以拖拽更多的控件到这个窗口中，然后再运行试试到底发生了什么。

## 再折腾

+ 接下来我们修改一下代码中的这一部分。这是原来的样子，我们修改一下这几个值：
<center>
    <p><img src="/../../../assets/images/java/javafx1/14.png" align="center"></p>
</center>
比如我，我把它们改成了这样：
<center>
    <p><img src="/../../../assets/images/java/javafx1/15.png" align="center"></p>
</center>
再运行试试？

+ 多改几次，你发现规律了吗？（注意看窗口标题栏和窗口大小）这个非常重要。你以后就知道，这几行代码是什么意思了。
<center>
    <p><img src="/../../../assets/images/java/javafx1/16.png" align="center"></p>
</center>
这是冰封的结果，可以看到，窗口变大了好多，变成了代码里设置的600 x 800，标题栏也变成了。。。。呃，文字好羞耻。。

在以后的博客中，冰封会讲到更多关于设置属性、父子控件、、业务逻辑绑定、CSS等~~本来该在这篇讲的~~内容。

enjoy!

## 你学到了什么
1. jfoenix的使用与下载
1. JavaFX Scene Builder的安装与使用
1. 如何进行JavaFX项目构建
1. 如何运行一个IDEA项目
1. Main.java中部分参数的含义

P.S. 写这段博客的时候在上学的路上，写完发现地铁坐过站了。。我的内心几乎是崩溃的。
