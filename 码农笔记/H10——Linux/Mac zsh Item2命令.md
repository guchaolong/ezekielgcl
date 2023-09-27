#Linux #MacOS #iTerm2


# Homebrew
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
```zsh
brew -v
brew install tree
```
4 切换到bash后，提示-bash: brew: command not found，执行：
```zsh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.bash_profile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
5 [Homebrew更换国内镜像源（中科大、阿里、清华）](https://blog.csdn.net/xiewanchen0708/article/details/128232697)
brew安装完成后，brew-cask也会随着自动安装，并不需要手动重新安装brew-cask

6 使用
```zsh
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

# Command Line Tools
执行`brew install cmatrix`命令的时候出现
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1673421272144-96d73839-2876-45ed-a302-d849199cbc89.png#averageHue=%2321333f&clientId=ue08a7ae4-1cdc-4&from=paste&height=174&id=u908b1296&originHeight=174&originWidth=968&originalType=binary&ratio=1&rotation=0&showTitle=false&size=96244&status=done&style=none&taskId=ua71cc914-5797-4bba-97a0-a3db3a6deba&title=&width=968)
然后执行`xcode-select --install`安装
安装完成后测试
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1673421424705-fd2b57db-c07c-46cd-b4aa-1b77d334f3c0.png#averageHue=%23283e4d&clientId=ue08a7ae4-1cdc-4&from=paste&height=304&id=u1d0f91ef&originHeight=304&originWidth=1230&originalType=binary&ratio=1&rotation=0&showTitle=false&size=386068&status=done&style=none&taskId=u341288a2-f301-465f-a808-46eed8cea99&title=&width=1230)
安装的实际位置`xcode-select --print-path`
/Library/Developer/CommandLineTools
删除系统现有的CommandLineTools：`sudo rm -rf /Library/Developer/CommandLineTools`

# 装X命令
```zsh
蒸汽火车
brew install sl
sl

代码雨
brew install cmatrix
cmatrix

牛说话
brew install cowsay
cowsay Fuckyou

输出一句话
brew install fortune
fortune


```

# export 列出当前的环境变量值
export -p

# top 资源占用情况 性能分析
top
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1682030069427-82af9c24-59d0-43a5-ad91-313ac901f97b.png?x-oss-process=image%2Fresize%2Cw_675%2Climit_0#averageHue=%23172f35&from=url&id=zho9c&originHeight=267&originWidth=675&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&status=done&style=none&title=)
修改刷新时间：输入s, 然后再输入数字，再enter
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1682030178144-2e2130a6-c278-47f1-9050-737ceab79ce4.png#averageHue=%230f272d&from=url&id=sIJHr&originHeight=217&originWidth=1029&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&status=done&style=none&title=)
排序：输入字母o, 可以看到下图，当前是以cpu排序，然后输入比如“mem”，enter, 就会按MEM排序
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1682030302459-20590858-f620-4e18-89f4-92323d0b8c56.png#averageHue=%230f272e&from=url&id=CLre8&originHeight=290&originWidth=820&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&status=done&style=none&title=)

![](https://cdn.nlark.com/yuque/0/2023/png/663445/1682030414012-0911c0c1-bfb7-442c-8e56-2bd21a44db86.png#averageHue=%2310282e&from=url&id=quSf3&originHeight=373&originWidth=819&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&status=done&style=none&title=)

# sysctl machdep.cpu查看cpu信息
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1687033582364-34318472-0fe1-438f-aba3-99aec5ae49f7.png#averageHue=%230c2931&from=url&id=xjgZx&originHeight=154&originWidth=464&originalType=binary&ratio=0.8999999761581421&rotation=0&showTitle=false&status=done&style=none&title=)

# smartctl -a disk0 查看磁盘读写量，剩余寿命
安装`brew install smartmontools`
查看读写，剩余寿命 `smartctl -a disk0`
简单看Percentage Used是多少就行，这个值越高说明寿命不行了，我的是 0，nice
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689198169335-3c29bd5d-c798-43f1-91f7-b66352e4bdab.png#averageHue=%23081d24&clientId=u24f4097a-630c-4&from=paste&height=198&id=uc24d469e&originHeight=395&originWidth=954&originalType=binary&ratio=2&rotation=0&showTitle=false&size=73512&status=done&style=none&taskId=u30b2ed6c-ad98-41dc-8b44-e14689a6bf5&title=&width=477)

# find 查找
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1689270934310-3b83c7a7-2e7d-4585-9147-8898988a0674.png#averageHue=%230f313a&clientId=u5089caa5-8bdf-4&from=paste&height=169&id=u12b32f54&originHeight=162&originWidth=593&originalType=binary&ratio=2&rotation=0&showTitle=false&size=64643&status=done&style=none&taskId=udee89a11-7e32-481e-b1de-d34fbca1691&title=&width=617.5)
macos下，根据 name 查询，如果有通配符，要在‘’内
```zsh
find . -name '*.log'|grep hello	当前目录及子目录下，查找后缀为log且文件中包含hello字样的文件
find ./ -name f2.txt			当前目录下查找名称为f2.txt的文件
find / -user zeki				根目录下查找属于zeki这个用户的文件
find / -size +20M				根目录下查找大于20M的文件（常用，磁盘不够，选出大文件删除）
find / -size -20M				...小于20M
find / -size 20M				...等于20M
```


 
