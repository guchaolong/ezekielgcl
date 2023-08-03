#JVM   

# 一、JVM基础知识
## 什么是JVM
JVM是可以运行Java代码的**虚拟的计算机**，既然是虚拟的计算机，当然也包含自己的**CPU、字节码指令集、寄存器、栈、垃圾回收、堆和存储方法域**，我们可以理解成JVM自己就是一套**操作系统**

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682010646487-bba13d59-3002-461c-986d-1ec292e19806.png#averageHue=%23515146&clientId=uca222285-5858-4&from=paste&height=324&id=N4Vko&originHeight=648&originWidth=1666&originalType=binary&ratio=2&rotation=0&showTitle=false&size=583646&status=done&style=none&taskId=ua12b87e2-ade3-42df-8311-e06b2dae1e2&title=&width=833)
能够在jvm上跑的语言除了有java, 还有scala lotlin等很多 ，目前有一百多种语言可以跑在Java虚拟机上…
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682010819583-eb4cb285-38bc-4e33-861d-d3d0fa3085bd.png#averageHue=%23111410&clientId=uca222285-5858-4&from=paste&height=348&id=SnOiQ&originHeight=499&originWidth=1211&originalType=binary&ratio=2&rotation=0&showTitle=false&size=598855&status=done&style=none&taskId=ubc332a80-f32d-4685-ac9f-026c49f00da&title=&width=843.5)

## Java从编码到执行
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682011362408-4e4c6fe5-0cb5-42c1-b567-df6237d0c2c9.png#averageHue=%23634215&clientId=uca222285-5858-4&from=paste&height=397&id=ua484e288&originHeight=769&originWidth=1625&originalType=binary&ratio=2&rotation=0&showTitle=false&size=920663&status=done&style=none&taskId=u16a35a01-93ad-498e-9cbb-202a699104d&title=&width=839)
## JVM与class文件格式
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682010874916-cb0cf817-9776-4987-a08e-b14c02e345f5.png#averageHue=%23a64415&clientId=uca222285-5858-4&from=paste&height=439&id=u41f38786&originHeight=641&originWidth=1277&originalType=binary&ratio=2&rotation=0&showTitle=false&size=501125&status=done&style=none&taskId=uc37c2d58-8ca0-4a71-8c27-aa672fbc660&title=&width=875.5)
jvm其实是和java没有关系的，只跟class有关系，跟其他的语言没有关系
这么多语言能在JVM上跑，最根本的原因就是class, 任何语言，只要能编译成class文件，符合class的规范，就能在jvm上跑

## 常见的JVM实现
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682011415698-7a8bdff6-5024-45f5-951a-beb9cd890890.png#averageHue=%231c1c1c&clientId=uca222285-5858-4&from=paste&height=426&id=u3e532ae7&originHeight=683&originWidth=1471&originalType=binary&ratio=2&rotation=0&showTitle=false&size=734932&status=done&style=none&taskId=ueb8d0621-12af-46fb-9a13-be9f5cb7773&title=&width=916.5)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682013062391-9250869a-f7b8-4435-9ae6-fa4c4ba8f2c4.png#averageHue=%2318100f&clientId=uc48cf5aa-a7c5-4&from=paste&height=261&id=u5b64c5a9&originHeight=482&originWidth=1568&originalType=binary&ratio=2&rotation=0&showTitle=false&size=145501&status=done&style=none&taskId=u0a70a172-33de-4994-880b-c6aa19387bf&title=&width=849)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682013079104-169afd1c-794e-4888-80e9-14e4c037ed7f.png#averageHue=%23102731&clientId=uc48cf5aa-a7c5-4&from=paste&height=113&id=u1f9c4686&originHeight=95&originWidth=761&originalType=binary&ratio=2&rotation=0&showTitle=false&size=36369&status=done&style=none&taskId=u295072e7-3517-47ce-a0dc-a64e8354e12&title=&width=905.5)

## 关于java收费
java要收钱，我该怎么办？
java收费，说的是jvm收费，不是java语言收费，java语言收费就完蛋了
hotspot从8开始，不再支持免费升级了，要进行收费了
怎么办呢，不用它就行了，可以用openJDK, 开源的 

## JDK JRE JVM
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682012330910-d6335dff-4fe1-4ca6-94a9-98dece248934.png#averageHue=%23927914&clientId=uc48cf5aa-a7c5-4&from=paste&height=425&id=uc2dc92b2&originHeight=608&originWidth=1177&originalType=binary&ratio=2&rotation=0&showTitle=false&size=294780&status=done&style=none&taskId=ua0c19616-da69-41f2-8668-e3df5446e1b&title=&width=823.5)

# 二、ClassFileFormat
> 面试不太会问到，当作兴趣了解
> 

