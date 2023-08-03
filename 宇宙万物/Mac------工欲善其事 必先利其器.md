> 新入手一台MacBook Pro（Apple M1 Pro芯片）
> 记录软件安装和开发环境搭建的过程

# 一、触控板手势：
## 一个桌面打开了多个窗口的情况
把这些窗口都推到角落（隐藏掉）/重新显示：4指横行张开/收拢

# 二、快捷键
## 显示隐藏文件
`comand + shift + .`
## 进入当前应用的Preference
`command + ,`
## 访达里显示文件路径
`option + command + p`

## F1～F12
安装snipaste的时候都试了一遍
默认情况下，F1-F12不作为功能键，而是其他功能，通过键上的小图标就知道是什么功能，以我的mac为例
F1 F2调节屏幕亮度，F3调度中心，F4聚焦搜索，F5听写功能，可以把你说的话转成文字，F6勿扰模式，F789播放功能，F10 11 12音量
> 以前的F456分别是F4启动台，F56调节键盘背光


偏好设置-键盘-勾选F1 F2等作为功能键
偏好设置-键盘-听写 -双击fn

这样之前的调节功能就需要fn + F123... 
听写功能则是双击fn

---

## keychron k3键盘蓝牙自动休眠
fn + s + o
## 切换桌面
`ctrl + <`    或 `ctrl + >`


# 三、设置、操作、技巧相关
## 开关机 充电
不要关机
外出用电池，家里充电，以保持电池电流的流动状态

## 文件已损坏，请移到废纸篓
item2
输入：`sudo xattr -r -d com.apple.quarantine ` （后面有个空格）
然后再把对应的应用程序拖到终端界面里
回车
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688437582353-5fda1059-a96e-4405-8249-3d35e74a8f8b.png#averageHue=%236a844c&clientId=u210129e2-2508-4&from=paste&height=448&id=u8f0c7ac2&originHeight=448&originWidth=1708&originalType=binary&ratio=1&rotation=0&showTitle=false&size=357703&status=done&style=none&taskId=u43d387e8-5eab-470d-b5fc-d823dd76240&title=&width=1708)

## 浏览器地址栏快速搜索
地址栏直接 bd + 空格或 g + 空格，再输入要搜的内容
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689200062020-9da9ca1c-e414-42bc-9aa5-505db0d02d6c.png#averageHue=%23fefefe&clientId=ufaa9a811-599e-4&from=paste&height=147&id=ud9b74821&originHeight=294&originWidth=737&originalType=binary&ratio=2&rotation=0&showTitle=false&size=20305&status=done&style=none&taskId=ucd4694dd-2e7a-40cc-a4a3-163090581c3&title=&width=368.5)

# 
# 四、Mac设备
## 内存
> 发现 mac 内存占用特别严重，idea就占 4G 以上
> 网上查一下，很多人都有这种情况，大概就是 M1  使用交换内存机制 ，CPU 压缩内存到硬盘，再从硬盘取回数据，SSD 有写入容量限制，一旦达到最大写入容量，SSD 就废了，因为 ssd和主板焊在一起的，所以就全套板子废了

