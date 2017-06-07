---
title: "Java编程思想"
layout: page
date: 2099-06-02 00:00
---
[TOC]

# 一切都是对象 #
##存储在什么地方##

* 寄存器

	最快的存储区，不能控制

* 堆栈

	速度仅次于寄存器，通过堆栈指针获得支持，向下分配内存，向上释放内存。需要知道确切的生命周期，因此灵活性差。

* 堆

	存放所有的Java对象。不需要知道数据的存活时间，因此较为灵活，但是分配和清理内容耗时多。

* 常量存储

	存放在代码内部。

* 非RAM存储

	后续再了解~ 目前没看懂。

#初始化与清理#

##构造器内调用构造器##

* 构造器调用必须在构造器的起始处

* 构造器内只能调用一个构造器

##初始化变量##

* 类成员变量会被初始化

		int i;
		char s;
		float f;

* 方法的成员变量需要强制初始化，若如上则会报错

##初始化顺序##

类初始化：

1. 父类--静态变量

2. 父类--静态初始化块

3. 子类--静态变量

4. 子类--静态初始化块

5. 父类--变量

6. 父类--初始化块

7. 父类--构造器

8. 子类--变量

9. 子类--初始化块

10. 子类--构造器

#用法总结#

##finally##
		try{
			调用某些方法
			}finally{
				do something...
			}

##final##

* final 变量

final变量就是常量，是不可以改变其值的，例如：

		public final int VAL=1

* final 对象

final对象表示final所指向的地址不会变，d永远指向sample，但是sample的值是可以改变的，例如：

		public final Sample d=sample

* 空白final

可以创建一个空白的final，例如：public final int a，但是必须在域的定义处或者构造器内初始化；

* final 参数

表示在方法内不允许改变m的指向

		public String method（final Memo m）{
			m=new Memo（）//不允许这么写！
		}

* final 方法

final方法表示在继承中此方法不允许被覆盖

* final 类

final表示此类不允许被继承

##abstract抽象##

* 含有抽象方法的类必须定义为抽象类

* 抽象方法也可以包含非抽象类

* 抽象方法只有定义没有实现，抽象方法在继承类中实现

		abstract class Instrument（）{
			abstract int f();
		int f(int i){...}
		}

##interface接口##

*	接口中只有方法的定义，没有任何实现

* 实现关键字implements，一个类可以实现多个接口

		interface Instrument(){
			int f();
		}

		interface Instrument2(){
			int f2();
		}

		class ins implements Instrument,Instrument2{
			int f(){...}
			int f2(){....}
		}

#java的正则表达式#
#类型信息#
