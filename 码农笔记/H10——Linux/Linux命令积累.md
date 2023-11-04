
#Linux 
# arch 显示当前主机硬件架构类型
# cd
```shell
cd ..                  返回上一级目录
cd ../..               返回上两级目录
cd或cd ~           		 返回home目录
cd -  								 返回上一次所在的目录
```
     
# wget 下载文件
```bash
#下载单个文件
wget http://www.minjieren.com/wordpress-3.1-zh_CN.zip

#使用wget -O下载并以不同的文件名保存
wget -O wordpress.zip http://www.minjieren.com/download.aspx?id=1080
```

# curl 下载文件、网站交互
wget是个专职的下载利器，简单，专一，极致；而curl可以下载，但是长项不在于下载，而在于模拟提交web数据，POST/GET请求，调试网页，等等。在下载上，也各有所长，wget可以递归，支持断点；而curl支持URL中加入变量，因此可以批量下载。个人用途上，我经常用wget来下载文件，加 -c选项不怕断网；使用curl 来跟网站的API 交互，简便清晰
```bash
# 打开baidu
curl http://www.baidu.com
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688840677662-afd23bb0-593d-4d04-809e-88efd7531b21.png#averageHue=%23140f0b&clientId=u08bc4fcc-dc58-4&from=paste&height=289&id=ua70cbc39&originHeight=260&originWidth=1415&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=52581&status=done&style=none&taskId=u77a7e9a0-ca8a-4645-97bd-b57c213bd7e&title=&width=1572.2222638718888)


# yum、yum源、阿里源
网络 yum 源配置文件位于` /etc/yum.repos.d/ `目录下，文件扩展名为"*.repo"（只要扩展名为 "*.repo" 的文件都是 yum 源的配置文件）
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688838488626-9f93d1c9-9b37-405b-af0b-6e3c5938402c.png#averageHue=%23100c08&clientId=u08bc4fcc-dc58-4&from=paste&height=212&id=u31dcd998&originHeight=191&originWidth=503&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=10206&status=done&style=none&taskId=u39f5f377-bce9-4884-9fc6-6fd01078c2d&title=&width=558.8889036943887)

配置yum源为阿里源
```bash
# Base基础的仓库
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

# epel额外的仓库
wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo

# 清空本地缓存
yum clean all

# 生成新的缓存
yum makecache
```

安装常用的工具
`yum install -y bash-completion vim lrzsz wget expect nettools nc nmap tree dos2unix htop iftop iotop unzip telnet sl psmisc nethogs glances bc ntpdate openldap-devel`

安装tldr
`yum install tldr`

# systemctl 防火墙
一、防火墙的开启、关闭、禁用命令
（1）设置开机启用防火墙：`systemctl enable firewalld.service`
（2）设置开机禁用防火墙：`systemctl disable firewalld.service`
（3）启动防火墙：`systemctl start firewalld`
（4）关闭防火墙：`systemctl stop firewalld`
（5）检查防火墙状态：`systemctl status firewalld`
# which、whereis、whatis、locate、find 查找

- which
用于查找命令文件，能够快速搜索二进制程序所对应的位置。如果我们既不关心同名文件（find与locate），也不关心命令所对应的源代码和帮助文件（whereis），仅仅是想找到命令本身所在的路径，那么这个which命令就太合适了
主要是用来查找系统$PATH 下的可执行文件。说白了就是查找那些我们已经安装好的可以直接执行的命令
which 查找的可执行文件，必须是要在 PATH 下的可执行文件，而不能是没有加入 PATH 的可执行文件，即使他就是可执行文件，但是没有加入到系统搜索路径，他仍然无法被 which 发现
文件名完全匹配、有后缀名也不行、遍历$PATH、找到一个匹配的文件即退出。

- whereis
用来查找二进制（命令）、源文件、man文件。与which不同的是这条命令可以是通过文件索引数据库而非PATH来查找的，所以查找的面比which要广
文件名完全配配、但可有后缀名、遍历包含$PATH的多个目录、找出所有匹配文件

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688600714518-1917b343-819b-4469-b951-cc1ee826444d.png#averageHue=%230c2b34&clientId=u24b53fa3-e1b0-4&from=paste&height=79&id=u6c1a8636&originHeight=79&originWidth=636&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15792&status=done&style=none&taskId=u04a47da4-01c6-4860-8b8b-734247573ce&title=&width=636)

- locate：模糊查询、找目录和文件。locate查找以某字符串结尾的文件或目录：locate *network"。locate在指定目录下查找：`locate：locate "/etc/*network"`
- find：完全匹配（可通过“*YourString*”形式模糊查询）、只找文件（可加-type d找目录）
- whatis：将man手册NAME节区下的那句描述的话打印出来，相当于man -f

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687855852830-bd070fae-4589-459e-976e-e9d953c9f700.png#averageHue=%230f0b08&clientId=u76d18795-c152-4&from=paste&height=97&id=uf5e41c95&originHeight=87&originWidth=458&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&size=5554&status=done&style=none&taskId=udcc712fc-6f8f-4e64-b1b1-7c0bc035429&title=&width=508.888902369841)


# cheat、tldr 查看命令的使用方式
cheat:
[https://mp.weixin.qq.com/s/eAX2Zzno4_al4k7ZXonHjg](https://mp.weixin.qq.com/s/eAX2Zzno4_al4k7ZXonHjg)
man、info 等帮助命令显示的信息太多了，而 cheat 是直奔主题，直接告诉你这个命令怎么用
个命令实在是太强大了，有了它，别说背命令了，基本上你都可以告别百度了，哪个命令不懂的话，只需要 cheat 一下就行
例如：cheat netstat
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688599658454-ff6b1805-4041-4c39-aa1b-7379fc039396.png#averageHue=%23031c23&clientId=ua0785db3-a252-4&from=paste&height=560&id=u54c2d49a&originHeight=560&originWidth=916&originalType=binary&ratio=1&rotation=0&showTitle=false&size=63749&status=done&style=none&taskId=ue0f42d9a-b0b4-48e4-85c5-1f27011a4b8&title=&width=916)

tldr:  即Too Long; Didn’t Read. 太长不看， man curl 的内容就是太长了，我不看
和 cheat 差不多
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688602620767-b706a52e-8735-4121-b13a-5b1a1643d281.png#averageHue=%23021b22&clientId=u2e43bb74-b940-4&from=paste&height=540&id=nuJOL&originHeight=540&originWidth=910&originalType=binary&ratio=1&rotation=0&showTitle=false&size=59178&status=done&style=none&taskId=u2fe2f6d0-5e84-4d14-9e04-6d3a77696ee&title=&width=910)

安装tldr
macos:	`brew install tldr`
Ubuntu:	`apt install tldr`
CentOs:	`yum install tldr`

# vim
`vim a.txt`

查找关键字`:/abcds`  按`n`显示下一个

显示行号`:set nu`，取消行号`:set nonu`
光标移到开始位置`gg`
光标移到结束位置`G`
光标移到第 12 行`输入数字 12，然后按 shift+g`

保存为b.txt  `:w b.txt `
保存并退出 `:wq`
不保存(无论修改与否)， 强制退出`:q! `
