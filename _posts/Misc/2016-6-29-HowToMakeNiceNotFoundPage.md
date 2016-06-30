---
layout: post
title: How to make a cool 404 page (Chinese)
category: Misc
tags: Essay
keywords: 404, java, ruby, c, kotlin
description: How to write a nice 404 page
---

如何写出一份很“程序员”的404.html？

这个问题冰封思索了很久，因为一个程序员的博客应该有一个很有逼格的404页面。想了半天，我也参考了GitHub、JetBrains、StackOverflow等网站的404页面。最后我觉得还是应该写代码。所以我就用自己最熟悉的四门语言分别写了提示内容的一部分。

## 关于每份代码

我要充分发挥这四门语言各自的特性，于是我先列出了它们分别的特性。

+ Ruby：元编程、函数式编程、面向过程、面向对象
+ Java：函数式编程、面向对象
+ Kotlin：函数式编程、面向对象、面向过程
+ C：面向过程

最终决定，四门语言各自体现一种特性——

语言 | 特性
:---:|---:
Ruby|元编程
Java|面向对象编程
Kotlin|函数式编程
C|面向过程编程+系统底层

于是我又好好干了一晚上。。。想了半天，很快写出第一版，又改了几下。特别是C语言那个版本，我在没有 stdio.h 的情况下使用 system 函数强行完成了标准输出，也是很强很强……

试试这个404吧： [http://ice1000.github.io/404](http://ice1000.github.io/404)

## 温馨提示
下面的代码都可以被编译运行哦，你可以复制源代码、使用命令行工具直接编译，程序会在控制台输出相应的内容。

这大概是世界上最程序员的404了吧。。。

```ruby
# This is Ruby
class ErrorReasoner
	def initialize
		@messageTitle = '404 Not Found'
		@messageContent = '你来到这个页面，通常有两个原因'
	end
	self.define_method "_print_reason", do
		print @messageTitle, "\n"
		print @messageContent, "\n"
	end
end

printer = ErrorReasoner.new
printer._print_reason
```

```java
// This is Java
public class ErrorReasoner {
	public ErrorReasoner() {
	}
	public final String messageTitle = "一、链接错误";
	public final String messageContent = 
		"原因：博客搬迁造成的旧链接失效。请回到主页。(*′﹃｀*)";
	public void printMessage(String msg) {
		System.out.println(msg);
	}
	public static void main(String[] args) {
		ErrorReasoner reasoner = new ErrorReasoner();
		reasoner.printMessage(messageTitle);
		reasoner.printMessage(messageContent);
	}
}
```

```swift
// This is Kotlin
class ErrorReasoner(private var printer: (message: String) -> Unit) {
	fun printMessage(message: String): Unit
		= printer(message)
}
fun main(args: Array<String>) {
	var reasoner = ErrorReasoner { println(it) }
	reasoner.printMessage("二、实验事故")
	reasoner.printMessage(
		"原因：冰封所建立的时间之域被隔壁实验室里的对撞机事故影响，" + 
		"造成部分页面损伤。"
	)
}
```

```c
// This is C ( pure C )
#include <stdlib.h>
#include <string.h>
const char* echo = "echo ";
void printMessage(char* message) {
	char* command = (char*) malloc (strlen(message) + strlen(echo) );
	strcpy(command, echo);
	strcpy(command + strlen(echo), message);
	system(command);
}
int main(int argc, char* argv[]) {
	printMessage("三、末日降临");
	printMessage(
		"原因：在归零者文明的号召下，" + 
		"冰封已将建立好的独立时间之域回归主宇宙。别担心，数据已经备份。"
	);
	return 0;
}
```