事实上，使用 OS X/linux 等类 Unix 操作系统时，是不需要担心内存占用太多的，因为内存就是要充分使用的。
当你有少量 free 内存，大量 inactive 内存时，表明此时系统运行在最佳状态，反而在刚开机时大量 free 时会比较慢。
只有当 free 和 inactive 都很少时才说明内存不够用了。但事实上，得益于 SSD 和 M1 MAX 的强大，即使 CPU 压缩内存到硬盘，再从硬盘取回数据，这之间的时间间隔也非常小，用户几乎很难察觉出来，所以 MAC 用户无需担心内存使用问题.
尝试过将 CPU 和内存拉满，但即使这样，系统 UI 也没出现明显卡顿.
得益于 OS X 系统采用了 Unified Buffer Cache，MAC 的空闲内存会被用来加速文件访问。即上图中的压缩内存.
在日常使用中，可以做到随时开随用，流畅无卡顿.
参考： [https://lanyundev.com/posts/50102](https://lanyundev.com/posts/50102)

## 磁盘
> 之前苹果被爆出磁盘大量读写的消息，M1的MacBook Pro被爆两个月就100多T出去了
> 然后就有很多人急着去看自己的磁盘读写，这个和磁盘寿命有关


磁盘大量读写的主要原因：swap交换内存（或者也可以理解为虚拟内存？）
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689196234922-ffc12e32-44d0-4fbf-aeb8-4b23f57b85a5.png#averageHue=%23e9d5d1&clientId=u39430a84-2d39-4&from=paste&height=502&id=kuxVy&originHeight=522&originWidth=741&originalType=binary&ratio=2&rotation=0&showTitle=false&size=150898&status=done&style=none&taskId=ued31031a-496e-4026-9c57-9e58de0f98b&title=&width=712.5)

通常由系统自己定义 swap 空间的大小，用磁盘来模拟内存的行为，
如果没有 swap，打开多个程序的时候，物理内存可能就不够用了

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689196553478-6e2cee36-f028-43e2-addb-14e45d9e6359.png#averageHue=%23f2f2f2&clientId=u39430a84-2d39-4&from=paste&height=127&id=NTc1p&originHeight=103&originWidth=617&originalType=binary&ratio=2&rotation=0&showTitle=false&size=17598&status=done&style=none&taskId=uabb291b6-c869-4f3e-a4a5-6a3bbd0806f&title=&width=762.5)
当物理内存不够时，就会使用到 swap 内存
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689196850733-13c707e5-7fc9-4c36-b733-d480d7c7b78c.png#averageHue=%23b5b9b1&clientId=u39430a84-2d39-4&from=paste&height=142&id=F551l&originHeight=284&originWidth=1107&originalType=binary&ratio=2&rotation=0&showTitle=false&size=128900&status=done&style=none&taskId=uf1823807-6902-4303-8038-d850dd48288&title=&width=553.5)
这样的话，还是能打开多个程序

检查 mac 的 SSD 健康状况：
关于本机 更多 系统报告 硬件 储存，如果状态显示已验证，说明 ssd 没有严重问题
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689191929252-4644afd9-fb13-4959-9eda-735dfb91b3ae.png#averageHue=%23e2e2e2&clientId=u39430a84-2d39-4&from=paste&height=438&id=d5PsL&originHeight=876&originWidth=1324&originalType=binary&ratio=2&rotation=0&showTitle=false&size=208028&status=done&style=none&taskId=uda581a70-ce99-4790-a92c-3a7f87a4320&title=&width=662)

更多 ssd 健康状况，使用工具smartmontools
brew install smartmontools
查看磁盘读写情况：smartctl -a disk0
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689195276201-e3548baf-400b-4867-81c4-dd1a623fa1a2.png#averageHue=%23081d25&clientId=u39430a84-2d39-4&from=paste&height=415&id=eP5e3&originHeight=829&originWidth=857&originalType=binary&ratio=2&rotation=0&showTitle=false&size=181625&status=done&style=none&taskId=ubb6957ca-79ac-4b7d-a3fa-6dc0a802de9&title=&width=428.5)
剩余寿命，简单看Percentage Used是多少就行，这个值越高说明寿命不行了，我的是 0，nice! 

macos下的容器、宗卷、分区
[https://blog.csdn.net/weixin_39011825/article/details/129027591](https://blog.csdn.net/weixin_39011825/article/details/129027591)
# 五、软件、工具
## cleanmymac x
订单号：
230323030144653110
商品名称：
CleanMyMac X Chinese【1年订阅版 + Mac】
注册码
id993031005328uks

## office 365
淘宝9.9元买的账号
卡号：t301@xxsvip.top 原密码：Paw74903 新密码：zeKino001
[https://www.yuque.com/docs/share/adefb839-4f11-4a2c-b5fb-e7239ee32dd5?#](https://www.yuque.com/docs/share/adefb839-4f11-4a2c-b5fb-e7239ee32dd5?#)《mac  ipad  手机 点开链接教程就会操作了  先看教程 》

## Alfred5
[https://qiujunya.com/article/2019/6/25/29.html](https://qiujunya.com/article/2019/6/25/29.html)
下载安装后，刚开始也是“不信任...打不开”，过了一会，就突然可以了
安装包：Alfred_5.0.4_(2093)_[TNT].dmg（已上传到网盘）
clipboard history默认快捷键是  `option + command + c`
改成：`option + c`

## snipaste
刚开始发现F1不起作用，原来是因为mac默认情况下，F1～FN的作用是调节屏幕亮度，音量等。
默认F1～FN是没有开启作为功能键的，所以需要fn + F1这种才会作为功能键
可以偏好设置-键盘-勾选将F1 F2等作为功能键

## xnip
长截图

## Bob
翻译工具


## OmniGraffle
账户名：guclno1zekiel
psw: 30GMCAndT8QLLY&Y
邮箱：guclno1@163.com
许可证：
Owner: Coffee
Lic Key: CRMP-NYCD-VKSG-GAGM-XNKK-BCPX-NKK
Owner: Espresso
Lic Key: LBGA-IVTE-QXTD-SMDM-QMRX-YDXQ-MRX

## others
CheatSheet 查看快捷键，长按 command
键指如飞 快速查看快捷键，双击 command键

## Adobe Pr Ps
[https://www.yuque.com/qingcaimantou/spseir/sr440e?#](https://www.yuque.com/qingcaimantou/spseir/sr440e?#)
[https://www.yuque.com/qingcaimantou/rrfkiw/lk0xf9?#](https://www.yuque.com/qingcaimantou/rrfkiw/lk0xf9?#)
## IDEA
完全卸载idea，依次执行下面4条命令，就可以重新安装了
```shell
 
rm -rf ~/Library/Logs/JetBrains/IntelliJIdea*
 
rm -rf ~/Library/Application\ Support/JetBrains/IntelliJIdea*
 
rm -rf ~/Library/Caches/JetBrains/IntelliJIdea*
 
rm -rf ~/Library/Preferences/jetbrains.idea*
```
idea历史版本下载：[https://www.jetbrains.com/idea/download/other.html](https://www.jetbrains.com/idea/download/other.html)
两种方式：无限重置30天试用（老版本）、一次性激活（新版本）[http://qiheo.com/zhishi/505.html](http://qiheo.com/zhishi/505.html)
本次采用最新版，永久激活方式
破解补丁为：/Users/ezekiel/ToolPkg/ja-netfilter/ja-netfilter.jar   （ja-netfilter文件夹里其他文件也要有）
其他方式[http://blog.mxnzp.com/?p=174](http://blog.mxnzp.com/?p=174)


IDEA 全局查找 shift + command + f 总是会同时弹出 mac 访达的搜索页面
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689112962505-0c427ae6-4479-431d-bc5a-48596c0b7ead.png#averageHue=%23e7e7e7&clientId=u8e488e16-37dd-4&from=paste&height=250&id=u0147cccf&originHeight=500&originWidth=1479&originalType=binary&ratio=2&rotation=0&showTitle=false&size=102943&status=done&style=none&taskId=u3364f0ce-72ca-4922-ae4a-c28920b270d&title=&width=739.5)
解决方法，关闭 mac 自己的快捷键，取消勾选
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689113071717-ea3df0ab-b83f-42f9-97e6-0c90f21218a1.png#averageHue=%23efefef&clientId=u8e488e16-37dd-4&from=paste&height=202&id=uf08542c4&originHeight=404&originWidth=670&originalType=binary&ratio=2&rotation=0&showTitle=false&size=66409&status=done&style=none&taskId=ud5a1efe9-468c-47d8-9a45-d5865271cb9&title=&width=335)

## DataGrip
最新版，激活方式同IDEA，但是激活码不同，我使用的激活码是[DataGrip 2022.3.1 破解教程_激活码](https://www.quanxiaoha.com/datagrip-pojie/datagrip-pojie.html)中的激活码

## Bob翻译
可以使用有道翻译、Google 翻译等
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1688638424319-82479603-d76e-4bc0-ad40-0260b9038875.png#averageHue=%23e4e1da&clientId=uc9b581d3-94c4-4&from=paste&height=185&id=ub50813db&originHeight=370&originWidth=963&originalType=binary&ratio=2&rotation=0&showTitle=false&size=69979&status=done&style=none&taskId=u34e167d2-762f-4b27-8464-96592ddedb2&title=&width=481.5)
有道 key 和密钥：
[https://ai.youdao.com/console/#/app-overview](https://ai.youdao.com/console/#/app-overview)
Bob配置方法：
[https://bobtranslate.com/service/translate/youdao.html](https://bobtranslate.com/service/translate/youdao.html)

## **terminal shell zsh bash区别**
**terminal**:提供一个**命令的输入输出**环境
**shell**：linux内核的外壳，负责外界与内核交互，本质就是命令解释器，bash、zsh这些都是shell，都是解释器
查看系统装了哪些shell:	   `cat /etc/shells`
查看当前使用的是哪个shell
```shell
echo $SHELL
或者
echo $0

切换到bash
chsh -s /bin/bash

切换到zsh
chsh -s /bin/zsh
```

打开termianl时，操作系统就会将terminal和shell关联起来，terminal中输入命令后，shell就负责解释命令
**console**: 记录机器重要日志的地方，一台电脑有且只有一个console,但可以有多个terminal, 举个列子：电视机的一个区域有开机 调音量等按钮，这个区域就可以当做console,遥控器就是terminal, 可以有多个

## ll命令
mac没有ll命令：
```shell
vim ~/.bash_profile

添加内容
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF

source ~/.bash_profile
```
## git
`git -v`
> 显示git version 2.37.1 (Apple Git-137.1)

`brew install git`
`git -v`
> 显示git version 2.39.0

`brew install git-gui`
`git config --global user.name "guchaolong"`
`git config --global user.email "guclno1@qq.com"`

配置ssh
```shell
#进入～/.ssh文件夹，如果没有，则mkdir创建文件夹
cd ~/.ssh

#创建密钥，然后问价下会生成两个东西
ssh-keygen -t rsa -C guclno1@qq.com

#打开id_rsa.pub文件，复制里面的内容，贴到github里
```
## Homebrew
Homebrew是一款Mac OS平台下的**软件包管理**工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷
[M1芯片Mac上Homebrew安装教程](https://zhuanlan.zhihu.com/p/341831809)
1 安装命令
```shell
/bin/bash -c "$(curl -fsSL https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)"
```

2 设置Homebrew 到 PATH 中
```shell
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
3 验证：
```shell
brew -v
brew install tree
```
4 切换到bash后，提示-bash: brew: command not found，执行：
```shell
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.bash_profile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
5 [Homebrew更换国内镜像源（中科大、阿里、清华）](https://blog.csdn.net/xiewanchen0708/article/details/128232697)
brew安装完成后，brew-cask也会随着自动安装，并不需要手动重新安装brew-cask

6 使用
```shell
brew update              # 更新brew软件自身

brew list                # 列出本机通过brew安装的所有软件
brew list --cask				 # 列出本机按照过的软件列表
brew info name           # 显示软件信息：版本，大小，地址..
brew search name         # 搜索软件
brew home 应用名					 # 打开应用的官网

brew install name        # 将name的源码编译并安装
brew uninstall name      # 卸载软件

brew outdated						 # 检查一下可更新的应用有哪些
brew upgrade name        # 更新安装过的软件,如果不加软件名，就更新所有可以更新的软件

brew cleanup -n					 # 看看有哪些应用可以清理，但暂时不需要处理它们
brew cleanup 应用名			 # 指定需要清理缓存的应用
brew cleanup             # 清把应用的旧版本和缓存删除


```

7 防止 Homebrew 自动升级和自动清理过期程序
```shell
export HOMEBREW_NO_AUTO_UPDATE=TRUE     防止Homebrew 擅自升级所有软件
export HOMEBREW_NO_INSTALL_CLEANU=TRUE  防止自动清理

把两行添加的.zprofile和.bash_profile
```

## Node.js
> nodejs和npm的关系
> 
> node.js是javascript的一种运行环境，是对Google V8引擎进行的封装，是一个服务器端的javascript的解释器。
> npm是nodejs的包管理器（package manager）。
> nodejs和npm是包含关系，nodejs中含有npm，安装好nodejs，cmd输入npm -v会发现npm的版本号，说明npm已经安装好。
> 
> 引用大神的总结:
> 其实我们在Node.js上开发时，会用到很多别人已经写好的javascript代码，如果每当我们需要别人的代码时，都根据名字搜索一下，下载源码，解压，再使用，会非常麻烦。于是就出现了包管理器npm。大家把自己写好的源码上传到npm官网上，如果要用某个或某些个，直接通过npm安装就可以了，不用管那个源码在哪里。并且如果我们要使用模块A，而模块A又依赖模块B，模块B又依赖模块C和D，此时npm会根据依赖关系，把所有依赖的包都下载下来并且管理起来。试想如果这些工作全靠我们自己去完成会多么麻烦！


安装 PicGo的插件的时候，提示要安装Node.js
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689020384552-5bb75905-9059-4c15-a687-cf484c3d2d23.png#averageHue=%23485355&clientId=u26f183a4-b78d-4&from=paste&height=343&id=u0efea8fc&originHeight=343&originWidth=746&originalType=binary&ratio=1&rotation=0&showTitle=false&size=73271&status=done&style=none&taskId=u41f22992-c8b8-4174-82a9-b77a3d564cf&title=&width=746)

先查看有没有装过
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689020467035-c87e7873-d748-4e5c-b87e-774f993dd1bf.png#averageHue=%2309262f&clientId=u26f183a4-b78d-4&from=paste&height=72&id=ucb78889b&originHeight=72&originWidth=746&originalType=binary&ratio=1&rotation=0&showTitle=false&size=13929&status=done&style=none&taskId=u86e0b391-0c9f-4035-ad30-7fadbec44a8&title=&width=746)

然后用 homebrew安装	
`brew install node`

验证：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689020614521-ad32e344-691c-4462-a176-3aac0f4da18a.png#averageHue=%2306242d&clientId=u26f183a4-b78d-4&from=paste&height=114&id=u71446d7a&originHeight=114&originWidth=926&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19818&status=done&style=none&taskId=ua299ac75-2dd8-4067-870a-9f2027aef07&title=&width=926)

## item2 + oh-my-zsh
**步骤1 安装item2、brew、git**
[https://iterm2.com/](https://iterm2.com/)  安装item2的时候会提示安装**pip3工具,点击安装**

item2界面：
![截屏2023-01-04 00.23.59.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672763060627-b1063b81-bd30-4dcb-a0f2-43fd08f32f76.png#averageHue=%23121212&clientId=uecf1408a-192f-4&from=drop&id=ucb825a8d&originHeight=1148&originWidth=2348&originalType=binary&ratio=1&rotation=0&showTitle=false&size=463255&status=done&style=none&taskId=u4407c794-1d0f-4ab0-ab73-f7d6b88ba28&title=)

**步骤2 安装oh-my-zsh**
```shell
#可能出现连接被拒绝，解决办法是配置host ip
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
安装完成后界面：
![截屏2023-01-04 01.01.47.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672765319431-002ec4d5-6ad1-4ff7-9cd8-a65816e03b86.png#averageHue=%230c0c0c&clientId=uecf1408a-192f-4&from=drop&id=u0b1f261e&originHeight=1378&originWidth=2666&originalType=binary&ratio=1&rotation=0&showTitle=false&size=500207&status=done&style=none&taskId=u9d6cfc56-fa77-4448-b805-dd49f1084f2&title=)
Using the Oh My Zsh template file and adding it to ~/.zshrc.
有了`~/.zshrc`文件还有`.oh-my-zsh`文件夹
`.zshrc`是on-my-zsh的配置文件，可以修改里面的配置从而修改不同的**字体**、**配色**等
> .zshrc_origin是我备份的,即最初的文件

```shell
#查看oh-my-zsh下的所有themes，默认是ZSH_THEME="robbyrussell"
ls .oh-my-zsh/themes
```

**步骤3 安装PowerLine**
```shell
pip3 install powerline-status --user
```
![截屏2023-01-04 02.06.15.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672769183399-02dda906-04fb-4180-8922-0b6de00a8865.png#averageHue=%230b0b0b&clientId=uecf1408a-192f-4&from=drop&id=u0d7af75c&originHeight=586&originWidth=2522&originalType=binary&ratio=1&rotation=0&showTitle=false&size=182618&status=done&style=none&taskId=u4ae49571-b3d4-4b05-bfac-f7df564fea3&title=)
上图中的黄色提示内容//todo

**步骤4 安装PowerFonts字体**
安装前omz的字体：
![截屏2023-01-04 02.37.49.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672771081571-8c41d3d4-97fd-4bdf-957b-b6af05f5e18c.png#averageHue=%23b7b7b7&clientId=uecf1408a-192f-4&from=drop&id=uc28562a3&originHeight=1438&originWidth=1982&originalType=binary&ratio=1&rotation=0&showTitle=false&size=567043&status=done&style=none&taskId=ub9a05da9-611f-48b4-b414-4dde1c7410b&title=)

```shell
mkdir ~/Source
cd Source
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
```
提示：
Copying fonts...
Powerline fonts installed to /Users/ezekiel/Library/Fonts

omz的字体也多了
![截屏2023-01-04 02.45.47.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672771558146-b9fa2df5-dec4-433b-8674-016963065f12.png#averageHue=%23d0d0d0&clientId=uecf1408a-192f-4&from=drop&id=u71d1f71c&originHeight=1156&originWidth=1834&originalType=binary&ratio=1&rotation=0&showTitle=false&size=355052&status=done&style=none&taskId=u8b5fdc0f-d25c-4a95-8133-bee89cbe42b&title=)**

步骤5 安装配色方案**
```shell
#切换到~/Rource
git clone https://github.com/altercation/solarized

solarized/iterm2-colors-solarized/
open .
#然后双击就可以把两张配色安装到item

```
![截屏2023-01-04 03.20.58.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672773666358-e05cf214-72f6-48bd-8306-268cf9d425e0.png#averageHue=%23c1c3c2&clientId=uecf1408a-192f-4&from=drop&id=u94ec9bed&originHeight=752&originWidth=486&originalType=binary&ratio=1&rotation=0&showTitle=false&size=152041&status=done&style=none&taskId=u45ef876a-a6f3-4b5b-a2ae-55ca1f82c15&title=)
**步骤6 安装agnoster-fcamblor主题**
```shell
cd Source
git clone https://github.com/fcamblor/oh-my-zsh-agnoster-fcamblor.git
cd oh-my-zsh-agnoster-fcamblor

#主题拷贝到oh my zsh的themes中
./install
```
![截屏2023-01-04 03.26.53.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672774018584-04d508c8-7204-4b0a-90fb-4f32b3f4aaed.png#averageHue=%23070707&clientId=uecf1408a-192f-4&from=drop&id=u54589319&originHeight=634&originWidth=1454&originalType=binary&ratio=1&rotation=0&showTitle=false&size=122238&status=done&style=none&taskId=u6eae9865-85db-435d-b529-f47fc74ec68&title=)

之前：
![截屏2023-01-04 03.28.26.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672774113646-c87f9598-2f80-4e7c-a890-447b7398b40c.png#averageHue=%230e0e0e&clientId=uecf1408a-192f-4&from=drop&id=u08d5f231&originHeight=548&originWidth=924&originalType=binary&ratio=1&rotation=0&showTitle=false&size=97236&status=done&style=none&taskId=uf2ae113d-c71b-46ac-ba20-05259cb8a25&title=)
之后：
![截屏2023-01-04 03.29.27.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672774192268-5d3748ef-d46f-4220-a511-c5fe618e1ccf.png#averageHue=%230e0e0d&clientId=uecf1408a-192f-4&from=ui&id=u9b947a80&originHeight=416&originWidth=790&originalType=binary&ratio=1&rotation=0&showTitle=false&size=70569&status=done&style=none&taskId=u5139bb8f-0c75-4f05-8037-b97db6b537a&title=)

**步骤7 在～/.zshrc配置agnoster主题**
```shell
vim .zshrc
#ZSH_THEME="agnoster"
source .zshrc
```
![截屏2023-01-04 03.38.01.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672774689078-0b9712a3-3709-4102-81be-cea5d0646db4.png#averageHue=%23213b46&clientId=uecf1408a-192f-4&from=drop&id=u0216461a&originHeight=914&originWidth=1294&originalType=binary&ratio=1&rotation=0&showTitle=false&size=232751&status=done&style=none&taskId=ue23c756b-6c52-4e1c-a693-218d7b3dd05&title=)
这个agnoster主题要配合之前安装的字体才能正常显示，如果是默认字体Monaco,就会出现乱码![截屏2023-01-04 03.40.22.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672774827749-04048ded-fc04-44af-9fd3-bd96b2bae18c.png#averageHue=%230b0b0b&clientId=uecf1408a-192f-4&from=drop&id=u8a697f71&originHeight=264&originWidth=952&originalType=binary&ratio=1&rotation=0&showTitle=false&size=51609&status=done&style=none&taskId=u3222adc2-6797-4ddf-9b27-3184f2f5866&title=)

**步骤8 配置高亮插件**
```shell
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
vi ~/.zshrc
#在git后面加上 zsh-syntax-highlighting
#在最后一行加上 source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source ~/.zshrc
```
**步骤9 安装命令建议和补全插件**
```shell
cd ~/.oh-my-zsh/custom/plugins/
git clone https://github.com/zsh-users/zsh-autosuggestions
vi ~/.zshrc
#找到plugins，git后面加上zsh-autosuggestions这个插件即可
source ~/.zshrc
```
> 添加web-search插件，输入`baidu adfsdf`就会打开百度，搜索关键词adfsdf

![截屏2023-01-04 04.16.04.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672777017868-635a09a5-afca-44db-8c51-27cb8eb9c488.png#averageHue=%23214152&clientId=uecf1408a-192f-4&from=ui&id=u5ffde1d2&originHeight=248&originWidth=1506&originalType=binary&ratio=1&rotation=0&showTitle=false&size=119759&status=done&style=none&taskId=uae598c66-e080-417b-9269-3f8dde41b02&title=)
补全命令的字体不太清晰，与背景颜色太过相近，其实可以自己调整一下字体颜色
Preferences -> Profiles -> Colors 中有Foreground是标准字体颜色，ANSI Colors中Bright的第一个是补全的字体颜色
![截屏2023-01-04 04.24.31.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672777474572-c69e2865-1c56-4702-99d5-eac2ec7506e5.png#averageHue=%231c3641&clientId=uecf1408a-192f-4&from=drop&id=u16e55441&originHeight=228&originWidth=1356&originalType=binary&ratio=1&rotation=0&showTitle=false&size=93010&status=done&style=none&taskId=u8279e6d0-1b76-4575-a6a6-78db7ce1a68&title=)
默认
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689260373311-1e93b63c-a15a-4e4a-afec-adb5cce70b91.png#averageHue=%2396957f&clientId=ube03873b-6676-4&from=paste&height=408&id=uc66d7a53&originHeight=605&originWidth=1024&originalType=binary&ratio=2&rotation=0&showTitle=false&size=295881&status=done&style=none&taskId=ub1adedfa-2b64-4975-a304-955777a814e&title=&width=690)


**步骤10 设置快捷键，快速调出item2**
![截屏2023-01-04 05.46.02.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672782388856-5c29603c-8af8-4f36-80d9-b29593f33ba8.png#averageHue=%23dfdede&clientId=uecf1408a-192f-4&from=ui&id=u6cb4fbd5&originHeight=934&originWidth=1180&originalType=binary&ratio=1&rotation=0&showTitle=false&size=226980&status=done&style=none&taskId=u10b955e4-af45-427c-a856-ef4926e5e80&title=)


![截屏2023-01-04 05.44.04.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672782285272-d2024526-2c0c-4dd2-aa10-50f0c1a6bfc4.png#averageHue=%23e9a296&clientId=uecf1408a-192f-4&from=ui&id=uad25eee8&originHeight=810&originWidth=1904&originalType=binary&ratio=1&rotation=0&showTitle=false&size=207260&status=done&style=none&taskId=ud1e79c63-1248-479f-99c3-633a1d7964a&title=)


![截屏2023-01-04 05.45.02.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672782334003-687c6cd6-bf89-42d7-af99-783b2f02c838.png#averageHue=%23f3f2f2&clientId=uecf1408a-192f-4&from=ui&id=u5f55cea4&originHeight=666&originWidth=1088&originalType=binary&ratio=1&rotation=0&showTitle=false&size=129501&status=done&style=none&taskId=udbeaf44b-e3e1-4410-9166-9a07a85ab13&title=)

点command + return就会出现

## jdk
jdk是安装在/Library/Java/JavaVirtualMachines下
安装前，/Library/Java/JavaVirtualMachines路径下啥都没有
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672920182564-dd4ec23a-145b-4e5f-8744-33a415800e94.png#averageHue=%230a2027&clientId=u21cf0cbf-b0db-4&from=paste&height=174&id=ua867f295&originHeight=224&originWidth=902&originalType=binary&ratio=1&rotation=0&showTitle=false&size=30087&status=done&style=none&taskId=ub15f1360-8583-41cc-ac98-a00d9f12902&title=&width=699)
m1芯片使用的是arm架构，而目前Oracle还没有推出适配Mac的arm架构的jdk，所以我选择安装Aule的ARM架构的JDK，官网[https://www.azul.com/downloads/?version=java-8-lts&os=macos&architecture=arm-64-bit&package=jdk](https://www.azul.com/downloads/?version=java-8-lts&os=macos&architecture=arm-64-bit&package=jdk)下载安装后，前面的路径下就有了
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672920392290-46f788a8-99c6-41d3-b0e1-3e78551c72c4.png#averageHue=%23071b20&clientId=u21cf0cbf-b0db-4&from=paste&height=209&id=u2ede81e2&originHeight=418&originWidth=1320&originalType=binary&ratio=1&rotation=0&showTitle=false&size=51706&status=done&style=none&taskId=u35c9a0f6-6d4e-4fab-8be9-56aa8b410a5&title=&width=660)
这个选择 .dmg 格式的 jdk 下载，然后直接安装就好了，这个**会自动配置好环境变量**，**不需要自己配置**
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672921089633-144b0b5e-50c2-4913-b6e6-8a9efe3115e4.png#averageHue=%23113140&clientId=u21cf0cbf-b0db-4&from=paste&height=99&id=u9516a71b&originHeight=198&originWidth=1778&originalType=binary&ratio=1&rotation=0&showTitle=false&size=83751&status=done&style=none&taskId=uf82c2ecf-5c0e-4cf3-982b-45206ceb54a&title=&width=889)

> 但是我自己配了一下
> `~/.zshrc`文件后面加上两行,然后`source ~/.zshrc`让配置文件生效
> export JAVA_HOME=/Library/Java/JavaVirtualMachines/zulu-8.jdk/Contents/Home
> export PATH=$JAVA_HOME/bin:$PATH

再查看环境变量：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672922265939-bd0236da-6b41-4087-bb60-439ec2c33348.png#averageHue=%23142a32&clientId=u21cf0cbf-b0db-4&from=paste&height=145&id=ub85f4248&originHeight=290&originWidth=3424&originalType=binary&ratio=1&rotation=0&showTitle=false&size=498001&status=done&style=none&taskId=uffca2da9-860d-45fc-9c43-3cb2d667fce&title=&width=1712)
> JDK1.5之后不用再设置classpath了



## maven
官网下载，解压到/Users/ezekiel/DevTool/apache-maven-3.8.7
配置环境变量
```shell
vim ~/.zshrc
#加上两行
export M2_HOME=/Users/ezekiel/DevTool/apache-maven-3.8.7
export PATH=$PATH:$M2_HOME/bin
source ~/.zshrc
mvn -v
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672925929430-4519af8d-7072-48fc-ac5f-41b4b642d52b.png#averageHue=%230c2026&clientId=u21cf0cbf-b0db-4&from=paste&height=146&id=u5f278058&originHeight=292&originWidth=2166&originalType=binary&ratio=1&rotation=0&showTitle=false&size=92810&status=done&style=none&taskId=u46e7e5dd-1799-440b-b54d-58400447c03&title=&width=1083)
查看环境变量
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672926205847-7dd91a14-7a9f-4c94-a6fb-3cc5599c0751.png#averageHue=%23162c33&clientId=u21cf0cbf-b0db-4&from=paste&height=161&id=u42e9c2ba&originHeight=322&originWidth=3416&originalType=binary&ratio=1&rotation=0&showTitle=false&size=597697&status=done&style=none&taskId=ufd1180c3-7d4f-412e-80b9-aa88bb70e53&title=&width=1708)
配置阿里云镜像和本地repository，配置IDEA maven

## gradle
下载-解压
`./zshrc`配置环境变量，加上
```shell
export GRADLE_HOME=/Users/ezekiel/DevTool/gradle-7.6
export GRADLE_USER_HOME=/Users/ezekiel/DevTool/gradle-repository
export PATH=$PATH:$GRADLE_HOME/bin
```
`source ~/.zshrc`
`gradle -v`
安装的是Gradle 7.6!   有些方法已经被摒弃
compile、runtime、testCompile 和testRuntime 配置自Gradle 4.10以来已被弃用，最终在Gradle7
上述配置应分别替换为implementation、runtimeOnly、testImplementation和testRuntimeOnly

**GRADLE_USER_HOME和Gradle user home的区别**

## VSCODE
打开命令控制台
> `command + shift + p `
> 就会显示vscode的一些功能，最近使用的排在前面

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1672996010776-550a29a2-7796-4d39-a292-4516195e7697.png#averageHue=%230f4469&clientId=u29e50739-4c1a-4&from=paste&height=177&id=ub27a18bb&originHeight=177&originWidth=667&originalType=binary&ratio=1&rotation=0&showTitle=false&size=23314&status=done&style=none&taskId=u35634fe7-6ed9-4937-a0d9-ea681ab9be2&title=&width=667)

vscode切换中英文
> `command + shift + p`
> 选择，然后选择对应语言


新建文件，并选择文件类型
> 新建：`command + n`
> 选择文件类型
> 方式1：`command + shift + p` 打开命令控制台，选择“更改语言模式” change language mode，在输入对应的格式（比如json)
> 方式2: `command + k`,  松开（不要继续按着command），再按 `m` , 在输入对应格式（如json）


