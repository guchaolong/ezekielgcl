
参考：[Centos部署biliup自动录播程序|分享即记忆](https://blog.waitsaber.org/archives/163)


录制主播视频上传B站

自动检测主播是否开播，开播之后，脚本会自动录制，等主播下播之后，它会自动把视频文件上传到 B 站，全程都是自动化的，无需人为操作

什么是Biliup？  
Biliup是支持自动录制各大直播平台实时流，自动上传到bilibili。也支持twitch直播回放列表自动搬运至b站。

# 准备
创建整个项目的目录
```
mkdir biliup
cd biliup
```

# 第一步：安装 python


先安装一些工具：
```
yum install -y vim wget tftp lrzsz bzip2 zip unzip net-tools bind-utils traceroute tcpdump telnet tree mlocate bash-completion rsync readline readline-devel gdisk
```

编译安装需要的包：
```
yum install -y make.x86_64 gcc gcc-c++ zlib zlib-devel openssl-devel
```

安装 Python 的步骤：
1. 下载源码包：
```
#下载源码包
wget https://www.python.org/ftp/python/3.9.10/Python-3.9.10.tgz

 #解压源码包
tar -xvf Python-3.9.10.tgz
```

2. 编译并安装：
```
 #进入解压出来的文件夹
cd Python-3.9.10

#设置安装目录并进行编译后安装
./configure --prefix=/usr/local/python3 && make && make install﻿​


```

3. 配置环境变量：
```
#更新全局环境

echo "export PATH=\$PATH:/usr/local/python3/bin" >> /etc/bashrc && source /etc/bashrc
```

4. 创建软连接并验证
```
#删除原有的python3软连接
rm -rf /usr/bin/python3 

#创建python3软连接
ln -s /usr/local/python3/bin/python3 /usr/bin/python3

#验证python3软连接是否正常创建，正常会返回安装的版本信息
python3 -V

#删除原有的pip3软连接
rm -rf /usr/bin/pip3

#创建pip3软连接
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3

#验证pip3软连接是否正常创建，正常创建会返回pip版本与关联的python版本信息
pip3 -V
```


# 第二步：安装 ffmpeg
[[01-ffmpeg + 脚本实现 24小时不间断视频直播推流#执行脚本]]


# 第三步： nodejs
`yum install nodejs`


# 第四步： 安装 biliup
>两种方式：pip快速安装、源码安装
>本次选择 pip 安装

`pip3 install biliup`

创建 config.yaml文件
然后执行 biliup start的时候出错：
ModuleNotFoundError: No module named '\_ctypes'

其实是 Python 没有成功安装

解决办法:
```
#安装libffi-devel
yum install libffi-devel

#然后重新进到 Python 解压包
cd Python-3.9.10/

#重新编译 创建软连接并验证
make & make install
```


# 使用 biliup


```
# 进到项目目录
cd biliup
```

创建配置文件 config.toml
```yaml

```


```
# 在创建配置文件的目录启动 biliup
$ biliup start

# 退出
$ biliup stop

# 重启
$ biliup restart

# 查看版本
$ biliup --version

# 显示帮助以查看更多选项
$ biliup -h

# 带 web-ui 启动 biliup。
# 默认监听 0.0.0.0:19159。可使用-H及-P选项配置。
# 考虑到安全性，建议指定本地地址配合web server或者添加验证。
$ biliup --http start

# 指定配置文件路径
$ biliup --config ./config.yaml start
```

使用`biliup start`启动

Linux下以daemon进程启动，录像和日志文件保存在执行目录下，程序执行过程可查看日志文件。启动之后使用命令`ps -A | grep biliup` 查看进程biliup是否启动成功

怎么看有没有开始录制，输入`ls`就能够看到相关文件了

# 上传 B 站
biliup-rs 是一个B站命令行投稿工具

下载biliupR-v0.1.19-x86_64-linux.tar.xz

上传到服务器
`scp /Users/ezekiel/Downloads/biliupR-v0.1.19-x86_64-linux.tar.xz root@120.24.58.36:/root/biliup`

```
tar -xvf biliupR-v0.1.15-x86_64-linux.tar.xz

cd biliupR-v0.1.15-x86_64-linux/

./biliup login
选择扫码登录，之后就会生成 cookies.json文件，复制一份cookies.json到 config.toml相同目录

```

