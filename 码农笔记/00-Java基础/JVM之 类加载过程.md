---
layout: post
title: JVM之 类加载过程
subtitle: 
author: ezekielgcl
date: 2023-08-16
aliases: 
tags: 
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: 2023-08-16
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[code6.jpeg]]"
banner_y: 0.40239
banner_icon: 📚
---


类加载

首先，简单说一下类的加载这样一个机制，就是我们自己写的 java 文件，到最终运行，它必须要经过<mark style="background: #FF5582A6;">编译</mark>和类<mark style="background: #D2B3FFA6;">加载</mark>这两个阶段，编译就是把 java 文件编译成.class文件，而加载是把.class文件加载到 JVM 内存里面，装载完以后会得到一个 Class 对象，我们就可以通过 new 关键字来实例化这个对象


![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230816042103.png)


而类的加载过程需要涉及到类加载器，JVM 在运行的时候会产生三个类加载器，这三个类加载器组成了一个层级关系，每一个类加载器分别去加载不同作用范围的 jar 包，比如 BootStrap ClassLoader，它主要负责 Java 核心类库的加载，也就是<mark style="background: #FF5582A6;">%{JDK_HOME}\lib</mark>下面的rt.jar和 resources.jar等等，Extension ClassLoader 主要是负责<mark style="background: #FF5582A6;">%{JDK_HOME}\lib\ext</mark> 下的 jar 包和 class 文件，Application ClassLoader 只要是负责当前应用里面classpath 下面的所有 jar 包和 class 文件，此外，还可以通过自定义的 ClassLoader 来满足一些特殊的场景需求

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230816042431.png)

而所谓的双亲委派模型呢，就是按照类加载器的层级关系，逐层进行委派，比如我们需要加载一个 class 文件的时候，首先会委派给父加载器去执行，如果父加载器无法加载，那么再尝试自己来加载这样一个 class 。


![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230816043333.png)

这样设计的好处？

有两个，一个是安全性，因为这种层级关系，实际上代表的是一种优先级，也就是说所有的类加载优先要给到 BootStrap ClassLoader ,那么对于核心类库中的一些类呢，就不会被破坏，比如说自己写了一个 java.lang.String ，最终还是会交给启动类加载器，再加上每个类加载器的本身的一个作用范围，那么自己写的 java.lang.String 就没有办法覆盖类库中的类；第二个，就是可以避免重复加载，如果父加载器已经加载过了，那么子加载器就没有必要再去加载了