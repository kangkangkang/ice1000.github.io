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

## 故事开始

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

<p><img src="/../../../assets/images/andr/decode/6.png" align="center"></p>

勇敢地逆向。至于我的逆向工具是什么，其实我不是特别想放出来，以后可能会有教程吧。长期关注博客，可能就会看到喔。

<p><img src="/../../../assets/images/andr/decode/7.png" align="center"></p>

## 文件目录说明

- e4a.runtime

估计就是易安卓的类库了，全是乱码的中文，我简直看不下去，不堪入目的代码。

- p

源代码。我对这个开发者有点无语，包名很奇怪啊……

下面是p目录下的代码。R文件大家都知道是什么东西，我就不放出来了。

```java
package com.p;

import com.e4a.runtime.Objects;
import com.e4a.runtime.annotations.SimpleDataElement;
import com.e4a.runtime.annotations.SimpleObject;
import com.e4a.runtime.components.impl.android.后台服务Impl;
import com.e4a.runtime.components.后台服务;
import com.e4a.runtime.variants.ByteVariant;
import com.e4a.runtime.variants.IntegerVariant;
import com.e4a.runtime.variants.Variant;
import com.e4a.runtime.系统相关类;
import com.e4a.runtime.转换操作;

@SimpleObject
public class 后台服务操作
  extends 后台服务Impl
{
  @SimpleDataElement
  public static 后台服务 后台服务操作;
  
  public 后台服务操作()
  {
    Objects.initializeProperties(this);
    $define();
  }
  
  public void $define()
  {
    后台服务操作 = (后台服务)this;
    后台服务操作.创建完毕();
  }
  
  public void 服务处理过程(String paramString)
  {
    int i = 0;
    if (paramString.equals("闹钟")) {
      for (;;)
      {
        int j = IntegerVariant.getIntegerVariant(i).add(ByteVariant.getByteVariant((byte)1)).getInteger();
        系统相关类.发送广播("后台服务广播", 1, 转换操作.整数到文本(j));
        i = j;
        if (IntegerVariant.getIntegerVariant(j).cmp(ByteVariant.getByteVariant((byte)1)) == 0) {
          i = 0;
        }
      }
    }
  }
}
```

可以看出，真的是个垃圾开发者。

+ Java的规范是大括号不换行，他换行。**辣鸡**。
+ 字符串硬编码，意义不明。

至于e4a里面的内容，我也简略看了一下，封装得不错，确实是为垃圾开发者提供了便利。不过，一个拿易语言开发Android的人，你又能对他报什么希望呢？

下面是简要截图。

<p><img src="/../../../assets/images/andr/decode/8.png" align="center"></p>

要想看到Material Design，肯定是不可能了。

## 最重要的声明

不开车。
