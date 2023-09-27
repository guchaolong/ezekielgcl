---
layout: post
title: Java内存区域和内存模型（JMM）
subtitle: 
author: ezekielgcl
date: 2023-08-08
aliases: 
tags: JMM
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: 2023-08-08
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[code6.jpeg]]"
banner_y: 0.40239
banner_icon: 📚
---



## 内存区域（运行时）数据区和JMM

要想深入了解Java并发编程，就要先理解好<mark style="background: #FF5582A6;">Java内存模型</mark>


java内存区域（运行时数据区）和java内存模型（JMM）是两个不一样的东西
<mark style="background: #FF5582A6;">内存区域</mark>是指 JVM 运行时将数据<mark style="background: #D2B3FFA6;">分区域存储</mark>，强调对<mark style="background: #FF5582A6;">内存空间的划分</mark>
<mark style="background: #FF5582A6;">内存模型</mark>（Java Memory Model，简称 JMM ）是定义了<mark style="background: #D2B3FFA6;">线程和主内存之间的抽象关系</mark>
[Java内存区域(运行时数据区域) 和 内存模型(JMM) - 知乎](https://zhuanlan.zhihu.com/p/434541309)


<mark style="background: #FFB8EBA6;">jdk1.8之前：</mark>

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808035240.png)


JDK1.8（含）之后：
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808035349.png)

我们可以把它们分为==两个类型的区域==，一种是==线程私有==的，另一种是==线程共享==的


更详细的图:

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808035426.png)
jdk1.7开始，**字符串常量池**，**静态变量**移除出永久代，保存在堆中。



[[JVM之 方法区、永久代、元空间三者的区别]]


Java内存模型(Java Memory Model简称<mark style="background: #FF5582A6;">JMM</mark>)是一种抽象的概念，并不真实存在，它描
述的是一组<mark style="background: #FF5582A6;">规则或规范</mark>，通过这组规范定义了程序中各个变量（包括实例字段，静态字段和构成数组对象的元素）的访问方式
JVM运行程序的实体是线程，而每个线程创建时JVM都会为其创建一个<mark style="background: #FF5582A6;">工作内存</mark>(有些地方称为栈空间)，用于存储线程私有的数据，而Java内存模型中规定<mark style="background: #D2B3FFA6;">所有</mark>变<mark style="background: #FF5582A6;"></mark>量都存储在<mark style="background: #D2B3FFA6;">主内存</mark>，主内存是共享内存区域，所有线程都可以访问，<mark style="background: #D2B3FFA6;">但线程对变量的操作(读取赋值等)必须在工作内存中进行</mark>，首先要将变量从主内存拷贝的自己的工作内存空间，然后对变量进行操作，操作完成后再将变量写回主内存，不能直接操作主内存中的变量，工作内存中存储着主内存中的变量副本拷贝，工作内存是每个线程的私有数据区域，因此不同的线程间无法访问对方的工作内存，线程间的通信(传值)必须通过主内存来完成

JMM与JVM内存区域的划分是不同的概念层次，更恰当说JMM描述的是一组规则，通过
这组规则控制程序中各个变量在共享数据区域和私有数据区域的访问方式，JMM是围绕<mark style="background: #FF5582A6;">原子性，有序性、可见性</mark>展开。JMM与Java内存区域唯一相似点，都存在共享数据区域和私有数据区域，在JMM中<mark style="background: #FF5582A6;">主内存</mark>属于共享数据区域，从某个程度上讲应该包括了<mark style="background: #FF5582A6;">堆和方法区</mark>，而<mark style="background: #D2B3FFA6;">工作内存</mark>数据线程私有数据区域，从某个程度上讲则应该包括<mark style="background: #D2B3FFA6;">程序计数器、虚拟机栈以及本地方法栈</mark>。

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808063516.png)

[[并发编程之JMM&synchronized&volatile详解.pdf]]







