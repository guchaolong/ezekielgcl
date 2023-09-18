#SpringBoot 

# 一、Runer方式
1. **ApplicationRunner**
2. **_CommandLineRunner_**

_
在日常的项目开发中经常会遇到这样的需求：**项目启动**的时候进行一些一次性的**初始化工作**，如**读取加载资源文件**、**读取配置文件**，**数据库连接**、**执行其它外部程序**等。这个时候我们就可以用到spring-boot为我们提供的一种扩展机制--**Runner**。在spring-boot中提供了两种Runner接口：**ApplicationRunner**和**CommandLineRunner**

他们的执行时机为容器启动完成的时候。这两个接口中有一个run方法，我们只需要实现这个方法即可。
这两个接口的不同之处在于：ApplicationRunner中run方法的参数为ApplicationArguments，而CommandLineRunner接口中run方法的参数为String数组

原理：
启动的run方法中会去调用**SpringApplication callRunners（）**方法查找实现了ApplicationRunner和CommandLineRunner接口的Bean，统一存放在一个list中，根据Bean的order进行排序，循环调用每一个Runner Bean的run接口。
_
# 二、Linstener机制
通过注册Listener，可以实现对于spring-boot整个生命周期各个状态变化进行监听，然后执行相应的业务代码。我们只需要监听其中几个启动状态就能够实现runner一样的功能了




_[七种方式教你在SpringBoot初始化时搞点事情](https://mp.weixin.qq.com/s?__biz=Mzk0NjExMjU3Mg==&mid=2247484571&idx=1&sn=09cdbdce8439670f0657451f525d8897&chksm=c30a55c8f47ddcdea0c4c1d67eb42013d6eff6a41a28a75e9314855deb8ed99bfd0825efbe41&scene=178&cur_album_id=1582225248089866241#rd)_


