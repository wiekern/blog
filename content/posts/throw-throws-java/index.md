---
title: throw and throws in Java
date: '2016-02-12T10:53:45+01:00'
categories:
- Java编程
tags:
- java
description: 本文主要通过checked Exception探讨两者的区别，因为checked必须处理，否则编译出错。当我们理解了throw,throws对checked
  Exception的作用，unchecked也迎刃而解。
---

本文主要通过checked Exception探讨两者的区别，因为checked必须处理，否则编译出错。当我们理解了throw,throws对checked Exception的作用，unchecked也迎刃而解。

- throws

用来声明可能会抛出的异常，然后将异常处理交由上级处理。这样写代码的时候可以不用try..catch。

```java
//通过throws处理异常
class Person {
	public void eat() throws FileNotFoundException {
		FileInputStream fs = new FileInputStream("fruit.txt");
		//此处可能会出现FileNotFoundException，
		//而FileNotFoundException 属于checked Exception，
		//因此必须处理该异常，你是用throws的方式抛出给上级去处理或者自己try...catch就由你自己权衡。
	}
}

//通过try...catch处理异常
class Person {
	public void eat() {
		try {
			FileInputStream fs = new FileInputStream("fruit.txt");
		} catch (FileNotFoundException e) {
			//可以什么都不做
		}
		//编译不会报错。但是如果谁调用此方法，必须处理该checked Exception（这两种方法任选其一），否则编译报错。
	}
}
```

由此看来，throws是一种用来处理异常的方式，即声明异常交由上级调用者处理，这样在对checked Exception必须做出处理时，免去了try…catch。

- throw

直接抛出一个异常。如果抛出checked Exception，那么必须处理，还是一个道理，上面的方式两选一。

```java
//throw 抛出异常
//如果你这么写，编译报错
class Person {
	public void eat() {
		throw new FileNotFoundException("checked Exception");
		//抛出checked Exception，但是没处理。
	}
} 

//第一种：throws交由上级处理
class Person {
	public void eat() throws FileNotFoundException {
		throw new FileNotFoundException("checked Exception");
	}
}
//为何此处既有throw又有throws呢？throw抛出异常，throws"处理"(交由上级处理)异常，两者分工合作很愉快。

//第二种：try...catch处理
//此处仅供学习，应该没人这么写。
class Person {
	public void eat() {
		try {
			throw new FileNotFoundException("checked Exception");
		} catch (FileNotFoundException e) {
			//do something
		}
	}
}
```

### 为什么throw抛出异常的第二种方式正常不会有人这样写？

**我的思考是：**用try去抛出一个异常然后自己再去catch并处理，这不是多此一举吗！我们用throw抛出一个异常肯定是希望上级去处理，所以应该用第一种。**另外，我们经常用throw去抛出一个unchecked Exception给上级。**

至此，unchecked Exception的处理也是同样的道理，只是编译器不强制你处理，所以编译能通过，但是程序一旦运行（所以它也称Runtime Exception），unchecked Exception没有被处理，程序肯定是要崩溃的。
