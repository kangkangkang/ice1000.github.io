---
layout: post
title: How can I master Kotlin 2 Hello World(Chinese)
category: Kotlin
tags: Kotlin
keywords: Kotlin
description: Learn kotlin 1 Hello World
---

同学们，你们期待已久的Kotlin教程终于出现啦！

本教程不仅面向完全不会编程的新人，也面向有其他语言基础的程序员。不过比起某些教程，本教程可能相对较为简洁。

## 说明

由于辣鸡GitHub Pages不支持Kotlin代码渲染，本文出现的代码全部都是渲染成Swift的——不过貌似完美支持。嘿嘿。语法几乎都一样，除了函数声明关键字——Swift是func，Kotlin是fun。

## 环境搭建

请参考我[另一篇博客](http://ice1000.github.io/2016/6/26/LearnIDEA.html)，下载安装IntelliJ IDEA（我本来打算自己先做一个比较简单的Kotlin IDE，不过后来发现这个轮子好像很难制造。。QAQ）。

然后根据那篇博客的内容，创建一个新工程。只不过这次我们创建的新工程是一个Kotlin工程，所以要在创建工程的时候选择“Kotlin”。

<p><img src="/../../../assets/images/java/kt1/1.png" align="center"></p>
<p><img src="/../../../assets/images/java/kt1/2.png" align="center"></p>

创建好之后你会看到和之前那篇博客中类似的界面，不过IDEA这次没有为你自动创建那些代码。不过没关系，现在我们已经完成了工程的创建。

## 初体验

还记得我们是怎么创建第一个Java class的吗？同理，创建一个Kotlin File！

<p><img src="/../../../assets/images/java/kt1/3.png" align="center"></p>

然后随便起个名字，这里就叫它Main.kt吧。如图所示。

<p><img src="/../../../assets/images/java/kt1/4.png" align="center"></p>

然后我们要在里面写代码了。这里说一下，任何Kotlin程序都是从一个main函数开始的。至于什么是main函数，你不用管。看完下文后你就会知道你该怎么做。至于为什么，要留到后期的学习中。

等等，我们现在是要插入一个main函数，那么此时我们遇到的问题就是，每次都要输入一次main函数，很麻烦。
还记得我在[另一篇博客](http://ice1000.github.io/2016/06/29/LearnIDEA3.html)中讲到的一个IDEA黑科技吗？此时你只需要输入**main**，第一个提示就是插入main函数。

<p><img src="/../../../assets/images/java/kt1/5.png" align="center"></p>

然后冰封就只能帮你到这了。

## 仪式

我们来写下这样一段代码：

```swift
fun main(args: Array<String>) {
    println("Hello World")
}
```

然后点击main函数左边的Kotlin图标，选择 Run ，稍等片刻，然后你就能在下面的控制台内看到一个 Hello World 了。

<p><img src="/../../../assets/images/java/kt1/6.png" align="center"></p>

运行！然后你就看到了运行结果：

<p><img src="/../../../assets/images/java/kt1/7.png" align="center"></p>

赶紧祝贺自己吧，你已经写下了人生第一个程序。在编程界中，学习任何一门语言、任何一门技术，你的第一步必定是“Hello World”。这是编程界亘古不变的传统。你现在已经将这个伟大的入门仪式进行了一遍。

万事开头难，恭喜你，你没有死在环境搭建和工程创建上，你已经成功了一半！

## 再折腾

任何与编程有关的事情都应该经历一个折腾的过程。试试将之前的代码修改一下，修改为

```swift
fun main(args: Array<String>) {
    println("Hello ice1000")
}
```

或者

```swift
fun main(args: Array<String>) {
    println("Hello ice1000")
    println("Hello iXinWei")
}
```

这样你会发现，那句println的作用就是把后面的括号加双引号里面的东西按行输出到下面的控制台中。很好，你已经掌握了函数“println()”的能量。接下来你还需要折腾，继续搞清楚那个双引号的作用。再改改你的代码吧：

```swift
fun main(args: Array<String>) {
    println(233)
    println("233")
}
```

再改改：

```swift
fun main(args: Array<String>) {
    println(233 + 666)
    println("233 + 666")
}
```

你发现了吗？嘻嘻，233+666你应该能看懂是什么意思，没错，这是加法运算。不过当你加了双引号之后，结果就变得不一样了。

我想你已经大概知道了那个双引号的作用。 如果你想深究这玩意，你可以搜索： 字符串 ，看看你的搜索结果吧。

接下来是其他运算，我这里就只给出运算符了。自己挨个试一遍吧，都是程序员的必经之路，不要偷懒。

```
+ 加法
- 减法
/ 除法（你可以试试除以0
* 乘法
% 取余
```

好了，相信你已经掌握了不少知识了。就到这里吧。

事实上，你在学会了运算符的基础之上，你可以把这个当成一个计算器——当然，如果你不嫌麻烦的话。

## 你学会了什么

- 创建、运行Kotlin工程
- Kotlin的Hello World
- 双引号的作用之一
- 五则基本运算