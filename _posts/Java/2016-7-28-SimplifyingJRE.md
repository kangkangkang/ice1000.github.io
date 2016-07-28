---
layout: post
title: 难忘的经历：精简JRE
category: Java
tags: Java, JRE
keywords: Java, JRE
description: Simplifying Java Runtime Environment
---


这几天一直在和 [Eldath](https://github.com/lizhaohan001)同学一起肝一个老坑——[Castle-game](https://github.com/ProgramLeague/Castle-game)（下文简称CG），本来是我年轻气盛的时候写的练手项目，结果Eldath同学说很喜欢这样的游戏模式，正好我从来没和除了那谁之外一起写过项目，所以就和Eldath一起继续写起了CG。结果深受之前年轻气盛时不会设计模式所造成的苦。不过还好，起码目前经过我自己的四次超大型重构，现在的代码起码能看。（分别是超大型重构，铠甲型重构，女性重构和野兽型重构 嘿嘿 看不懂的去补进击的巨人

## 为什么要精简JRE

今天想到了一些关于拿给别人玩的问题。既然是Java写的那么少不了安装JRE啊，这不是增加那些没玩过MC想玩CG的人的负担吗，所以我就开始想把JRE一起打包进去。

我翻出了C盘的jre1.8.0_71，打开属性一看，**哇！**（请脑补葛叔脸）

### 整整176MB，我的妈呀，这还不如直接让用户安装JRE

看来精简一下是必须的了。

那么怎么精简呢？

我灵机一动，想到了一个简单直接的方法。我先将jre里面的东西拷贝到了CG的release包里面，并命名为jre。然后我默默打开了可爱的cui.bat，将内容改为：

```bash
@echo off

jre\bin\java -jar cui.jar

pause
```

然后我跟平时调试一样跑起了cui.jar，一个命令行界面的CG。没有任何问题，现在我运行的CG已经是跑在我拷过来的这个JRE上了。

## 接下来是重点

然后打开了复制过来的jre，先打开bin目录，Ctrl+A全选，然后删除。说正在运行、占用了的，全保留。然后对lib目录做了同样的事。

切换到CG终端，试了几个指令，毫无问题，跑得溜得很。我保存退出了，把整个release重新压缩了，结果只有30.5MB，我的内心非常的excited，并兴奋地发到群文件给Eldath看。

然后我又跑了跑CG的GUI，害怕我无意中删除了一些GUI组件导致GUI跑不起来。结果我马上就遇到了Exception，我的内心几乎是崩溃的。然后我又试了试CUI，发现同样出车祸了。我更崩溃了。

我感觉应该是JVM初始化的时候用到的一些文件被我艹了。于是我赶紧删了那个JVM重新拷一份，重新试试。

<br/><br/><br/><br/><br/>

又出车祸。mdzz，我对这个看脸的世界绝望了，果然只有长得帅才能不报错啊。如果不够帅的话，就只有和编译器（此处是虚拟机）坐下来好好谈谈了。

~~嘿嘿，此时我想的是JVM迟早会变成我的RBQ。~~

## 最后的调试

运行！

```bash
D:\git-repos\城堡游戏\out\artifacts\JAR>cui.bat
Error: could not open `D:\git-repos\城堡游戏\out\artifacts\JAR\jre\lib\amd64\jvm.cfg
```

翻回收站！把amd64这个目录拷回去。再跑！

```bash
D:\git-repos\城堡游戏\out\artifacts\JAR>cui.bat
can't open D:\git-repos\城堡游戏\out\artifacts\JAR\jre\lib\tzmappings.
Exception in thread "main" java.lang.Error: java.io.FileNotFoundException: D:\git-repos\城堡游戏\out\artifacts\JAR\jre\lib\tzdb.dat (系统找不到指定的文件。)
        at sun.util.calendar.ZoneInfoFile$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.util.calendar.ZoneInfoFile.<clinit>(Unknown Source)
此处省略50行报错
```

赶紧翻回收站，把tzmappings找回来！
		
```bash
D:\git-repos\城堡游戏\out\artifacts\JAR>cui.bat
Exception in thread "main" java.lang.Error: java.io.FileNotFoundException: D:\git-repos\城堡游戏\out\artifacts\JAR\jre\lib\tzdb.dat (系统找不到指定的文件。)
        at sun.util.calendar.ZoneInfoFile$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.util.calendar.ZoneInfoFile.<clinit>(Unknown Source)
        at sun.util.calendar.ZoneInfo.getTimeZone(Unknown Source)
        at java.util.TimeZone.getTimeZone(Unknown Source)
        at java.util.TimeZone.setDefaultZone(Unknown Source)
        at java.util.TimeZone.getDefaultRef(Unknown Source)
        at java.util.TimeZone.getDefault(Unknown Source)
此处省略50行报错
```

赶紧翻回收站，把tzdb.dat找回来！再跑！

```bash
D:\git-repos\城堡游戏\out\artifacts\JAR>cui.bat
Exception in thread "main" java.lang.InternalError: java.io.FileNotFoundException: D:\git-repos\城堡游戏\out\artifacts\JAR\jre\lib\currency.data (系统找不到指定的文件。)
        at java.util.Currency$1.run(Unknown Source)
        at java.util.Currency$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.util.Currency.<clinit>(Unknown Source)
        at java.text.DecimalFormatSymbols.initialize(Unknown Source)
此处省略77行报错
```

这次是currency.data！

```bash
D:\git-repos\城堡游戏\out\artifacts\JAR>cui.bat
欢迎来到Castle Game！
这是一个超复古的CUI游戏。
最新版本和源代码请见https://github.com/ProgramLeague/Castle-game
Kotlin版本与旧版本请见https://github.com/ice1000/Castle-game
敬请期待OL版本https://github.com/ProgramLeague/Castle-Online
检测到存档。
您好，ice1000
如果您需要任何帮助，请键入 'help' 并回车。

读书的气氛很浓厚。
您的位置：书房
出口有: east north
这里的Boss是优雅的读书人,已经被你打败过啦O(∩_∩)O哈哈~
```


我的内心非常的excited，压缩了之后一看，发现并没有怎么增加体积，变成31mb了，我立刻兴奋地发到群文件给Eldath看。

之后要精简JRE的话也可以这么干啦，~\(≧▽≦)/~真是太好了，又能靠Java把妹了哈哈哈哈——

## 你学到了什么

+ 精简JRE的方法
