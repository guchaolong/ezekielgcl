---
layout: post
subtitle: 知识积累
date: 2018-12-09
author: guchaolong
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
category: Java
tags:
  - Java
---

>掌握好java的基础知识


# 1.基础知识
补充：[[java基础]]


>**面向对象** 是一种**思想**，对现实世界的一种抽象
>
>**面向过程** 顺序性的完成一系列动作


>**静态**语言 如java，**编译期**确定**数据类型**，**运行前**就能够检查**类型**的**正确性**，要编写准确无误的代码；
>
>**动态**语言 如python，为了让程序员提高编码**效率**，用更少的代码实现功能
>
>**静态**语言的**执行效率**比动态语言**高**，速度更**快**

## 概述

1991年sun公司的james gosling开发oac，1994改名为java 

j2se、j2ee、j2me
==se==是另外两个的基础

jdk、jre、jvm
**jdk**包含：jre、java工具、java类库
JDK包含JRE，JRE包含JVM
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689110048085-0ebf8e0d-5b21-4d3a-b079-b26f5907be60.png#averageHue=%23efefef&clientId=ua4632015-d88a-4&from=paste&height=90&id=u0988d160&originHeight=179&originWidth=383&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13331&status=done&style=none&taskId=u2a799edf-eaef-482a-997b-bf401516cb4&title=&width=191.5)
>不同的操作系统有不同的jvm实现，java是运行在jvm上
多线程、健壮性

>运行一个java程序，就相当于启动了一个==jvm进程==，也就是一个==jvm实例==，jvm可以运行main方法，一台机器上可以运行多个jvm实例，每个jvm实例都有一套jmm，好比一台完整的机器，有内存、磁盘等，jvm实例之间共享那一台机器的内存空间


classpath:也就是.class文件所在的路径，jvm运行的时候，需要去加载.class文件，classpath告诉jvm去哪里加载.class


如果使用java的javac、java命令，就会去当前目录以及环境变量classpath中查找.class文件加载

服务器上，安装jdk后，配置环境变量JAVA_HOME、JRE_HOME  。然后tomcat是用java写的，也依赖与jre,启动tomcat可以通过运行bin下的startup.bat，startup.bat会调用catalina.bat文件，而catalina.bat会调用setclasspath.bat文件来获取JAVA_HOME和JRE_HOME这两个环境变量的值


## 数据类型
基本数据类型：
byte short int long float double char boolean

int 的取值范围:
-2,147,483,648（-2 ^ 31）和 2,147,483,647（2 ^ 31 -1）

<mark style="background: #FF5582A6;">char: 占2个byte, 16bit</mark>

boolean: 单独使用时占4个字节，在数组中每个boolean元素占1个字节

在java里面，没小数点的默认是int,有小数点的默认是 double

byte-short-int-long-float-double遵循规则，有char都必须强转 


引用类型：除基本数据类型以外的，都是引用类型，<mark style="background: #FF5582A6;">数组</mark>也是引用类型


包装类型
`new Integer(123)`每次都会创建一个新对象
`Integer.valueOf(123)`使用缓存池中的同一个对象
<mark style="background: #D2B3FFA6;">-128~127</mark>，基本类型对应的包装类型，都有对应的缓存池


## 运算符:
**赋值、算术、自增减、比较、逻辑、位、位移、三元**
位运算，异或 ^ ,两边==不一样==的时候true（1)    两边相同的时候 false (0)
2\*8=2<<3
位运算，扩展[[二进制、原码、反码、补码]]

## 类型转换  

```java
byte b1=3,b2=4,b; 

b=3+4;//3和4都是常量，所以java在编译时期会检查该常量的和是否超出byte类型的范围。如果没有可以赋值  

b=b1+b2;//编译出错,因为b1和b2是变量，因为变量的值会变化，不确定具体的值，所以默认使用int类型进行存储

b1 = b1 +1;//出错，b1是变量，会转换为int类型  

b1 += 1; //可以完成自动类型转换
```