`javap`是jdk自带的反解析工具。它的作用就是根据class字节码文件，反解析出当前类对应的code区（汇编指令）、本地变量表、异常表和代码行偏移量映射表、常量池等等信息。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682019838056-588da14f-bd76-405a-878d-3ce69d590eae.png#averageHue=%23303030&clientId=u70bc0c89-c77e-4&from=paste&height=362&id=u0d40baa7&originHeight=724&originWidth=1727&originalType=binary&ratio=2&rotation=0&showTitle=false&size=158293&status=done&style=none&taskId=uf43e51a9-cb78-4f17-84f7-1807298ed2b&title=&width=863.5)

Java虚拟机规定用u1、u2、u4三种数据结构来表示1、2、4字节无符号整数，相同类型的若干条数据集合用表（table）的形式来存储。
```c
classFile{
u4              magic;                                  // 魔数

u2              minor_version;                          // 副版本号
u2              major_version;                          // 主版本号

u2              constant_pool_count;                    // 常量池数
cp_info         constant_pool[constant_pool_count - 1]; // 常量池

u2              access_flags;                           // 访问标记
u2              this_class;                             // 类索引
u2              super_class;                            // 超类索引

u2              interfaces_count;                       // 接口数
u2              interfaces[interfaces_count];           // 接口表

u2              fields_count;                           // 字段数
field_info      fields[fields_count];                   // 字段表

u2              methods_count;                          // 方法数
method_info     methods[methods_count];                 // 方法表

u2              attributes_count;                       // 属性数
attribute_info  attributes[attributes_count];           // 属性表
}
```


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682021618882-3c7ca12e-1988-4193-aeaa-021d4bdc3b18.png#averageHue=%23f4f4f4&clientId=u70bc0c89-c77e-4&from=paste&height=875&id=ue6d0db96&originHeight=1750&originWidth=1384&originalType=binary&ratio=2&rotation=0&showTitle=false&size=396794&status=done&style=none&taskId=ucacbee3f-6673-4a58-8b3d-796840053dd&title=&width=692)


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682023548508-9e4a1418-300f-4fe2-9849-54c74d6d661b.png#averageHue=%2390683a&clientId=u70bc0c89-c77e-4&from=paste&height=427&id=aLBBL&originHeight=684&originWidth=1277&originalType=binary&ratio=2&rotation=0&showTitle=false&size=831544&status=done&style=none&taskId=u02e74350-0ce5-4fe8-9123-ce3279a2a34&title=&width=796.5)

## 魔数：
魔数0xCAFEBABE是JVM识别.class文件的标志，虚拟机在加载类文件之前会先检查这4个字节，如果不是0xCAFEBABE，则会抛出java.lang.ClassFormatError异常
## 版本号：
在魔数之后的四个字节分别表示**副版本号（Minor Version）**和**主版本号（Major Version）**
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682019227591-15277913-e830-40b9-8854-67bb8f741a25.png#averageHue=%23f4f4f4&clientId=u70bc0c89-c77e-4&from=paste&height=320&id=u885a8856&originHeight=640&originWidth=1798&originalType=binary&ratio=2&rotation=0&showTitle=false&size=205917&status=done&style=none&taskId=u603c1ed2-1489-4437-8525-2637bff3160&title=&width=899)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682020030272-5b135f37-d7c7-4c6c-a24c-95a6a746e936.png#averageHue=%232b2b2b&clientId=u70bc0c89-c77e-4&from=paste&height=233&id=u78c776b8&originHeight=465&originWidth=1576&originalType=binary&ratio=2&rotation=0&showTitle=false&size=103110&status=done&style=none&taskId=ub4b158cc-1f26-4120-99e9-4130e830c9e&title=&width=788)

## 常量池
常量池中常量的数量是不固定的，所以在常量池入口需要放置一个 u2 类型的数据来表示常量池的容量「constant_pool_count」，和计算机科学中计数的方法不一样，这个容量是从 1 开始而不是从 0 开始计数。之所以将第 0 项常量空出来是为了满足后面某些指向常量池的索引值的数据在特定情况下需要表达「不引用任何一个常量池项目」的含义，这种情况可以把索引值置为 0 来表示。
> _Class 文件结构中只有常量池的容量计数是从 1 开始的，其它集合类型，包括接口索引集合、字段表集合、方法表集合等容量计数都是从 0 开始。_

常量池中主要存放两大类常量：**字面量**和**符号引用**。

- **字面量**比较接近 Java 语言层面的常量概念，如字符串、声明为 final 的常量值等。
- **符号引用**属于编译原理方面的概念，包括了以下三类常量：
   - 类和接口的全限定名
   - 字段的名称和描述符
   - 方法的名称和描述符
