---
layout: post
title: 比较新鲜的Android开发常识
category: Android
tags: Java,Android
keywords: Java,MaterialDesign,Android
description: Something you don't know from old tutorials
---

今天一个群里的朋友说要去面试了，想准备一个App来展示，作为一个比较关心世俗的~~超级菜鸡~~普通人，我觉得我还是应该给他一些建议以表示我的关心的。

对方似乎是培训班出身的移动开发程序员，培训班出身的程序员最大的缺点就是只会写培训班教的东西。我曾经在知乎上看到一个回答，答主说他一个朋友去面试。

> 面试官问他研究过音视频编解码没有，他说没有。面试官又问他，如何启动一个未安装的apk，他说也不知道。这就不是面试官严不严格的问题了，这是个人的能力问题和常识问题。

我两个都研究过，但是音视频编解码我只知道概念，不会写代码，但是基于ClassLoader的插件化编程我是进行过深入研究的。

说明我去面试就不会挂，哈哈～

言归正传，我当时给他的建议是，使用新技术。他让我举个例子，我当然是告诉他我的最爱——Kotlin+anko，这一对前几天才把我坑惨了的家伙。

不过这个建议显然有些不现实，因为他说他马上就要去面试了，这几天抓紧时间学点东西可能学不了那么多。我当时觉得也是，毕竟我入门Kotlin也是花了半个星期左右的，不能强求人家。于是我就开始思考，给他一些更有实际意义的建议。

我当时想的是，那就祭出几个Support包里的东西吧。其实我当时内心还想过AA或者ButterKnife的注解反射简化代码，OKHttp等框架，不过这些的学习周期貌似挺长，从头开始做一个App也不大现实（其实OKHttp很简单的，是我太笨）。

> 那就RecyclerView、NavigationView、DrawerView、CoordinatorLayout、TextInputLayout、CollapsingToolbarLayout、CardView， 这些用上。

他居然说一个没听说过。。。

我当时的内心几乎是崩溃的，又是一个从来没打开过SDK Manager的人……要不然也不会不更新Support包了。

所以我又一次决定来扫盲～

## 常见MD控件

- Toolbar

更加自由的Actionbar

- NavigationView + DrawerLayout

侧滑菜单，需要Toolbar，我用得最多的两个控件之一。

- RecyclerView

高度解藕的ListView，能实现瀑布流、表格、列表等效果。 我用得最多的两个控件之一。

- TextInputLayout

内嵌一个EditText，会有意想不到的效果。

- CardView

卡片布局，一个ViewGroup，类似FrameLayout。

- CollapsingToolbarLayout

下拉缩小显示的Toolbar父布局。

目前我记得的就这些了，咳咳。

另外还有一些常用框架，这些你不知道也该作个了解：

## 常用框架

- Gradle

构建工具，大家都在用。

- AndroidAnnotations

即前文提到的AA。

一个基于注解的框架，帮你简化代码，77.经常使用。

- ButterKnife

另一个注解框架。

- OkHttp

简化网络流操作的框架，我笨看不懂说明文档。。。

- JustWeEngine

更多的应该是引擎，一个面向Android原生的游戏引擎。我用它实现了个打飞机游戏，只用了300多行代码。

引擎作者是我的一个朋友，他是一个很奇特的人。

- anko

如果说上面的几个框架是华雄、李傕、郭汜之流，那么anko就应该是赵云吕布了。

多的不说，anko其实你们也不陌生，就是我昨天遇到bug那个，编译器内部报错多半都是anko的原因。

但是如果你因此放弃anko的话，你可以说，Android这个行业，你白入了。

多的不说，以后可能有教程。

## 软件

- Android Studio

不知道的同学，你不用继续关注我了。我不稀罕你的关注。

今天就到这里吧，刚刚和室友打了一晚上东方萃梦想。。。
