#Linux #Kali


# Linux
Unix/Linux/Linux发行版:
Linux 是一个类似 Unix 的操作系统，Unix 要早于 Linux，Linux 的初衷就是要替代 UNIX，并在功能和用户体验上进行优化，所以 Linux 模仿了 UNIX（但并没有抄袭 UNIX 的源码），使得 Linux 在外观和交互上与 UNIX 非常类似。

UNIX/Linux系统结构：
![](https://cdn.nlark.com/yuque/0/2023/jpeg/663445/1687113052606-8eda3e1a-e5a2-49a8-be1e-5735ae8d6452.jpeg#averageHue=%23f6f6f6&clientId=ua30f09d9-dfc4-4&from=paste&id=ua9c82b97&originHeight=289&originWidth=400&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u254e40fb-92a8-4f96-b36e-1682ec68ac9&title=)
1) 内核层
内核层是 UNIX/Linux 系统的核心和基础，它直接附着在硬件平台之上，控制和管理系统内各种资源（硬件资源和软件资源），有效地组织进程的运行，从而扩展硬件的功能，提高资源的利用效率，为用户提供方便、高效、安全、可靠的应用环境。
2) Shell层
Shell 层是与用户直接交互的界面。用户可以在提示符下输入命令行，由 Shell 解释执行并输出相应结果或者有关信息，所以我们也把 Shell 称作命令解释器，利用系统提供的丰富命令可以快捷而简便地完成许多工作。
3) 应用层
应用层提供基于 X Window 协议的图形环境

# Kali
> 黑客最喜欢的操作系统
> linux发行版操作系统，拥有超过300个渗透测试工具，集成了600多种黑客工具，可以永久免费使用kali

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687113552966-bee7279d-8684-41a6-9044-44f202b76f81.png#averageHue=%23e6e6e6&clientId=ua30f09d9-dfc4-4&from=paste&height=395&id=u2ed8b1f1&originHeight=395&originWidth=1423&originalType=binary&ratio=1&rotation=0&showTitle=false&size=254450&status=done&style=none&taskId=ub38e909e-706c-4f1f-9060-da3744d1463&title=&width=1423)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687119449852-8b9c650a-d6ab-4142-86b5-3a91afa7787f.png#averageHue=%232b2e3d&clientId=u72fad70d-3dbb-4&from=paste&height=854&id=u67ce9ebc&originHeight=854&originWidth=1701&originalType=binary&ratio=1&rotation=0&showTitle=false&size=518918&status=done&style=none&taskId=u1237c395-555b-475d-8703-c238d931f19&title=&width=1701)


## 切换语言
sudo dpkg-reconfigure locales
选择zh-CN
重启

## 搜历史命令
方法1：history
方法2：ctrl + r + '关键字'
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687128623725-0d255c97-01f7-4b93-a082-2e7593ff17c1.png#averageHue=%231e2028&clientId=u726d8754-8b53-4&from=paste&height=720&id=u34b4fad9&originHeight=720&originWidth=1280&originalType=binary&ratio=1&rotation=0&showTitle=false&size=152227&status=done&style=none&taskId=ufa484c64-e125-493d-a38f-e3c6f78b5a9&title=&width=1280)

## xshell远程连接kali
[链接](https://huaweicloud.csdn.net/63563d6dd3efff3090b5bdd1.html?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Eactivity-1-125249371-blog-127337556.235%5Ev38%5Epc_relevant_anti_vip&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Eactivity-1-125249371-blog-127337556.235%5Ev38%5Epc_relevant_anti_vip&utm_relevant_index=2)

## kali默认字体
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687134667208-8eebf93e-7feb-4c18-a582-372c7c0b0319.png#averageHue=%231e212a&clientId=u398d6528-f7af-4&from=paste&height=860&id=ufe33dfd9&originHeight=860&originWidth=1280&originalType=binary&ratio=1&rotation=0&showTitle=false&size=288817&status=done&style=none&taskId=u4b71689d-00e1-4064-9b77-f34fe1247f2&title=&width=1280)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687134720113-9246b12e-4d58-42a6-b4cf-f23509592e71.png#averageHue=%231e2129&clientId=u398d6528-f7af-4&from=paste&height=860&id=ua9fed796&originHeight=860&originWidth=1280&originalType=binary&ratio=1&rotation=0&showTitle=false&size=287030&status=done&style=none&taskId=u261046d6-29a7-44b7-a21a-948e87cfc55&title=&width=1280)
