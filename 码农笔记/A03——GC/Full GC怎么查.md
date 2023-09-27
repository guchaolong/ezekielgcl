

# Step1.分析“敌情”

## 1.1 JVM内存分布介绍

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/d87d4a3688f365dbeddefc3465cfe231.png)
### 1.11 理论性的概述 

- 程序计数器：线程私有，存储当前线程所执行的字节码行号指示器。分支、循环、跳转、异常处理、线程恢复等基础功能都需要依赖这个计数器来完成。此模块溢出概率极低，可忽略不计。

- Java虚拟机栈：线程私有。描述的是Java方法执行的内存模型。每个方法调用过程，都会对应一个栈帧在虚拟机中入栈到出栈的过程。局部变量表的大小在编译期确定。当JVM运行每个线程时，会为每个线程分配一个java虚拟机栈。包含执行当前方法的相关调用信息、当前方法的变量信息。如下图，各个local variable。所有的原始类型，对象引用存储在栈中。对于一个对象的成员方法，方法中的成员变量依旧是存储在栈中。Java虚拟机栈会抛出：StackOverflowError和OutOfMemoryError

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/e6de250fb5adab9a5c9260f26c036135.png)

- 本地方法栈：与虚拟机栈的区别是，此为本地方法栈所服务.同样有可能抛出StackOverflowError和OutOfMemoryError。

- Java堆：线程共享区域。存储对象实例以及数组，所有对象的成员变量（原始和包装）也会被存储至此。有可能抛出OutOfMemoryError

- 方法区 ：线程共享区域，用于存储已被虚拟机加载的类信息、常量、静态变量、即时编译后的代码等数据，又称“非堆”或者永久代，在java 8中逐步取消了，转而替换是metaspace(元数据区)。可能抛出OutOfMemoryError

- 直接内存：NIO机制，使用Native函数库直接分配堆外内存，然后使用Java堆中DirectByteBuffer对象作为这块内存的引用操作。避免了Java堆和native堆中来回数据复制，提高性能。一般会随着老年代Full GC，顺便清理掉堆外内存废弃对象，也会因为自己的容量不足，抛出OutOfMemoryError。

## 1.2 JVM常见垃圾回收算法

### 1.21 垃圾收集算法原理介绍

- 标记-清除算法：标记所有需要回收的对象，在标记完后统一回收。缺点：标记清除效率不高。产生碎片较多。
- 复制算法：将内存分成两份，使用其中的一份，把存活的对象复制到另一块去。则一次性清理另一半的内存。（如：Eden空间与survivor空间）
- 标记-整理算法：与标记-清理类似，但后续步骤是将存活对象向一端移动，然后直接清理掉端边界以外的内存。
- 分代收集算法：根据存活周期的不同划分。如新生代、老年代。根据生命周期的不同，而进行选择。

### 1.22 垃圾收集算法分类

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/ceb9f37416d3a2c6c0aa28c9365d3470.png)

其中新生代与老年代连线处为两者可以两两搭配服务JVM垃圾  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/887b027f8641d48942bc84af9914ef22.png)

## 1.4 通用的对象分配策略

新生代GC（Minor GC）:发生在新生代的垃圾收集动作，java对象大多数都朝生夕灭，所以Minor GC非常频繁。  
老年代GC（Major GC／Full GC）：发生在老年代

1. 大多数情况下，对象在新生代Eden区中分配，当Eden不够进行分配时，则进行一次Minor GC.
2. 大对象直接进入老年代
3. 长期存活的对象将进入老年代。可以设置－XX：MaxTenuringThreshold=XX来设置晋升老年代的年龄阈值
4. 动态对象年龄判定：如果在Survivor空间中相同年龄所有对象大小大于Survivor空间的一半，则大于或等于该年龄可以直接进入老年代。
5. 空间分配担保：计算新生代MinorGC后剩下的对象若Survivor无法容纳，是否能通过老年代来担保分配空间，若不能，则可能需要触发一次Full GC.HandlePromotionFailure=false设置是否允许老年代担保。


# Step2.工具选用

了解了基本的JVM概念，下面通过实际的操作，通过工作中的案例来进一步明朗化这些概念。  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/f3dcb572c1351e6c5f3d970da333ba49.png)

JDK的监控和故障处理工具：
## jps
- **jps** **（JVM Process Status Tool ）** ：显示指定系统内所有的虚拟机系统。
-v表示启动时候JVM参数  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/5ffae96326e03dd7d87cf431c65a423e.png)


## jstat
- **Jstat(jvm Statistics Monitoring Tool)** ：用于收集虚拟机各方面的运行数据。
`jstat [option vmid [interval [s|ms] [count]] -gc`监视java堆状况，包括Eden区、两个survivor区、老年代、永久代等的容量、已用空间、GC时间合计等信息。
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/d6b30c79ebf05190d4c599387b3dc597.png)  
-gcutil 监视内容与gc基本相同，但输出的主要是已使用占用的总空间百分比。  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/1bf05b5bf266881fdc31d8a22127d5fb.png)jstat –gccause 查询GC的原因.  
S0、S1表示新生代survivor0、survivor1.E：Eden区 O：老年代 P：永久代（表示permanent）。YGC（Young GC）YGCT(Young GC Time),运行以来共发生300次，总共耗时11.691s .FGC（Full GC）,FGCT(Full GC Time) ，运行起来发生多少次Full GC,消耗时间。GCT：所有GC消耗时间。


