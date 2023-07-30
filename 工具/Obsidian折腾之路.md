#Obsidian #工具 #笔记 #效率

# 主题
* vue
* Blue Topaz

# 插件相关
## 日历——calendar
右侧显示日历栏

##  PicGo图床——Image auto upload Plugin
配合PicGo，图片自动上传到图床，转换成连接形式

## 备份到GitHub——Obsidian git
**同步**到GitHub，现在github默认分支是main，需要设置一下
  `git branch -M main`


## 模版——Templater


## 闪念想法收集——memos、quick add


## 隐藏界面图标、工具栏、状态栏——Hider


## 文章封面图——Banners
你找不到好看的头图？给你一个链接 https://pixabay.com/images/search/banner/

## 单词自动补全——various complements
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230731020019.png)


## 主题的样式设置——Style Setting
例如，当前的blue topaz主题，md文件前有图标，可以在style setting中去掉
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230731024313.png)

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230731024601.png)


## 图表——charts view和Dataview
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230731040724.png)

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230731041215.png)







# 备份和同步
备份：
在github新建仓库，使用Obsidian git插件备份到GitHub

ios同步：
方法一：iCloud同步
开启obsidian使用iCloud云盘Apple ID->iCloud->iCloud云盘->同步至iCloud云盘的App

现在iPhone端创建仓库，勾选iCloud同步
然后mac上
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230730055640.png)

Obsidian打开已有仓库



方法二：使用working copy软件
参考 [使用 working copy 同步笔记到obsidian](https://segmentfault.com/a/1190000041888141)
Mac上弄好GitHub仓库
iPhone上下载working copy软件
Obsidian创建一个仓库`ezekielgcl`,不勾iCloud，并且设置配置文件为`.obsidian.mobile`
`
在**文件**app中就可以看到
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230730064102.png)


working copy中点+号，`Clone repository`把GitHub上的仓库克隆下来

长按仓库，点`Share`-> `Link Repository to Folder`，选择我的iPhone下的Obsidian下的刚创建的仓库


之后在working copy上同步到iPhone上
点右下角这个图标，然后pull
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230730061313.png)


![IMG_6EA169491203-1.jpeg](https://raw.githubusercontent.com/guchaolong/articleImgs/master/IMG_6EA169491203-1.jpeg)



# 设置
## 日记模版和存放位置
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230730043916.png)




# 文章推荐
[Obsidian 一周使用心得（配置、主题和插件）](https://zhuanlan.zhihu.com/p/534185171)


# 快捷键
插入链接：`command + k`，()中是url, \[\]中是显示的文字
切换编辑模式和阅读模式：`command + e`



# 语法
## 标注块
### info
> [!info] 信息
> 这是一个info块



### note
> [!note] 注意
> 这是一个注意块

> [!info]- 折叠的info块
> 使用`> [!info]-`  + 空格 + 提示字，就会默认折叠下面的内容


### abstract, summary, tldr

> [!abstract] 摘要， 摘要， tldr

### tip, hint, important
> [!TIP] 提示，提示，重要

### success, check, done
> [!success] 成功，检查，完成


### question, help, faq
> [!question] 问题， 帮助， 常见问题

> [!FAQ]- 标注是否可折叠？  
> 是的！在可折叠标注中，内容在展开之前一直处于隐藏状态。

### warning, caution, attention
> [!warning] 警告，谨慎，注意

### failure, fail, missing
> [!failure] 失败、失败、缺失

### danger, error
> [!error] 危险，错误

### bug
> [!bug] 错误


### example
> [!example] 例


### quote, cite
> [!quote] 引用，引用





