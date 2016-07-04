---
layout: post
title: Decompiled an 616-like Android app(Chinese)
category: Android
tags: Android, java
keywords: java, Android
description: How Decompile Android Applications
---


大家还记得616惨案吗？

一个大学森在某QQ群上下载了一个App，叫“QQ悄悄话查看器”，该大学森也不看看这个apk只有几kB，下载安装的时候也根本不看权限，简直纸张，打开之后发现他的手机音量无法调整，直接变成最大，然后发出了巨大的~~啊嗷嗷啊啊啊~~的声音，老师和同学都听见了，场面非常尴尬。。。

这让很多WP用户和iOS用户幸灾乐祸，我只能说，你们还too young，sometimes Naive。连申请的权限都不看，那么小的apk也不逆向试试，自己黄了你倒还怪到Android系统上来了，真是Naive。

然后就有该App被逆向了的消息，我是在知乎上看到的，当时我一看代码，我嘞个去，易安卓！

传说中的易语言，中文编程！

也是可以，我也不知道该App开发者到底是和居心，不过肯定编程水平很糟糕就是了，毕竟易安卓这种东西的尿性大家也都是知道的，作为一个高贵的Kotlin开发者我一直认为非JVM语言写Android总是坑很多，现在看了，的确是的……

不过总觉得自己的母语被这样侮辱，有点不好呢……

但是我当时对此的心态是，对于源代码非常好奇，以及我很想听听那不和谐的声音究竟是怎样的……

不久后，冰封的损友群之一就出现了这样的消息：

<p><img src="/../../../assets/images/andr/decode/1.png" align="center"></p>

这名字，这大小……

一个300kB，一个1.3MB，一看就知道不是什么好东西……

我当时瞬间就想起了616惨案。这回轮到我欺负人家了。作为一个Android开发者，我自然是掌握着逆向工程技能的。

<p><img src="/../../../assets/images/andr/decode/2.png" align="center"></p>

这个人恬不知耻，竟然班门弄斧地发了所谓的截图，看起来好厉害的样子……

不过我非常好奇这玩意代码是什么样的，而且两个apk，大小都不一样，内容应该不一样吧，于是我默默下载之后，打开了apktool……

<p><img src="/../../../assets/images/andr/decode/3.png" align="center"></p>

我马上声明了自己要做的事。

虽然我手机上没有可以用的逆向工具（Show Java和ApkTool都罢工了，不知道为什么）不过反编译apk本身很简单，我用ES解压之后就看到了……

当天晚上，我半夜把解包后的音频文件声音放出来，当时我想的是把声音开到最小应该没问题吧，结果声音本来就巨大，差点吵醒我那学数学竞赛的室友……

<p><img src="/../../../assets/images/andr/decode/4.png" align="center"></p>

我回击了那个发apk的人。

然后后来我实在忍不住，就去反编译了代码。这是解包出来的文件目录。

<p><img src="/../../../assets/images/andr/decode/5.png" align="center"></p>

我简直无力吐槽，连个multi dex都没有，易安卓果然辣鸡，药丸啊！




