---
layout: post
title: 如何让孩子爱上Kotlin第四章：基本类型
category: Kotlin
tags: Essay
keywords: Kotlin
description: Learn kotlin 4 Variables
---

好了我们继续学习Kotlin吧。

上一节我们讲了变量与常量（最初发布的时候忘记讲常量了，请没看到的同学回溯一下），这次我们讲讲基本的数据类型。

不知道有没有细心的读者发现我上一节讲常量声明的时候所声明的那个pi，我加了小数点：

```swift
val pi = 3.1415926
```

这个带小数点的数和普通的整数是不一样的。带小数点的数叫浮点数，另外一种叫整数。

不同的数据有不同的类型，数据类型这个概念在各个语言中都是非常重要的。

大体来说，基本数据类型一般有以下几种：

中文名|Kotlin中的符号|Java中的符号
:---|:---:|---:
整数|Int|int
浮点数|Float|float
长整数|Long|long
字符|Char|char
字符串|String|String
布尔|Boolean|boolean

<br/>
大概就是这些了，其中的整数你们已经见过了，是用来表示一个不带小数位的整数的，浮点数就是所谓的小数。比如

```swift
val int = 1415926
val float = 3.1415926
```

所谓布尔，就是你们曾经听说过的true和false，一个布尔的变量只有两种可能的值，就是true和false，分别表示真和假。比如

```swift
val bool1 = true
val bool2 = false
```

字符串就是一串字符，也就是一段文字。前面读者应该已经接触了一些了，比如：

```swift
val string = "this is a String"
val char = 'c'
```

一个字符只能表示一个字符，一个字符串可以表示一堆字符，大概就是这个意思。

其实很多人以为编程是在处理数字运算，其实大多数时间都是在处理字符串哦。

## 瞎折腾一下

你可以试一试下面这段代码：

```swift
println(100 / 30)
```

输出的结果是不是出乎意料？

再试试：

```swift
println(100.0 / 30)
println(100 / 30.0)
```
输出的结果是你想要的吗？

想想为什么，读者可以通过阅读[这篇文章](http://www.educity.cn/it/sun/200912291014511906.htm)来了解原因。文章质量可能不高，我花了40秒随手找的。

## 你学到了什么

+ 数据是分类型的
