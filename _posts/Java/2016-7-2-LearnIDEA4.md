---
layout: post
title: 传教之IntelliJ IDEA第四章：集成版本控制系统
category: Java
tags: Java, IntelliJ IDEA
keywords: Java,IDEA, PhpStorm,WebStorm,PyCharm,Rider,RubyMine,CLion,Android Studio,Git,GitHub
description: IDEA for beginners chapter 4
---

本篇主要讲述IntelliJ IDEA的集成版本控制系统。由于集成版本控制系统是基于JetBrains产品平台本身，因此本文同样适用于JetBrains其它产品，包括但不仅限于PhpStorm,WebStorm,PyCharm,Rider,RubyMine,CLion,Android Studio。

版本控制对于程序员来说是一个非常重要的概念。不了解版本控制的话你就孤陋寡闻了，请先使用搜索引擎，了解一下版本控制这个东西吧。

目前最常用的版本控制工具应该是Git，然后还有SVN、CVS、Mercurial、Perforce、Subversion等，这些比较流行的版本控制系统IntelliJ IDEA都有对应的插件支持。这些插件都可以在IntelliJ IDEA插件搜索器里找到。我个人使用的是IntelliJ IDEA Ultimate（帮人家贡献了一点点中文官网的翻译，人家送了我一年订阅），里面都有内置的这些插件。在安装IntelliJ IDEA时，它会问你要安装哪些版本控制插件。我个人平时使用Git，所以就只勾选了Git和GitHub。

至于为什么要选GitHub，原因你懂的。程序员约架、同性交友、膜蛤圣地。

## 依赖

- Git（本教程中是2.7.0）
- GitHub账号一个
- IntelliJ IDEA

## 基本配置

首先你需要安装Git工具，请前往官网下载。我就不作更多说明了。下载安装之后记住你安装的位置。

然后打开IntelliJ IDEA，并转到Settings界面。如下图所示，确保你已经开启了这两个插件。

<p><img src="/../../../assets/images/java/idea4/1.png" align="center"></p>

请忽略我诡异的线条……之前都是用的QQ截图，今天学校把机房的网断了，我就只有用Windows自带的截图工具，那东西比较猥琐，博客的push和commit都是靠的手机……心疼流量。

**Ctrl+Alt+S**，打开设置。找到这个玩意，你需要它来设置你的Git路径。如图所示。

<p><img src="/../../../assets/images/java/idea4/2.png" align="center"></p>

在图中标出来Test按钮左边的输入框输入你的Git的安装路径。然后点击Test按钮。如果弹出一个成功的对话框，那么恭喜你，你配置成功了。

接下来配置GitHub。

<p><img src="/../../../assets/images/java/idea4/3.png" align="center"></p>

把Login填成你的账号，Password填成你的密码。别的都可以照搬我的设置。

好了，你的集成版本控制系统已经配置好了。

## 开始使用

+ 你可以将你的一个本地项目直接推送到你的GitHub上。在这里可以找到这个选项。然后在弹出的窗口输入仓库名和介绍。

<p><img src="/../../../assets/images/java/idea4/4.png" align="center"></p>

如果你只是想开启版本控制系统而不是上传到GitHub，请选择上面的“Enable Version Control Integration”。

+ 你可以便捷地进行版本控制操作。

快捷键 | 功能
:---|---:
Ctrl+Shift+K| push（推送）
Ctrl+K | commit（提交）
Ctrl+T | pull（拉取）

<br/>
+ 你可以直接从GitHub上的仓库创建一个项目。

<p><img src="/../../../assets/images/java/idea4/5.png" align="center"></p>

## 用户体验

这是我的已经提交了的一段代码：

```swift
                } catch (e: IndexOutOfBoundsException) {
                }
            }
            i++
```

我将它改为：

```swift
                } catch (e: IndexOutOfBoundsException) { }
                Log.i("important", "parse finished")
            }
            i++
```

然后我们以此为例子演示一下IDEA的Git支持。

+ 你的改动会在行号旁边显示出来。有改动的地方，IDEA会为你标出来。这样你能清晰地看到你的改动记录（如果你合理使用Git的话）。

<p><img src="/../../../assets/images/java/idea4/6.png" align="center"></p>

下面的图片中清晰地标明了每个地方的作用。

<p><img src="/../../../assets/images/java/idea4/7.png" align="center"></p>

+ 你可以在上面那个界面中双击你需要查看的文件，此时会弹出更改列表。非常清晰明了的修改说明。

<p><img src="/../../../assets/images/java/idea4/8.png" align="center"></p>

由于我的改动很简单，仅仅是两行代码的删除，看不出什么特别的地方，读者可以试试更奇怪的修改，IDEA绝对会给你一个惊喜。

+ 这是推送的界面。你的未推送的提交全部在这里了。

<p><img src="/../../../assets/images/java/idea4/9.png" align="center"></p>

另外，在这里也能查看更改记录，前文提到的很牛逼的改动说明就大概是这样的：（我当时正在封装一个网络连接信息获取的操作）

<p><img src="/../../../assets/images/java/idea4/10.png" align="center"></p>

+ 右边的文件目录树也会有变化，文件名的颜色会根据在Git中的情况变成相应的颜色：

颜色|对应的状态
:---|---:
白色|已经提交或已经忽略
红色|不受版本控制系统管理的文件（不是报错！不是报错！）
绿色|刚创建还未提交的文件
蓝色|已修改待提交的文件
黄色|我也不知道
黑色|你的IDEA竟然是白色皮肤，异端去死！

<br/>

## 写代码出车祸了怎么办

版本控制有一个优点就是能帮你免除车祸。比如你重构你的主业务逻辑代码，发现写着写着你自己都不知道你在写什么了，完全是看着自己的代码一脸懵逼，此时你就需要使用版本控制来救你：

<p><img src="/../../../assets/images/java/idea4/11.png" align="center"></p>

它能让你回到上次提交的样子。

好啦，终于把坑填完了~~好开心啊~~

赶紧扔掉SourceTree、Tortoise Git，使用IDEA的集成版本控制系统吧！

## 你学到了什么

+ 集成版本控制系统，太多操作了