## access_flag
访问标志
紧接着常量池之后的两个字节代表访问标志（access_flag），这个标志用于识别一些类或者接口层次的访问信息，包括这个 Class 是类还是接口；是否定义为 public 类型；是否定义为 abstract 类型；如果是类的话，是否被申明为 final 等。具体如果是类的话，是否被申明为 final 等。具体的标志位以及标志的含义见下表
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682022012419-70e89d06-8d6f-4905-ae2d-86c7e214461c.png#averageHue=%23f1f1f1&clientId=u70bc0c89-c77e-4&from=paste&height=594&id=u020e5a77&originHeight=1188&originWidth=1320&originalType=binary&ratio=2&rotation=0&showTitle=false&size=376522&status=done&style=none&taskId=uae4b43a5-2ae0-4bb3-9809-cdd894f7760&title=&width=660)
## this_class、super_name、interfaces
这三部分用来确定类的继承关系，this_class表示类索引，super_name表示直接父类的索引，interfaces表示类或者接口的直接父接口
this_class是一个指向常量池的索引，表示类或者接口的名字，用两字节表示
super_class 和interfaces的原理与之类似，不再赘述。

## 字段表
字段表包含 fields_count字段的数量 fields[fields_count]字段信息数组
**字段 field_info 结构**
```c
field_info{
     u2              access_flags;               // 访问标志
     u2              name_index;                 // 名字索引
     u2              descriptor_index;           // 描述索引
     u2              attributes_count;           // 属性数
     attribute_info  attribute[attributes_count];// 属性数组
 }
```
access_flags表示字段的访问标记，用来标识是public，private是protected，是否是static，是否是final等
name_index 用来表示字段名，指向常量池的字符串常量；
descriptor_index 是字段描述符的索引，指向常量池的字符串常量；
attributes_count、attribute_info表示属性的个数和属性集合。
## 方法表
## 属性表



# 三、类加载-初始化
## ClassLoader
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682024566574-e63d20c8-cfcd-499b-afad-99c5c73f23c2.png#averageHue=%23141412&clientId=u70bc0c89-c77e-4&from=paste&height=340&id=uba22deed&originHeight=687&originWidth=1744&originalType=binary&ratio=2&rotation=0&showTitle=false&size=1005369&status=done&style=none&taskId=u652bfd18-3d80-4304-a819-14c90efca80&title=&width=863)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682034569653-b879f639-4b43-4546-b36d-ac65ab655024.png#averageHue=%23856135&clientId=u4a1dd2e0-65a5-4&from=paste&height=273&id=ua28aff54&originHeight=540&originWidth=1666&originalType=binary&ratio=2&rotation=0&showTitle=false&size=145457&status=done&style=none&taskId=u4ee04646-46e2-472d-b187-46e33801d1e&title=&width=841)
> String是ClassLoader打印为null，是因为BootStrapClassLoader是用c++写的，使用原生代码来实现，并不继承于java.lang.ClassLoader，所以在返回该ClassLoader时就会返回null


双亲委派：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682035375852-d3e002e8-6403-44c7-b2dd-a66247b05591.png#averageHue=%234c1a13&clientId=u4a1dd2e0-65a5-4&from=paste&height=315&id=u69fb22ad&originHeight=489&originWidth=1440&originalType=binary&ratio=2&rotation=0&showTitle=false&size=726395&status=done&style=none&taskId=uaf76d8ca-1620-4a00-9ddb-1348d845e45&title=&width=929)
> 父加载器指的是ClassLoader类里的parent字段
> private final ClassLoader parent; 


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682034975208-768f44ea-9f7b-452b-b657-8ecb29eacb2b.png#averageHue=%23a55b48&clientId=u4a1dd2e0-65a5-4&from=paste&height=507&id=u8757f2ea&originHeight=1013&originWidth=1782&originalType=binary&ratio=2&rotation=0&showTitle=false&size=1550270&status=done&style=none&taskId=ue65d64a7-8e45-49f7-bbc6-ef8a1e08532&title=&width=891)  
 
类加载器范围
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682036800829-8f48cd6d-aa9e-4df6-8b70-5f2b11c78f2a.png#averageHue=%23222225&clientId=u4a1dd2e0-65a5-4&from=paste&height=249&id=u110d433b&originHeight=233&originWidth=725&originalType=binary&ratio=2&rotation=0&showTitle=false&size=222927&status=done&style=none&taskId=u803a5859-e070-425b-a2e0-bbf2bf10282&title=&width=775.5)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682036885373-6670461c-0333-4e75-b9d1-b3f663605bac.png#averageHue=%232e2e2e&clientId=u4a1dd2e0-65a5-4&from=paste&height=582&id=ue7cd1a60&originHeight=847&originWidth=1120&originalType=binary&ratio=2&rotation=0&showTitle=false&size=199376&status=done&style=none&taskId=u571fed45-701e-4ad7-a0aa-ce7e15e34bd&title=&width=770)


