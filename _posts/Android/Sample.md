---
layout: post  
title: 手机端搭建Java编译运行环境  
category: Android
tags: Essay
keywords: Android,Java,搭建  
description: 手机端搭建Java编译运行环境  
---

　　今天带给大家的是手机端搭建Java编译运行环境（手机党福利）。  

　　众所周知，Java是一种可以撰写跨平台应用软件的面向对象程序设计语言。Java技术具有卓越的通用性、高效性、平台移植性和安全性，广泛应用于PC、数据中心、游戏控制台、科学超级计算机、移动电话和互联网，同时拥有全球最大的开发者专业社群。我国也慢悠悠的跟在了世界的屁股后面，随着学习Java的人越来越多，人口慢慢向低龄化趋势发展了。  

　　越来越多学生开始学Java，但是学生大部分都没有电脑，这就是局限吗？不，我们身边还有Android手机，Android手机日益强大的今天，有人用来玩游戏，有人用来学习；有人被手机支配，有人支配手机。让我们开始用Android手机做些有用的事吧（前面说了那么多废话，终于到正题了．．．）。  

###  前提  ###

* 手机必须ROOT
* 终端模拟器
* [JDK](http://pan.baidu.com/s/1ntjDoVZ "密码:6pnc")  
* [lib](http://pan.baidu.com/s/1dDArXDJ "密码:4yjv")  

##  教程  ##

1. 把JDK和lib下载到SD卡非中文目录。  

2. 打开终端模拟器，输入`su`回车获取权限。  

3. `tar -xzvf /**/jdk1.8.0.tar.gz -C /system/`  
**为JDK的路径、注意大小写；  
如果提示 `tar: can't create directory 'jdk1.8.0_06': Read-only file system`，则输入`mount -o remount rw /system/`挂载系统目录/system为读写  

4. `export PATH=/system/jdk1.8.0_06/bin:$PATH`  
注意大小写  

5. `mkdir /lib`  
如果提示 `mkdir: can't create directory '/lib': Read-only file system`，则输入`mount -o remount rw /`挂载根目录/为读写  

6. `unzip **/lib.zip -d /lib/`  
**为lib路径  

7. `chmod 755 /lib/*`  
这个直接输入*  

8. `javac`  
如果出现大量代码，恭喜你搭建成功。

## 注意 ##

　　终端模拟器重启一次就要重新执行2~4的步骤。手机每次重启，第6步解压出来的文件就会删除，需要重新执行5~7的步骤。这里有个小技巧。  

　　终端模拟器菜单中打开首选项，找到初始命令，填上下面代码（注意换行和大小写）：  

> su  
> export PATH=/system/jdk1.8.0_06/bin:$PATH  
> rm -rf /lib  
> mount -o remount rw /  
> mkdir /lib  
> unzip \*\*/lib.zip -d /lib/  
> chmod 755 /lib/*  

###  PS：Android手机上不支持Java弹窗．．．你懂的  ###