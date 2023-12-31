---
layout:     post
title:      Tomcat
subtitle:   知识积累
date:       2020-04-05
author:     guchaolong
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
category: Java
tags:
       - Tomcat
       - 服务器
---

#Tomcat

# Tomcat 基础

# Tomcat 架构

# Jasper

# Tomcat 服务器配置

# Web 应用配置

# Tomcat 管理配置

# JVM 配置

# Tomcat 集群

# Tomcat 安全

# Tomcat 性能调优

## Tomcat 性能测试

对于系统性能，用户最直观的感受就是系统的加载和操作事件，即用户执行某项操作的耗时。从更为专业的角度上讲，性能能测试可以从以下两个指标量化。

1. 响应时间：如上所述，为执行某个操作的耗时。大多数情况下，我们需要对同一个操作测试多次，以获取操作的平均响应时间
2. 吞吐量： 即在给定的时间内，系统支持的事务数量，计算单位为 TPS

通常情况下，我们需要借助于一些自动化工具来进行性能测试，因为手动模拟大量用户的并发访问几乎是不可行的，而且现在市面上也有很多的性能测试工具可以使用，如：ApacheBench、ApacheJMeter、WCAT、WebPolygraph、LoadRunner

### ApacheBench

ApacheBench(ab)是一款ApacheServer基准的测试工具，用户测试Apache Server的服务能力（每秒处理请求数），它不仅可以用户Apache的测试，还可以用于测试Tomcat、Nginx、lighthttp、IIS等服务器

1. 安装

   ```
   yum install httpd-tools
   ```

2. 查看版本号

   ![Image text](https://raw.githubusercontent.com/guchaolong/guchaolong.github.io/master/_posts_img/tomcat/abv.png)

## Tomcat 性能优化

### JVM参数调优

Tomcat是一款Java应用，那么JVM的配置便与其运行性能密切相关，而JVM优化的重点则集中在内存分配和GC策略的调整上，因为内存会直接影响服务的运行效率和吞吐量，JVM垃圾回收机制则会不同程度的导致程序运行中断。可以根据应用程序的特点，选择不同的垃圾回收策略，调整JVM垃圾回收策略，可以极大减少垃圾回收次数，提升垃圾回收效率，改善程序运行性能。

1. JVM内存参数

   | 参数                 | 参数作用                                        | 优化建议                |
   | -------------------- | ----------------------------------------------- | ----------------------- |
   | -server              | 启动Server，以服务端模式运行                    | 服务端模式建议开启      |
   | -Xms                 | 最小堆内存                                      | 建议与-Xmx设置相同      |
   | -Xmx                 | 最大堆内存                                      | 建议设置为可用内存的80% |
   | -XX:MetaspaceSize    | 元空间初始值                                    |                         |
   | -XX:MaxMetaspaceSize | 元空间最大内存                                  | 默认无限                |
   | -XX:MaxNewSize       | 新生代最大内存                                  | 默认16M                 |
   | -XX:NewRatio         | 年轻的可老年代大小比值，取值为整数，默认为2     | 不建议修改              |
   | -XX:SurvivorRatio    | Eden区与Survivor区大小比值，取值为整数，默认为8 | 不建议修改              |

   

# Tomcat 附加功能

























