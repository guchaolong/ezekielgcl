#Linux 

>Linux 的世界里，一切皆文件

# 关于linux发行版以及发行版对应的包管理工具

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202311050422584.png)

说到Linux不得不说它的两大派系：
1.RedHat系列：
>Redhat、Centos、Fedora 等
>注重稳定性和安全，主要用于生产环境，适用于服务器环境，比如CentOS
>虚拟机安装的时候都没有界面，只有命令行
>使用的是基于RPM的YUM软件包管理器

2.Debian系列：
>Debian、Ubuntu、kali等
>注重用户友好性，桌面环境，也有命令行，更适用于个人，
>使用DPKG 机制的APT软件包管理


[浅谈Linux下dpkg、apt-get、yum和rpm命令的区别-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1759038)

[5 种 Linux 安装包管理工具中文手册！抓紧看，别再说不会了，丢人。。。-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/2141242?areaId=106001)

>主要学习centos，因为用户界面有win和macos了，再学了服务器环境的centos


# 获取 Linux 环境的方式
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687808047983-c3bf3500-5c9c-4de6-a1b0-7b30006a7c69.png#averageHue=%23f2f3f6&clientId=ud46e4ec5-23ba-4&from=paste&height=1071&id=u37616923&originHeight=964&originWidth=1475&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=294536&status=done&style=none&taskId=ud7c813bb-6a29-441d-b1a2-fc3014e0c4d&title=&width=1638.888932304619)

> ubuntu:
> user: guchaolong
> psd: guchaolong


> Kali
> user: kali
> psd: kali
> root psd: kali


> Xshell连接虚拟机Ubuntu，出现连接不上，物理机ping虚拟机ip，出现超时
> 需要虚拟机安装ssh服务：`sudo apt-get install openssh-server`，物理机再次ping虚拟机ip，就能连接了

# Linux目录介绍
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687812625293-56ca80ff-63b0-467e-b314-359b4171e858.png#averageHue=%23f5f2df&clientId=u9aca1641-503c-4&from=paste&height=987&id=u88e84089&originHeight=888&originWidth=617&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=279313&status=done&style=none&taskId=u2dd32ce8-c740-46cf-ba8a-0c587dd5f3b&title=&width=685.5555737165762)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687812684407-79f0353e-136f-4a3b-a2ab-beb7c79ced22.png#averageHue=%23f9f6e3&clientId=u9aca1641-503c-4&from=paste&height=138&id=u9f010029&originHeight=124&originWidth=620&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=28878&status=done&style=none&taskId=u934ea63e-1609-42ea-9dbe-d42a4288b65&title=&width=688.8889071382127)

# 文件类型和权限
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687815387009-ddb00b73-307c-4f2c-8b64-3db0fb073cad.png#averageHue=%2376be98&clientId=u9aca1641-503c-4&from=paste&height=485&id=u80993ab2&originHeight=790&originWidth=1801&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=561816&status=done&style=none&taskId=u7c909cd5-16da-4273-984f-575ba9fe835&title=&width=1106.763916015625)
Linux 中文件可以分为 5 个类型， ls -l 输出的每条信息中的 第一个字符 就用于表示文件类型。
```
d	目录
-	文件
l	符号链接等
b	可供储存的接口设备
c	串行端口设备，如键盘、鼠标等
```


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687816458017-2478080c-7d15-42ec-90d5-863cdaab336e.png#averageHue=%23b5c7d4&clientId=u9aca1641-503c-4&from=paste&height=459&id=u994208b4&originHeight=413&originWidth=856&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=91060&status=done&style=none&taskId=u618503b1-45cc-4edc-bfb9-c8c2e808e92&title=&width=951.1111363069517)
权限信息 由 9 个字符组成，分为三组，分别对应 拥有者, 用户组, 其他人 拥有的权限。
使用`chmod`命令时，可以数字来代表各个权限
```
r:4
w:2
x:1
```
比如`chmod [-R] 770 文件或目录`

很明显，这样修改文件权限是很麻烦的，因此 `chmod` 提供了另一种更好用的方式来修改文件权限,通过 **身份表示符**, **操作表示符** 和 **权限表示符**来实现
```
身份表示符
u	文件的拥有者
g	文件的拥有者所在用户组
o	其他人
a	所有用户

操作表示符
+	添加权限
-	去除权限
=	设定权限

权限表示符
r    读
w    写
x    执行
```
比如`chmod u=rwx,go+x .vimrc`这条指令让拥有者具有所有权限，而为用户组和其他人添加执行权限，需要注意的是： `u=rwx,go+x` 之间没有空格


# 快捷键、Tab键
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687815817523-e86edaca-ad92-4f22-a512-419dee75ae4f.png#averageHue=%23ebedf0&clientId=u9aca1641-503c-4&from=paste&height=960&id=ud470e807&originHeight=864&originWidth=819&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=261956&status=done&style=none&taskId=uc883d6ec-3281-4e26-a6b2-26b43a7d0c6&title=&width=910.0000241067681)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687815884419-e766436f-0ad8-4c9b-9638-644db931378b.png#averageHue=%23eeeff2&clientId=u9aca1641-503c-4&from=paste&height=204&id=u35266277&originHeight=184&originWidth=814&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=46847&status=done&style=none&taskId=uc26fe2f0-e46d-458c-9a7f-60126e5e9e6&title=&width=904.4444684040405)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687816003112-4c900177-bb3a-4c10-8388-72a8e52d6a0e.png#averageHue=%23f3f3f6&clientId=u9aca1641-503c-4&from=paste&height=402&id=u5e41c4b4&originHeight=362&originWidth=853&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=91913&status=done&style=none&taskId=u2e320dcb-a7a9-420e-81be-3f5acbd4bd6&title=&width=947.7778028853153)


# 通配符
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687816552248-ccc2df4e-598f-41a5-ab69-38ab1dcc0097.png#averageHue=%23f2f3f6&clientId=u9aca1641-503c-4&from=paste&height=484&id=u6da62b52&originHeight=436&originWidth=833&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=78160&status=done&style=none&taskId=uebd188ee-a1df-4ff6-af51-b217c1e1f20&title=&width=925.5555800744052)


