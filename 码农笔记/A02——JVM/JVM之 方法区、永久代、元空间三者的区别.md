---
layout: post
title: JVM之 方法区、永久代、元空间三者的区别
subtitle: 
author: ezekielgcl
date: 2023-08-08
aliases: 
tags: 
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


[【大厂突击】五、一文搞懂JVM之 方法区、永久代、元空间三者的区别🔥 - 掘金](https://juejin.cn/post/7081987703335550989)


方法区：是在JVM规范里被定义的
永久代和元空间：都是Hotspot虚拟机中 对方法区的实现

**`jdk1.7` 版本之前的方法区实现叫永久代（`PermGen space`），`jdk1.8` 之后叫做元空间（`Metaspace`）**



如 `JRockit（Oracle）`、`J9（IBM）` 虚拟机有方法区 ，但是就没有永久代 `PermGen space`所以我们以下讨论的都是基于 `HotSpot` 虚拟机


`JDK1.7`以前的`HotSpot`虚拟机和`jdk8`的虚拟机运行时内存的变化如下图
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808041113.png)



`Metaspace`（元空间）和 `PermGen`（永久代）都是对 `JVM`规范中方法区的一种落地实现




`jdk7`开始已经对<mark style="background: #D2B3FFA6;">字符串常量池</mark>等从永久代移除，所以永久代的移除过程跨越了`jdk7`和`jdk8`两个大版本。是渐进式的移除。

在 Java 7 之前，字符串常量池位于永久代（Permanent Generation）的内存区域中
从 Java 7 开始，为了解决永久代空间不足的问题，将字符串常量池从<mark style="background: #FFB8EBA6;">永久代中移动到堆中</mark>
  


jdk1.7，有永久代，但已经逐步去永久代，**字符串常量池**，**静态变量**移除，保存在堆中。使用 JVM 虚拟机内存,如图:
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808042112.png)

jdk8，取消永久代，使用**元空间**实现方法区（保存类型信息，字段，方法，常量） JVM内存–>本地内存。如图:
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230808042132.png)