## 流程控制
if	if...else	if...else if（如果 if满足了，else if后面的就不会执行了）[https://www.liaoxuefeng.com/wiki/1252599548343744/1259539352677728](https://www.liaoxuefeng.com/wiki/1252599548343744/1259539352677728)


switch，固定值时，可以 if, 但建议 switch，效率相对较高
switch支持：`char，byte, short, int, Character, Byte, Short, Integer, String, enum`
不支持`long float double`,因为Switch设计的初衷就是对那些<mark style="background: #D2B3FFA6;">只有少数几个值</mark>的类型进行等值判断，如果过于复杂，还是if比较合适


while  do...while	for 
jdk1.5 之后出了 for-each,方便对数组和集合进行遍历
break	continue	return


# 2.面向对象
类、属性、方法、构造函数、重载、重写

继承、多态、组合
>多用组合，少用继承，组合的耦合性低

## 接口、抽象类
抽象类和普通类最大的区别是，<mark style="background: #FF5582A6;">抽象类不能被实例化，只能被继承</mark>

接口，java8之前，不能有任何的方法实现，java8开始，接口可以拥有默认的方法实现，因为，如果接口添加一个方法，所有的实现类都要修改，去实现这个方法，这样的话维护成本太高

本来接口的成员（字段+方法）默认都是public的，java9开始，允许将方法定义为private，这样就能定义某些复用的代码，又不会把方法暴露出去

接口的字段默认都是static和final的

## 内部类
静态内部类
<mark style="background: #FFB8EBA6;">非静态内部类</mark>依赖于外部类的实例，也就是说要先创建外部类的实例，才能用这个实例去创建非静态内部类，而静态内部类不需要
静态内部类不能访问外部类非静态的变量和方法

## this、super
<mark style="background: #FF5582A6;">公子包内</mark>
private 本类
default 同包
protected  子类(包括不同包下的子类）
public 所有

## final 
变量
基本类型，数值不变  
引用类型，不能再指向其他对象，对象本身是可以修改的

方法，不能被重写，<mark style="background: #FF5582A6;">private方法隐式地被指定为final</mark>,如果子类中定义的方法和父类的一个private方法签名相同，此时子类的方法不是重写基类方法，而是在子类定义了一个新的方法

类，不能被继承

## static
<mark style="background: #D2B3FFA6;">初始化</mark>顺序：
父类静态代码块
子类静态代码块
父类构造代码块
父类构造函数
子类构造代码块
子类构造函数

## 访问控制
(主要是一个<mark style="background: #FF5582A6;">可见性</mark>，可见就是<mark style="background: #FF5582A6;">可以用</mark>，“用”：同一个类内部，直接调，类外部，通过obj.xxx）
**private**:  只有在类内部才能用（只能在内部直接使用，类外不无法用，即obj.xxx是不行的）
**默认**：    内部（直接用）、同包下（obj.xxx)
**procted** : 内部、同包、子类中
**public** ： 到处


## String
不可变的特性
<mark style="background: #FF5582A6;">final</mark>修饰，java8，用char数组存储，java9以后用byte数组存储
不可变的好处
1. hash值也不会变，只需要进行一次计算
2. String Pool，重复利用
3. 线程安全

String Pool字符串常量池
java7之前，String Pool是在运行时常量池中，属于永久代，而在java7,String Pool被移到堆中，因为永久代空间有限，大量使用字符串的场景下会导致`OutOfMemoryError`错误
`new String("abc")`:会创建两个对象，一个在String Pool中，一个在堆中


## equals和hashCode
其实hashCode()方法和equals()方法的作用是一样的，都是用来判断两个对象是否相同。
java比较两个对象是否相同的标准方法是equals()方法，继承来的equals()默认是比较内存地址，
如果要实现自己的比较的逻辑，就需要重写equals方法

但为什么有了标准的equals了还要有hashCode呢？
因为<mark style="background: #FF5582A6;">equals</mark>往往比较<mark style="background: #FF5582A6;">复杂</mark>，执行<mark style="background: #FF5582A6;">效率不高</mark>，<mark style="background: #D2B3FFA6;">hashCode方法效率高</mark>
为什么hashCode效率高，为什么还要有equals呢？
因为hashCode不一定准确，如果hashCode相等，equals不一定相等

原则：
equals相等，hashCode必定相等
hashCode相等，equals不一定相等

HashSet存值：
首先算对象的hashCode值，看是否已经存在和该值相等的对象，如果不存在，则直接加入
如果存在，再进行equals判断，相等则舍弃，不相等，就加入

HashMap存取：
put:先算出hashCode值，用hashCode值进行hash计算得到索引位置，如果该位置没有对象则直接加入，
如果有，则进行equals判断，相等，则替换原来的value,
如果不相等，则使用“链地址”法，生成一个链表


# 3.集合  
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1681901726599-487fc937-7915-41a9-be26-379912397506.png#averageHue=%23fdfdfd&clientId=u66e9edbd-d778-4&from=paste&height=744&id=rO2eb&originHeight=1487&originWidth=2105&originalType=binary&ratio=2&rotation=0&showTitle=false&size=355105&status=done&style=none&taskId=ue90d16eb-2409-432e-856c-6032d26419a&title=&width=1052.5)

数组，初始化之后<mark style="background: #FFB8EBA6;">尺寸固定</mark>，只能通过<mark style="background: #BBFABBA6;">索引取出</mark>，所以要用到集合，删除某个元素之后，需要<mark style="background: #FFB8EBA6;">移动</mark>后续元素  
注意分两类：
1. Collection 集合类的根接口
    - List 有序可重复
    - Set 无序 不可重复
    - queue  先进先出，跟排队一样，在队尾加入，队头处理完就移除
2. Map 键值对


queue:
```
add     添加               如果队列已满，则抛出一个IIIegaISlabEepeplian异常
remove  移除并返回头部的元素  如果队列为空，则抛出一个NoSuchElementException异常
element 返回队列头部的元素    如果队列为空，则抛出一个NoSuchElementException异常

offer   添加并返回true           如果队列已满，则返回false
poll    移除并返问队列头部的元素 如果队列为空，则返回null
peek    返回队列头部的元素       如果队列为空，则返回null

put     添加一个元素             如果队列满，则阻塞
take    移除并返回队列头部的元素 如果队列为空，则阻塞
```

## ArrayList
> jdk1.8
基于<mark style="background: #FF5582A6;">数组</mark>实现，RandomAccess接口标识支持快速随机访问，默认容量<mark style="background: #FF5582A6;">10</mark>

扩容：
oldCapacity + (oldCapacity >> 1),即<mark style="background: #FF5582A6;">1.5倍</mark>
扩容操作要调用Arrays.copyOf()方法，复制整个数组到新数组，这个操作代价很高，因此，最好创建ArrayList对象时就指定容量大小，减少扩容次数

删除元素：
要移动后面的元素，代价很高

Fail-Fast:
modCount用来记录ArrayList结构发生变化的次数。结构发生变化是指<mark style="background: #FF5582A6;">添加</mark>或者<mark style="background: #FF5582A6;">删除</mark>至少一个元素的所有操作，或者调整内部数组的<mark style="background: #FF5582A6;">大小</mark>，仅仅是设置元素的值不算结构发生变化
进行序列化或者迭代操作时，需要比较操作前后modCount是否改变，如果改变了需要抛出ConcurrentModificationException异常

Vector：
使用了synchronized同步，每次扩容为<mark style="background: #FF5582A6;">2倍</mark>

替代方案：
1. 可以使用Collections.synchronizedList()得到一个线程安全的ArrayList
2. concurrent并发包下的CopyOnWriteArrayList

## CopyOnWriteArrayList
读写分离，互不影响，写操作在一个复制的数组上进行，读操作还是在原来的数组中进行

写操作需要加锁，防止并发写入时导致写入数据丢失，写操作结束后需要把原始数组指向新的复制数组

适用场景：
读多写少的应用场景

缺点：
1. 内存占用：复制数组，2倍左右
2. 数据不一致：读操作不能读取实时性数据，因为部分写操作还未同步到读数组中
所有不适合内存敏感以及对实时性要求高的场景

## LinkedList
基于双向链表实现


## HashMap

> jdk1.7

数组 + 单链表
Entry
头插法（此代码作者认为，后进来的被访问的可能性更大，头插，提高查询效率，rehash，多线程可能形成环链表）

> jdk1.8 

数组 + 链表/红黑树

HashMap 的长度为什么是 2 的幂次方？
**取余(%)操作中如果除数是 2 的幂次则等价于与其除数减一的与(&)操作（也就是说 hash%length==hash&(length-1)的前提是 length 是 2 的 n 次方；）

**采用二进制位操作 &，相对于%能够提高运算效率**



# 4.IO
输入（input）：把数据读到内存，如读硬盘上某个文件 从网络读取  
输出（output）：从内存输出到外部，如写到硬盘上的某个文件  
IO流：二进制数据最小以byte（字节流）为单位；字符流传输的最小数据单位时char,字符流输出的byte取决于编码方式  
同步IO:读写时等待数据返回 才能执行后续代码；编写简单 CPU效率低（JDK的java.io是同步IO）  
异步IO:读写IO发出请求，然后立刻执行后续代码；编写复杂 CPU执行效率高（JDK的java.nio是异步IO）  

```
FileInputStream  
​    int read():读取下一个字节，并返回改字节对应的int值（0-255）,末尾-1
​    int read(byte [] b):读取若干字节到数组b中，返回读取的字节数  
FileOutputStream  
​    write(byte[] b):写入b中的所有字节  
​    write(byte[] b,int off,int len):写入b指定范围的字节  
​    void flush():将缓冲区的内容输出  
```
​    
把项目依赖的资源放在classpath中可以避免文件路径的依赖（相对路径）  
Class对象的getResourceAsStream("")可以从classpath中读取资源（需要检查返回的stream是否为null）  

序列化  
把一个java对象变成二进制内容（byte[]），然后就可以把该数组保存在文件中 或在网络中传输

# 5.Java异常处理
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689106268361-53145fa0-32de-47b7-870e-57815f6fa713.png#averageHue=%23faf4f1&clientId=ua4632015-d88a-4&from=paste&height=952&id=u122c2fab&originHeight=952&originWidth=1604&originalType=binary&ratio=1&rotation=0&showTitle=false&size=232069&status=done&style=none&taskId=ud26567e7-efdf-4928-a55d-2f154d82565&title=&width=1604)

throws  throw
try...catch 、try...ﬁnally、try...catch...ﬁnally



# 6.多线程、并发
## 多核并发缓存架构：  
![Image text](https://raw.githubusercontent.com/guchaolong/guchaolong.github.io/master/_posts_img/cpu_mode.png)  

现在的计算机，从硬盘把数据读取到主内存，cpu在计算的时候，并不总是从内存读取数据，
它的数据读取顺序优先级 是：寄存器－高速缓存－内存。线程耗费的是CPU，线程计算的时候，
原始的数据来自内存，在计算过程中，有些数据可能被频繁读取，这些数据被存储在寄存器 和高速缓存中，当线程计算完后，这些缓存的数据在适当的时候应该写回内存。当个多个线程同时读写某个内存数据时，
就会产生多线程并发问题，涉及到三个特 性：原子性，有序性，可见性  

![Image text](https://raw.githubusercontent.com/guchaolong/guchaolong.github.io/master/_posts_img/jmm2.png)  

线程**工作内存**是cpu寄存器和高速缓存的抽象描述，使用频率高的数据从主存拷贝到高速缓存中，
每个线程在cpu高速缓存中对拷贝的数据进行读取、计算、赋值，
再在合适的时候同步更新到主存的该数据，如i=1，i+1=2，若2在更新到主存前，
其他线程是不知道该值被改变了，其他线程高速缓存中该值依然为1.

解决方法：需要各线程间可见的变量前加上volatile修饰，
在一个线程的高速缓存中改变该值时，其他线程会获得该值的更新值

## JVM内存模型1    
jvm的设计的模型其实就是操作系统的模型，基于操作系统的角度，jvm就是个java.exe/javaw.exe，也就是一个应用，jvm就是个操作系统，而jvm的方法区，也就相当于操作系统的硬盘区（permanent 也就是永久区）  

启动一个java进程会相当于启动一个jvm实例，一台机器上可以有多个jvm实例，打开任务管理器可以看到多个java.exe或javaw.exe,
jvm实例也是运行在机器的内存中的，只不过在jvm内部又存在jmm  

当一个classLoader启动的时候，classLoader的生存地点在jvm中的堆，然后它会去主机硬盘上将A.class装载到jvm的方法区，方法区中的这个字节文件会被虚拟机拿来new A()，然后在堆内存生成了一个A的对象，然后A对象有两个引用一个指向A的Class对象，一个指向加载自己的classLoader
（图中应该是有误的）  
如图：  
![Image text](https://raw.githubusercontent.com/guchaolong/guchaolong.github.io/master/_posts_img/jmm1.jpg)

## JMM数据原子操作

* read 读取：从主内存读取数据
* load 载入：将读取到的数据写入工作内存
* use 使用：从工作内存取数据进行计算
* assign 赋值：计算好的值重新赋值到工作内存
* store 存储：工作内存的数据存储到主存
* write 写入：将store到主存的数据赋值给主存中的变量
* lock 锁定：将主存变量加锁，标识为线程独占状态
* unlock 解锁：将主存变量解锁，其他线程可以锁定该变量

# 7.反射
> **java的反射机制是框架设计的灵魂，反射是框架的基础** 
> 反射是 java很重要也很高级的特性，spring等一系列框架就是根据反射的思想写成的

## 定义
java运行状态下，对于任意一个类，都能知道类的属性和方法；对于任意一个对象，都能调用它的任意属性和方法，这种动态获取信息和动态调用对象方法的机制叫做反射   

每个类都有一个 Class 对象，包含了与类有关的信息。当编译一个新类时，会产生一个同名的 .class 文件，该文件内容==保存==着 Class 对象。==类加载相当于 Class 对象的加载==，类在第一次使用时才动态加载到 JVM 中。也可以使用 Class.forName,这种方式来控制类的加载，该方法会返回一个 Class 对象


**jvm 编译 运行**        
类的加载：运行一个程序的时候，JVM启动，运行启动类加载器：bootstrap classloader用于加载java核心API（ExtClassLoader和AppClassLoader也在此时被加载），然后`ExtClassLoader`加载扩展API,`AppClassLoader`加载classpath下的API  

在编译时.java文件被编译器编译成.class文件        

运行时，启动jvm进程，jvm从classpath路径下寻找并加载.class文件，将**类的类型信息**加载到**方法区** ，然后，在堆里创建代表这个类的java.lang.class对象（每个类的Class对象都只有一个，jvm对每个类都只会加载一次），作为方法区中类信息的访问入口，我们使用反射得到的那个class对象就是这个，它相当于一面镜子，映射出方法区中该类的信息

Class对象是jvm创建的

jvm为每个加载的类创建对应的Class实例，在该实例中保存了类的所有信息

通过Class实例获取类信息的方法叫做==反射==
  
利用JVM动态加载class的机制，可以在运行期间根据条件加载不同的实现类

## 三种方式
```java
Class c1 = Student.class;//知道类名

Student student = new Student();
Class c2 = student.getClass();//知道对象名

Class c3 = Class.forName("com.guchaolong.javalearn.chapter04_reflect.Student");
```



## 反射的优点
1. 扩展性，外部自定义的类，根据完全限定名创建实例

## 反射的缺点
1. 性能开销：涉及动态类型的解析，JVM无法对这些代码进行优化
2. 安全限制：要求程序在没有安全限制的环境中运行
3. 内部暴露：反射允许代码执行一些在正常尽快下不被允许的操作，比如访问私有的属性和方法

# 8.泛型
* 引出
```java
        List list = new ArrayList();
        list.add("sdf");
        list.add(12);
        for (Object o : list){
            String a = (String)o;
        }
```

ArrayList底层使用数组存储元素，元素的类型是Object,如果把不同类型的对象放进去，取出来的时候就不知道，具体是哪个类型，会报类型转换异常，使用`ArrayListM<String>`之后，就只能放入String类型的对象

Object类是所有类的根类，所以都可以向上转换为Object类型的引用，使用的时候再向下转换，运行期间可能报转换异常，但是使用了泛型标识之后，在实际使用时，类型就已经确定了，不需要在进项强制类型转换

* 特性
<mark style="background: #FF5582A6;">泛型只在编译期有效，编译之后会进行类型擦除</mark>（编译期间正确检验泛型结果后，将泛型相关信息擦除）
```java
    List<String> l1 = new ArrayList<String>();
    List<Integer> l2 = new ArrayList<Integer>();
    System.out.println(l1.getClass().equals(l2.getClass()));//true
```


* 泛型的使用-泛型类 泛型接口 泛型方法 通配符
```java
/**定义泛型类
 * T也可以写成其他,泛型也叫做参数化类型，这里的T就相当于一个形式参数
 * 在实例化这个泛型类的时候再指定实际类型，（实际参数）
 */
public class Generic<T> {

    //key这个成员变量的类型为T,T的类型由外部指定
    private T key;

    public Generic(T key) {
        this.key = key;
    }
    
    //虽然在方法中使用了泛型，但是这并不是一个泛型方法。
    //这只是类中一个普通的成员方法，只不过他的返回值是在声明泛型类已经声明过的泛型。
    //所以在这个方法中才可以继续使用 T 这个泛型。
    public T getKey() {
        return key;
    }
    public void setKey(T key) {
        this.key = key;
    }
}

        Generic g0 = new Generic("DS");//如果不指定，就起不到类型检查的作用，会按Object处理
        Generic<String> g1 = new Generic<>("df");
        System.out.println(g1.getKey());
        Generic<Integer> g2 = new Generic<>(12);
```


```java
public interface Generator<T> {
    T next();
}
/**
 * 未传入泛型实参时(还是T), 实现类后面必须要有<T> 否则报错
 */
public class FruitGenerator<T> implements Generator<T> {
    @Override
    public T next() {
        return null;
    }
}
//传入泛型实参（String)
public class FruitGenerator implements Generator<String> {
    @Override
    public String next() {
        return null;
    }
}
```


```java
    static void f1(Generic<Number> n){
        System.out.println(n.getClass());
    }
    
    Generic<Number> n1 = new Generic<>(1);
    f1(n1);
    Generic<Integer> n2 = new Generic<>(2);
    f1(n2);//会报错,f1()接口的类型时Generic<Number> n 这是就需要通配符
    
    //这里的？就是通配符，在这里时类型实参，和String Number 这些一样 是实际的类型
    static void f2(Generic<？> n){
       System.out.println(n.getClass());
    }
    f2(n1)；
    f2(n2)；
```

泛型类，是在实例化类的时候指明泛型的具体类型；泛型方法，是在调用方法的时候指明泛型的具体类型

```java

        //我想说的其实是这个，虽然在方法中使用了泛型，但是这并不是一个泛型方法。
        //这只是类中一个普通的成员方法，只不过他的返回值是在声明泛型类已经声明过的泛型。
        //所以在这个方法中才可以继续使用 T 这个泛型。
        public T getKey(){
            return key;
        }

        /**
         * 这个方法显然是有问题的，在编译器会给我们提示这样的错误信息"cannot reslove symbol E"
         * 因为在类的声明中并未声明泛型E，所以在使用E做形参和返回值类型时，编译器会无法识别。
        public E setKey(E key){
             this.key = keu
        }
        */
    }


    /** 
     * 这才是一个真正的泛型方法。
     * 首先在public与返回值之间的<T>必不可少，这表明这是一个泛型方法，并且声明了一个泛型T
     * 这个T可以出现在这个泛型方法的任意位置.
     * 泛型的数量也可以为任意多个 
     *    如：public <T,K> K showKeyName(Generic<T> container){
     *        ...
     *        }
     */
    public <T> T showKeyName(Generic<T> container){
        System.out.println("container key :" + container.getKey());
        //当然这个例子举的不太合适，只是为了说明泛型方法的特性。
        T test = container.getKey();
        return test;
    }


    //这也不是一个泛型方法，这就是一个普通的方法，只是使用了Generic<Number>这个泛型类做形参而已。
    public void showKeyValue1(Generic<Number> obj){
        Log.d("泛型测试","key value is " + obj.getKey());
    }


    //这也不是一个泛型方法，这也是一个普通的方法，只不过使用了泛型通配符?
    //同时这也印证了泛型通配符章节所描述的，?是一种类型实参，可以看做为Number等所有类的父类
    public void showKeyValue2(Generic<?> obj){
        Log.d("泛型测试","key value is " + obj.getKey());
    }

     /**
     * 这个方法是有问题的，编译器会为我们提示错误信息："UnKnown class 'E' "
     * 虽然我们声明了<T>,也表明了这是一个可以处理泛型的类型的泛型方法。
     * 但是只声明了泛型类型T，并未声明泛型类型E，因此编译器并不知道该如何处理E这个类型。
    public <T> T showKeyName(Generic<E> container){
        ...
    }  
    */

    /**
     * 这个方法也是有问题的，编译器会为我们提示错误信息："UnKnown class 'T' "
     * 对于编译器来说T这个类型并未项目中声明过，因此编译也不知道该如何编译这个类。
     * 所以这也不是一个正确的泛型方法声明。
    public void showkey(T genericObj){

    }
    */
```
 

+ 泛型上下边界
    使用泛型的时候，我们还可以为传入的泛型类型实参进行上下边界的限制，如：类型实参只准传入某种类型的父类或某种类型的子类

```java
//上边界，<? extends T> 即传入的类型实参必须是指定类型的子类型
<? extends Number> obj)

//下边界 ：<? super T>  
<? super Number> obj)
```

* 符号
```java
    E - Element (在集合中使用，因为集合中存放的是元素)  
    T - Type（Java 类）                    
    K - Key（键）                    
    V - Value（值）                    
    N - Number（数值类型）                 
    ？ -  表示不确定的java类型 
```


# 9.注解
java 注解 Annotation，又称元数据，它为我们在代码中添加信息提供了一种形式化的方法

它是 jdk1.5 引入的，java 定义了一套注解，共 7 个，3 个在 java.lang中，4 个在 java.lang.annotation中
用在代码中的三个
`@Override`
`@Deprecated`
`@SuppressWarnings`

4 个元注解，是用来<mark style="background: #FFB8EBA6;">标注注解</mark>的注解
@`@Retention` 
`@Documented` 
`@Target` 
`@Inherited`

jdk1.7 开始，有添加了三个额外的注解
`@SafeVarargs`
`@FunctionalInterface`
`@Repeatable`
 
# 10.网络编程
## Socket
+ 是一个抽象概念  
+ 一个应用程序通过一个Socket来建立一个远程连接  
+ Socket内部通过TCP/IP协议把数据传输到网络  
+ Socket、TCP、IP的功能都是操作系统提供的，不同的编程语言只是提供了对操作系统调用的简单封装,例如Java提供的几个类就封装
了操作体统提供的接口  

## 为什么需要Socket？
+ 同一台计算机 同一时间会运行多个网络程序，当计算机收到一个数据包的时候，如果只有IP地址，就没法判断应该发给哪个应用程序
所以操作系统抽象除Socket，每个应用程序需要对应到不同的Socket
+ 可以把IP地址简单理解为IP+端口号（0-65535，由操作系统分配，其中小于1024的端口属于特权端口，需要管理员权限） 
    ```java
    public class TCPClient {
        public static void main(String[] args) {
            InetAddress addr = InetAddress.getLoopbackAddress();//localhost/127.0.0.1
            System.out.println(addr);
            try {
                Socket socket = new Socket(addr, 9090);//打开一个远程连接
                BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream(), StandardCharsets.UTF_8));
                BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream(), StandardCharsets.UTF_8));
                writer.write("time\n");
                writer.flush();
                String resp = reader.readLine();
                System.out.println("Response: "+resp);
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
    
    public class TCPServer {
        public static void main(String[] args) {
    
            try {
                ServerSocket serverSocket = new ServerSocket(9090);
                System.out.println("Tcp server ready");
                Socket socket = serverSocket.accept();
    
                BufferedReader reader = new BufferedReader(new InputStreamReader(socket.getInputStream(), StandardCharsets.UTF_8));
                BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream(), StandardCharsets.UTF_8));
                String cmd = reader.readLine();
                if("time".equals(cmd)){
                    writer.write(LocalDateTime.now().toString()+"\n");
                    writer.flush();
                }else{
                    writer.write("sorry?\n");
                    writer.flush();
                }
    
                socket.close();
                serverSocket.close();
    
            } catch (IOException e) {
                e.printStackTrace();
            }
    
        }
    }
    ```

# 11.JAVA8、JAVA9
## 函数式编程  

和面向对象编程、面向过程编程类似，函数式编程是另一种编程范式、思想、方法论  
在函数式编程中，函数是第一等公民，可以被赋值，可以被当作参数传递

## 匿名类和函数接口

``` java
 Runnable runnable = new Runnable() {
            @Override
            public void run() {
                System.out.println("hello");
            }
        };
```
- __匿名类__：  
  以上是匿名类的典型，首先接口是不能实例化的，接口也没有构造方法，被new修饰是因为，new的时候实际是创建了一个匿名的实现了Runable接口的
  实现类，实现了run方法，如果没有匿名类，就需要单独去创建一个类实现run方法，代码就会更加繁琐，于是就有了`lambda`表达式  

- __函数接口__
  java8之后接口里可以有默认方法，有且仅有一个抽象方法的接口，叫做函数接口，函数接口可以用lambda表达式  
  java8以前的函数接口有`Runnable` `Callable` `Comparator`等
  Java8以后，增加了 `java.util.function`下的一些类 如`Predicate<T>、Supplier<T>`等  

- __Lambda表达式__:

  （）->{};  参数列表->语句

- __Stream API__:
  __流__ : 流水线，一步一步处理数据，最终得到想要的数据  

  __并行流__ : 有多个数据，如果是单核CPU,就是在一条流水线上处理数据，处理完一个再处理另一个；如果是在多核CPU上，每个CPU上可以处理一个数据，每个CPU都相当于一条流水线，同时进行  

  __中间操作__:  返回一个流  

  __终止操作__:不返回流  

  __惰性求值__:如果流没有做中止操作，中间操作就不会执行  

  __map()__  转换，例如源数据是一个字符串，可以用map获得该字符串的长度  

  __flatMap()__  A对象，A对象下面有个集合类型的属性b,使用map()，每个A都会得到一个b的列表，使用flatMap(),可以得到所有A对象的所有b属性的一个列表  

  __filter()__  过滤  

  __peek()__  peek接收一个没有返回值的λ表达式，可以做一些输出，外部处理等。map接收一个有返回值的λ表达式，之后Stream的泛型类型将转换为map参数λ表达式返回的类型

  __reduce()__  对所有数据进行处理得到一个结果  如下 输出Optional\[my|name|is|faker]  13 0是初始值
```java
Optional<String> reduce = Stream.of(str.split(" ")).reduce((s1, s2) -> s1 + "|" + s2);  
System.out.println(reduce);  
  
Integer reduce1 = Stream.of(str.split(" ")).map(s -> s.length()).reduce(0, (L1, L2) -> L1 + L2);  
System.out.println(reduce1);
```
 
> __Stream操作机制__ :
> 所有操作都是链式调用，如 要迭代A B C三个元素，操作有a b c三个，对A执行a b c，然后对B执行a b c,不会对A执行a后就对B执行a


## JDK9的Reactive Stream
Jdk9的引入的一套标准，是基于发布订阅模式数据处理的规范，和Jdk8的Stream没关系，代码也没有耦合  

在JDK9里面其实叫Flow API
- 背压  
  发布者和订阅者之间的互动，订阅者可以告诉发布者 需要多少数据，起到一个调节数据流量的作用  
  例子：自来水公司（发布者）、家庭（订阅者） 被动接受，有了背压（水龙头），需要就打开，不需要就关闭

- 结构  

    Flow  
    Publisher :发布者  
    Subscriber :订阅者  
    Subscription :订阅关系  
    Processor：对数据进行过滤和加工   
    能实现背压的原因 订阅者会把收到的数据先放到缓冲池（默认256条数据），发布者的submit()方法是一个阻塞方法，当订阅者的缓冲池满了，就不会再发布  
    阅者消费了一条数据之后，发布者又再发布一条

- 响应式编程
    1. 同步、异步：  
        同步就是一件事做完之后，再做另一件事；异步就是做一件事，还没完成，在等待期间开始做另一件事
    2. 同步Servlet、异步Servlet:  
        前者是阻塞的，tomcat容器管理Servlet线程(线程调用servlet中的service方法)，一个请求对应一个Servlet线程，一个请求到达之后，tomcat容器启动一个Servlet线程去处理，处理完这个请求之后，这个Servlet线程才会去处理其他请求  
        后者是非阻塞的，一个请求到达，启动一个Servlet线程处理，在等待业务逻辑处理的时候，这个Servlet线程可以去处理其他请求，这样就可以提高并发量 
    3. Reactor = jdk8的Stream + jdk9的Reactive Stream  
        Mono和Flux都实现了Publisher  
        Mono 0-1个元素  
        Flux 0-n 个元素


