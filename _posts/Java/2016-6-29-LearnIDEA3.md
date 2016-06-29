---
layout: post
title: IDEA for beginners 3 Tricks in Code Completing(Chinese)
category: Java
tags: Essay
keywords: Java,IDEA,IntelliJ,IntelliJ IDEA
description: IntelliJ IDEA for beginners chapter 3, some code completing tricks
---

请读者在阅读本篇博客之前学习一下Java语言，因为本篇教程是面向有Java基础的读者的。不过不用担心，你不需要知道太多东西。Java学到OOP那个程度就行了。本文主要内容是一些IDEA中灵活运用代码提示的东西。

## 开始

你可能会问，代码提示还有啥灵活运用的方法？没关系，如果你对于IDEA一无所知的话，本文能让你对IDEA的爱更上一层楼~~

现在打开之前创建的那个空项目。还记得之前的Main.java吗？打开它。代码大概是下面这样的：
<center>
    <p><img src="/../../../assets/images/java/idea3/1.png" align="center"></p>
</center>
没错，只有一个Main类，里面也是空的。上面一坨是注释，不用管。现在我们就要在这里做实验了，准备好你的狗眼，我要开始了。

## 缩写补全

还记得每次运行Java程序都需要输入一遍 
```java
public static void main(String[] args) {
}
```
吗？难道你就不厌烦吗？明明是非常常用的一段代码，这么长一大段每次都要打好久啊！所以IDEA作为最屌的Java IDE为你提供了贴心的缩写补全功能。

试试输入：**psvm**四个字母。然后你会看到这个提示：
<center>
    <p><img src="/../../../assets/images/java/idea3/2.png" align="center"></p>
</center>
敲下你高贵的回车，选择这个宿命中的提示。然后你就直接插入了之前你已经敲烦了的一大段代码——
<center>
    <p><img src="/../../../assets/images/java/idea3/3.png" align="center"></p>
</center>

下面列出一些别的常用的类似的缩写。

缩写|补全内容
:---:|---:
**psvm**|public static void main(String[] args){}
**sout**|System.out.println("");
**souf**|System.out.printf("");
**serr**|System.err.println("");
**psf**|public static final
**psfi**|public static final int
**psfs**|public static final String

赶紧试试吧。

这些功能根据我的朋友的说法，NetBeans也具备，于是我还得拿出更多杀器啊。

## 快速构建

这个功能是为一些手速比较慢的同学提供的。

## 你学到了什么？
