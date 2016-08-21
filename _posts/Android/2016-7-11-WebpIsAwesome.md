---
layout: post
title: 谷歌黑科技：为什么这么小啊
category: Android
tags: Android, png, image, webp
keywords: Android, image, png, webp
description: Why is this so f#cking small ?!
---

我今天算是被震撼了，本来OI考试我[第一题超级水题输出忘了换行，导致全爆](https://github.com/ice1000/OI-codes/blob/master/else/2016-7-11-game.cpp)，非常尴尬的心情完全因为认识了下面这个东西而消失不见啦。

这是谷歌出品的一个黑科技，主要作用是图片压缩，目前在apk瘦身中广为运用。

它的名字叫，**Webp**。

## 依赖

+ Webp 命令行工具

别害怕，看完博客让你摆脱对命令行的恐惧（当然，如果你本来就喜欢命令行的话更好 ^_^

## 安装与部署

+ 打开[官网](https://developers.google.com/speed/webp/)自己找链接（需要科学上网）
+ 下载之后将解压后的bin目录添加到环境变量。如果你不知道我在说什么，你可以继续看下去没关系，教程中的操作是不需要配置环境变量的（除了最后的实验我自己要用），不过还是推荐读者事先了解如何配置环境变量，操作和配置git的方法相同，你可以按照配置git的方法来做。
+ 复制一张png图片到bin目录下
+ 打开终端，进入到bin目录

现在你应该是这个状态。

<p><img src="/../../../assets/images/andr/webp/2.png" align="center"></p>

另外，我把我的桌面用于演示了。这是我的桌面图片原图，大小你可以在上面的截图看到，1.3MB，比较可怕。

<p><img src="/../../../assets/images/andr/webp/1.png" align="center"></p>

现在我们要压缩它。

打开终端的话，win10用户可以这样打开。别的你只能自助了。

<p><img src="/../../../assets/images/andr/webp/3.png" align="center"></p>

## 使用

执行以下命令：

```bash
cwebp -q 100 [你的图片文件名] -o [你的图片文件名，扩展名改为webp]
```

如果你不知道我在方括号里面写的是啥，可以把图片命名为 test.png ，然后试试和我一样的命令：

```bash
cwebp -q 100 test.png -o test.webp
```

然后看着奇迹发生吧，这是命令行的截图：

<p><img src="/../../../assets/images/andr/webp/4.png" align="center"></p>

再看看生成的图片的大小：

<p><img src="/../../../assets/images/andr/webp/5.png" align="center"></p>

我非常一颗赛艇。这个图片格式是可以用于Android的，直接拖进去当成一个png用就行了。当然，chrome也支持打开。

## 更好地使用

改变压缩率：

```bash
cwebp -q [质量] [source.png] -o [target.webp]
```

将webp转化为png：

```bash
dwebp [source.webp] -o [target.png]
```

后来我发现，Google Play上的所有App相关的图片全部是webp格式的，我右键保存了几张图片，下载的时候就全是webp。。不知道那些没听说过这个格式的人会不会以为人家是在加密啊。。

然后我就拿 dwebp把图片给弄回去了。（幸好有了命令行工具啊，不然也只能看着一张张只有Chrome才能打开的图片发呆了（不过截图倒是一个solution，嘿嘿））

## 你学到了什么

+ apk瘦身技巧
+ webp命令行工具的安装与使用