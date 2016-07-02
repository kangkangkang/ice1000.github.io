---
layout: post
title: Use Java to play mp3 and wav(Chinese)
category: Java
tags: Java, JavaSound
keywords: Java, JavaSound
description: How to use JavaSound to play mp3
---

> JavaSound is so f#cking terrible！！

这是我在完成了[Dekoder](https://github.com/ice1000/Dekoder)第五个版本——v1.3之后唯一想说的话。

因为JavaSound真的是太猥琐了……我都不知道该怎么形容。而那个JMF，Java Media Framework，竟然是使用的JNI和C++完成的解码。这还能再猥琐一点吗？

> 简直是狗日的JavaSound！！

#### 推荐大家先去看看[Dekoder](https://github.com/ice1000/Dekoder)，了解一下冰封的音乐播放器作品。

为了让大家少走弯路，冰封在这里特地写出一份教程，告诉大家如何使用Java进行音频的播放。

## 播放wav

wav的播放倒是非常简单，网上随便搜索就会出来。这里提供一些我随手找的链接，多找几个以防他们挂掉（真的是随手找的，就是我自己bing搜索之后简单筛选了一下的结果）：

- [link1](http://www.anyexample.com/programming/java/java_play_wav_sound_file.xml)
- [link2](http://blog.163.com/penghaimin138@126/blog/static/1336243962009103010149510)
- [link3](http://blog.csdn.net/zi_jun/article/details/7971846)
- [link4](http://tech.163.com/tm/030531/030531_95896.html) 推荐，有JavaSound的SourceDataLine等类之间的关系、音频播放原理的讲解。
- [link5](http://blog.csdn.net/jgd28/article/details/4566672)

其实这个功能Dekoder最早的版本就已经支持了——播放wav，多简单个事。

另外，你的播放代码应该是这样的（我的代码是用Kotlin写的，这里就不贴出来了）：

```java
File audio = new File("你的音频文件路径");
audioInputStream = AudioSystem.getAudioInputStream(audio);
AudioFormat audioFormat = audioInputStream.getFormat();
if (audioFormat.getEncoding() != AudioFormat.Encoding.PCM_SIGNED) {
	audioFormat = new AudioFormat(AudioFormat.Encoding.PCM_SIGNED,
			audioFormat.getSampleRate(), 16,
			audioFormat.getChannels(),
			audioFormat.getChannels() * 2,
			audioFormat.getSampleRate(), false);
	audioInputStream = AudioSystem.getAudioInputStream(audioFormat,
			audioInputStream);
}
DataLine.Info info = new Info(SourceDataLine.class, audioFormat);
sourceDataLine = (SourceDataLine) AudioSystem.getLine(info);
sourceDataLine.open();
sourceDataLine.start();
floatVoiceControl.setValue(-20);
byte[] buf = new byte[0xFF];
int onceReadDataSize = 0;
while ((onceReadDataSize = audioInputStream
		.read(buf, 0, buf.length)) != -1)
	sourceDataLine.write(buf, 0, onceReadDataSize);

sourceDataLine.drain();
sourceDataLine.close();
audioInputStream.close();
```

呃，最后别忘了try catch！

不过当你用这样的代码打开MP3文件的时候，你会看到 

```
javax.sound.sampled.UnsupportedAudioFileException: 
	could not get audio input stream from input file
```

这样的报错。冰封在这个问题上起码纠结了接近一个月，中间还跑去学了Lua和C#，最终才得以解决这个~~本来怎么看都应该是甲骨文的错的~~问题。

## 播放mp3

不得不说，我找到这个项目的时间绝对不比找到JFoenix的时间短。

[这个项目](http://www.javazoom.net/mp3spi/sources.html)简直堪称业界良心，虽然文档还是简陋了点，虽然它还是有bug（总时长获取失败）。

这是一个非常优秀的项目，它不需要JMF，不需要JNI，不需要C++，就完成了Java对于MP3的解码。而且最重要的是，你只需要导入它帮助文档中所说的三个jar包到你的项目内之后，你就能愉快地播放MP3了——就是原来的wav播放代码，不需要修改！

mp3spi目前的最新版本是1.9.5，不要被那些早就deprecated的博客给骗了——当然，要是冰封的博客什么时候也deprecated了，请务必邮件通知我！我一定修改！

然后别动你上面的代码。试试用它打开一个MP3文件。

怎么样？惊喜吧？

打开了，高兴吧？

没错，当时冰封心里也是这样的感受。

其实，我现在心里也是这样的感受。

赶紧吸一口，让我拿自己的播放器听听girigiri爱——

<p><img src="/../../../assets/images/java/javasound/1.png" align="center"></p>

我还能再吸。。。吸。。girigiri爱。。