自定义类加载器
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682068613932-6c93f6e8-6e10-4b39-8f16-ff1fd73314a8.png#averageHue=%23252525&clientId=u7ab86c91-cb71-4&from=paste&height=375&id=ub884c6f9&originHeight=259&originWidth=551&originalType=binary&ratio=2&rotation=0&showTitle=false&size=160500&status=done&style=none&taskId=u02c94dd3-2bba-42db-bea3-68f0f67edb1&title=&width=797.5)

## 加载过程

1. 加载loading
2. 连接linking
   1. 验证verification
   2. 准备preparation
   3. 解析resolution
> 验证verification：验证文件是否符合JVM规定，看是否符合class文件的标准，魔数，CA FE BA BE
> 准备preparation：为静态变量赋默认值，如：static int num = 5; 这里将int设置为0，5的值会在初始化时赋值，对于final static修饰的变量，编译阶段就分配了
> 解析：将类、方法、属性等符号引用解析为直接引用，常量池中的各种符号引用解析为指针、偏移量等内存地址的直接引用

3. 初始化initializing
4. 使用
5. 卸载

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682023718065-217aaea8-3aa1-433c-9ac5-5cc45043683c.png#averageHue=%230b0d0a&clientId=u70bc0c89-c77e-4&from=paste&height=359&id=u1581385d&originHeight=718&originWidth=1674&originalType=binary&ratio=2&rotation=0&showTitle=false&size=949796&status=done&style=none&taskId=ue6394e1e-3655-44b8-8f8d-c47bd2d1a47&title=&width=837)
> 验证verification：验证文件是否符合JVM规定，看是否符合class文件的标准，魔数，CA FE BA BE
> 
> 准备preparation：为静态变量赋默认值，如：static int num = 5; 这里将int设置为0，5的值会在初始化时赋值，对于final static修饰的变量，编译阶段就分配了
> 
> 解析：将类、方法、属性等符号引用解析为直接引用，常量池中的各种符号引用解析为指针、偏移量等内存地址的直接引用
> 
> 初始化：调用类的初始化代码<clinit>，给静态成员变量赋初始值


```bash
public class Code_06_ClassLoadingProcedure {
    public static void main(String[] args) {
        System.out.println(T.count);
    }
}

class T {
    /*
    第一种情况：输出结果为3
    分析：
    加载：class文件落到内存
    验证
    准备：静态变量赋默认值，count=0， t = null
    解析
    初始化：静态成员变量赋初始值，count = 2,
            t = new T(), 调用了构造函数，count = 3
    ...
     */
    public static int count = 2;//默认值为0，初始值为2
    public static T t = new T();//默认值为null, 初始值为new T();

    private T() {
        count++;
    }
}

```


```bash
public class Code_06_ClassLoadingProcedure {
    public static void main(String[] args) {
        System.out.println(T.count);
    }
}

class T {
    /*
    第二种情况：输出结果为2
    分析：
    加载：class文件落到内存
    验证
    准备：静态变量赋默认值，t = null， count=0，
    解析
    初始化：静态成员变量赋初始值，t = new T()，调用了构造函数，count = 1;
           count = 2, ,
    ...
     */
    public static T t = new T();//默认值为null, 初始值为new T();
    public static int count = 2;//默认值为0，初始值为2




    private T() {
        count++;
    }
}

```
## 编译器
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682355730993-96e575ac-dfca-4e7a-86b3-c040134ed793.png#averageHue=%231f1f1e&clientId=ue2b5deab-f56e-4&from=paste&height=430&id=u580da084&originHeight=860&originWidth=1663&originalType=binary&ratio=2&rotation=0&showTitle=false&size=1303332&status=done&style=none&taskId=u8cfdb10b-7ca9-4e80-84f9-adc1ea967f7&title=&width=831.5)
> 默认使用混合模式
> class文件落到内存后，解释器解释执行，同时检测热点代码（多次被调用的方法、循环），把热点代码编译为本地代码


## 懒加载
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1682355928979-33c327a7-97d3-480d-b1ee-fddd5cd641e9.png#averageHue=%23222221&clientId=ue2b5deab-f56e-4&from=paste&height=428&id=ud7e5864b&originHeight=856&originWidth=1744&originalType=binary&ratio=2&rotation=0&showTitle=false&size=1405387&status=done&style=none&taskId=u5e1d7ca3-9769-4615-a898-208d69612fc&title=&width=872)


# 四、JMM

# 五、对象