## jinfo
- **jinfo:** **虚拟机配置信息**
Jinfo pid  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/2191290cddc24704f40d137cde393966.png)jinfo –flag 可以搜索或者修改一些参数值  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/a1d19c6641f258dd41ef522a38c976ed.png)


## jmap
- **jmap** **（Memory Map for Java）** :生成虚拟机的堆转储快照。-XX:+HeapDumpOnOutOfMemoryError参数，可以让虚拟机在OOM异常之后，自动生成dump文件。
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/1fb590e18eca243e44102919ea76a015.png)  
jmap –heap 显示java堆详细信息，如使用哪些回收器、参数配置、分代状况等。jmap –dump 生成堆内存快照信息jmap –histo:live pid

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/167cecc710f0f3a407cd628be52d55a3.png) 



## jstack
- **jstack:stack trace for java** .显示虚拟机的线程快照。

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/14bdd00d6daf270d37e5bbc55b70ab13.png)

## 图形化界面分析工具

- VisualVM（ [https://visualvm.github.io/](https://visualvm.github.io/) ）JVM文件分析工具，可以实时获取的一些有关本地或远程 JVM 上运行的应用程序的信息
    
- JProfile:性能监测工具： [下载地址](http://www.ej-technologies.com/download/jprofiler/files)
- MAT：堆内存分析工具： [下载地址](http://www.eclipse.org/mat/downloads.php)
    
- 功能模块：Histogram可以列出内存中的对象，对象的个数及大小
    
- Dominator Tree可以列出那个线程，以及线程下面的对象占用的空间。
- Top consumers能通过图形列出最大的object。
- Leak Suspects能自动分析泄漏的原因。
- 内有OQL ，类似SQL的查询。可以进行对象、地址等查询关联。
    
    ```
    使用上文命令，dump个文件分析，让你更能体现与直观认识。
    ```
    

# Step3.如何利用快速分析并解决问题

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/8a8b6966cafe7cc477c1f6aa9d56f2ba.png)  
## 3.1 如何查线程最耗费CPU的线程信息。  
1.ps –ef|grep java 或者 jps 查找出java进程ID。  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/7b9d1db00e4961c4eb110d7abf8fe781.png)2.top –Hp pid 查找最耗CPU 的线程PID![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/31d153931319184fb61b79b2e6014be2.png)3.printf “%x\n” 4867 转换16进制  
4.使用jstack查找出堆栈信息，跟踪代码分析  
![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/24e1ac3c99a14a35259ee5fd1c20fc14.png)可以理解一下，stack打印出来信息。  
[Java线程Dump分析工具--jstack - 残雪余香 - 博客园](https://www.cnblogs.com/nexiyi/p/java_thread_jstack.html)

6.其它方法：arthas

![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/57f74b4ca7c212823f4937702ce18787.png)  
arthas：打印最忙碌的前10个线程及占用CPU情况。

## 3.2 OOM 排查

### 3.21 产生原因。

从1.1内存介绍可以看出，除了程序计数器外，其它内存存储，均可以产生OOM。

1. 大数据量，无可用内存分配
2. 内存泄漏，没及时回收。
3. JVM内存容量参数分配不合适。
4. 代码bug,死循环无限期分配容量。

### 3.22 参数理解

|参数|描述|
|---|---|
|-Xms|初始堆|
|-Xmx|最大堆大小|
|-Xmn|新生代的内空间.空间包含（eden+2个survivor）,默认配比是8:1:1|
|-XX:SurvivorRatio|Eden区与Survivor区的大小比值|
|-XX:PermSize|永久代的分配|
|-XX:MaxPermSize|永久代最大值|
|-Xss:|每个线程堆栈的大小|

### 3.23 排查思路

1.各个内存不够分配，拿到dump文件，分析内存的分配情况。  
报错信息：javaOutOfMemoryError:java heap space……  
1.使用命令jmap![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/5f33aa8b0d2ef0987bfcdb74ec2c0a77.png) 2.使用memory analyzer分析：  
工具MAT作用：Histogram可以列出内存中的对象，对象的个数以及大小。  
Dominator Tree可以列出那个线程，以及线程下面的那些对象占用的空间。  
Top consumers通过图形列出最大的object。  
Leak Suspects通过MA自动分析泄漏的原因。  
MAT使用教程参见：[http://www.cnblogs.com/AloneSword/p/3821569.html](http://www.cnblogs.com/AloneSword/p/3821569.html) [](http://www.cnblogs.com/AloneSword/p/3821569.html)下载地址：[http://www.eclipse.org/mat/downloads.php](http://www.eclipse.org/mat/downloads.php) [](http://www.eclipse.org/mat/downloads.php)可以下载下来，dump个文件，跟着教程试试看。  
或者使用集团：Zprofile文件分析工具  
其他更多outOfmemory 问题，可以参见毕大师总结的，如：堆外溢出，线程栈溢出等：[https://www.atatech.org/articles/15611](https://www.atatech.org/articles/15611)

## 3.3 Minor GC/Full GC

1.使用工具j**stat –gcutil或者查看gc.log日志，查看内存的回收情况。** ![](http://ata2-img.cn-hangzhou.img-pub.aliyun-inc.com/8b0967eb948ddb9fc4844dd36bd09b6a.png)

2.dump内存分析  


3其他参数调优  
若程序代码层面无bug或优化已是瓶颈，或者自适应自身应用的运行特点。可以调节一下JVM 层面的参数。如:根据GC 情况进行调节，如减少minor gc，则可以调大Survivor,或Eden, 调大TenuringThreshold