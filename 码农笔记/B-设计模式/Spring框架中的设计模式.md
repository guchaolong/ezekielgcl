---
layout: post
title: Spring框架中的设计模式
subtitle: 
author: ezekielgcl
date: 2023-08-23
aliases: 
tags: 设计模式 
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: 2023-08-23
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[code6.jpeg]]"
banner_y: 0.40239
banner_icon: 📚
---

# spring框架中使用了哪些设计模式及应用场景


1.工厂模式:
在各种`BeanFactory`以及`ApplicationContext`创建中都用到了

2.模版模式：
在各种`BeanFactory`以及`ApplicationContex`实现中也都用到了

3.代理模式:
Spring AOP 利用了 AspectJ AOP实现的 AspectJ AOP 的底层用了动态代理

4.策略模式:
加载资源文件的方式,使用了不同的方法,比如:`ClassPathResourece`,
`FileSystemResource`, `ServletContextResource`, `UrlResource`但他们都有共同的接口`Resource`;在Aop的实现中,采用了两种不同的方式,JDK动态代理和CGLIB代理

5.单例模式:
比如在创建bean的时候

6.观察者模式:
spring中的`ApplicationEvent`、`ApplicationListener`、`ApplicationEventPublisher`

7.适配器模式:
`MethodBeforeAdviceAdapter`，`ThrowsAdviceAdapter`，`AfterReturningAdapter`

8.装饰者模式:
源码中类型带`Wrapper`或者 `Decorator`的都是



