---
layout: post
title: {{VALUE:Title}}
subtitle: 
author: ezekielgcl
date: {{DATE}}
aliases: 
tags: 
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: {{DATE}}
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[cpu.jpeg]]"
banner_y: 0.40239
banner_icon: 💻
---

#DIY装机 #硬件/显卡
#硬件



> PC硬件知识，本文以Intel、NVIDIA的作主要介绍

# CPU
> 主要是Intel和AMD两家


## Intel酷睿系列cpu命名后缀
> 无后缀：不可超频，有核显
> K：不锁超频，增加了<mark style="background: #FF5582A6;">超频</mark>能力
> F：<mark style="background: #FFF3A3A6;">不带核显</mark>，价格会更便宜，现在多数都会配独立显卡，核显使用的概率较小，这种cpu比较有性价比
> KF：可超频，无核显
> X：酷睿最高级别的系列，性能毁天灭地
> S：特别版，i9-9900KS，S指的特别版本，可以理解为精挑细选出来体质更为优秀的CPU，相较9900K具有更强的超频属性


## 核心数、线程数、逻辑处理器等相关概念：
物理CPU/CPU
物理CPU内核/核心数/Core
逻辑CPU/逻辑处理器/Processor
> 一个物理CPU可以有<mark style="background: #D2B3FFA6;">1个或者多个</mark>物理内核
> 一个物理内核可以作为<mark style="background: #ABF7F7A6;">1个或者2个</mark>逻辑CPU
> 没有开启超线程时，逻辑CPU的个数就是总的CPU物理内核数
> 开启超线程后，逻辑CPU的个数就是总的CPU物理内核数的两倍
> 有多少个逻辑处理器，就说明你的cpu可以同时处理几个线程(**线程数=逻辑处理器个数)**


## 13代的P-CORE和E-CORE
> 最新一代的英特尔CPU采用了<mark style="background: #BBFABBA6;">性能核心(P-CORE)</mark>＋<mark style="background: #ADCCFFA6;">能效核心(E-CORE)</mark>的混合架构设计
> P-CORE又称为性能核/大核，专门负责强化<mark style="background: #ABF7F7A6;">单线程</mark>处理能力，在<mark style="background: #BBFABBA6;">游戏、生产力</mark>创作中都可以提供超强性能
> E-CORE又称为效率核/小核主要加强<mark style="background: #BBFABBA6;">多线程</mark>处理能力，可以应对大吞吐量负载，并针对<mark style="background: #FFF3A3A6;">后台应用</mark>进行优化


## 主频、外频、倍频系数
> CPU的频率指的是一秒内CPU的时钟周期运行的次数，单位是Hz

我们平时看到的4.0GHZ、3.0GHZ等指的就是CPU主频，即每秒可以产生40亿、30亿个脉冲信号
早期的CPU运行速度还不快，CPU和系统总线的工作频率是一样的，但随着技术的发展，CPU的性能快速提升，而其他设备无法承受更高的频率，CPU的频率很快就超过了系统总线的频率，于是就出现了倍频。
倍频是为了解决系统总线频率跟不上CPU的速度而出现的，通过在CPU内部设置<mark style="background: #BBFABBA6;">锁相环频率发生器</mark>，将系统输入的信号进行分频处理，按照设定的比例提高外频的频率，提高之后的频率就是CPU的主频，而设定的这个比率就是倍频系数。
![](https://cdn.nlark.com/yuque/0/2023/jpeg/663445/1686784199745-4102c701-0673-4fe4-aa64-891333dbf56c.jpeg#averageHue=%23f9f9f9&clientId=u5dbafcce-ea1e-4&from=paste&id=ufcc636c0&originHeight=188&originWidth=600&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u07014664-a403-44ec-b1e7-3eff9ef6c48&title=)
举个简单的例子，当外频是100MHz的时候（目前大多数平台的外频都是100MHz），设置一个37的倍频系数，就可以得到CPU的主频=100MHz x 37=3.7GHz了。
CPU厂商对主频的设置较为保守，而用户对高频率又有一定的需求，这也是超频的背景。知道了<mark style="background: #D2B3FFA6;">主频=外频×倍频系数</mark>，就可以发现，不管提升外频还是提升倍频都可以起到提升主频的效果，这也就是超频的几种方式。
我们经常说的锁倍频指的就是CPU中的锁相环频率发生器锁定倍频系数，也就是无法通过提升倍频的方式超频。

<mark style="background: #BBFABBA6;">目前英特尔的CPU只有K尾缀是不锁倍频的，且需要搭配Z系列主板才能超频</mark>；而AMD的CPU全系都不锁倍频，但也需要B系列或X系列的主板才能超频。
不过即使锁了倍频系数，也可以通过提升外频的方式进行超频。提升外频需要特定的主板支持，也需要玩家有一定的动手能力，不过英特尔的13代酷睿把外频也锁了，不带K的处理器就真的不能超频了。

## 默频、睿频、超频
默认基础频率，是 CPU 标出的主频
睿频 是采用 Intel 睿频加速技术可达到的更高频率，可以理解为<mark style="background: #CACFD9A6;">自动超频</mark>。
超频 是为了实现超过额定频率性能，人为调整各种指标（如电压、散热、外频、电源、BIOS等），属于<mark style="background: #ADCCFFA6;">手动超频</mark>。

由于强行超频对系统和硬件会产生负面影响，所以大厂们在CPU出厂时将其倍频锁定在一个固定的数值，使其倍频系数不能再任何变动，即锁频

睿频和超频很像，都可以提升频率，提高性能，但两者还是有本质区别。
超频是人为提升频率，调整各项指标，一般会超过处理器的规划规格，导致功耗的大幅度增加，虽然超频可以带来明显的性能提升，但是准入门槛高，风险很大，对CPU和系统都可能造成严重损坏。
睿频是采用睿频加速技术（Intel的睿频技术为Turbo Boost Technology；AMD的睿频技术为TurboCore），依靠处理器的智能自主处理，使 CPU 主频可以在某一范围内根据处理数据需要自动调整主频

## CPU分类
<mark style="background: #BBFABBA6;">i3=办公、i5=游戏、i7=生产力、 i9=旗舰</mark>

办公家用（带核显就行）：i3-12100、i3-13100
> i3-13100/F：适合家用、办公、网游，性能不俗，i3-12100F的马甲，领先幅度极小，目前行情不值得选购，建议考虑i3-12100F，两者价格差距在几十块再考虑选择i3-13100F


游戏性价比：i5-12400F   i5-12490F、i5-13400F、i5-13490F、i5-12600KF
> i5-12600KF：性能和i5-13400F一样，单核性能比i5-13400F高10%，多核高5%，价格太贵，性价比不高
> i5-13400F：相比i5-12400F新增4个效能核心，多核性能则领先30%左右，单核性能也有5%左右提升，除了打游戏，对于程序多开、生产力需求更好，新款主流中端选择，性价比比较高
> i5-13490F：目前价格有点贵，现阶段推荐i5-13400F
> i5-13600KF：适合打游戏、生产力需求，贵，性价比不高


生产力性价比：i7-13700/F、i7-13790F
> i7 13700/F：建议生产力需求
> i7-13790F：价格偏贵，没有散片CPU选择，现阶段不值得选择
> i7-13700K/F：搭配Z790主板；（打游戏、生产力需求）


高生产力：i9-13900KS/F
> i9-13900K/F：搭配Z790主板；（高端旗舰级CPU，全能型）
> i9-13900KS：高端旗舰级CPU，全能型，相比i9-13900K/F拥有更高的频率，适合发烧级游戏


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686764958755-8b92c6e6-c2e6-4697-8194-70ce9ba3b3b0.png#averageHue=%23161336&clientId=u80c815c6-4fa7-4&from=paste&height=1145&id=uf18b36d4&originHeight=1145&originWidth=777&originalType=binary&ratio=1&rotation=0&showTitle=false&size=988402&status=done&style=none&taskId=ucaece70c-4e7f-445b-8fac-a0d84948aaa&title=&width=777)


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686765157258-4d9b744d-da72-4652-8c91-1bbef7ee2324.png#averageHue=%230d0d0c&clientId=u80c815c6-4fa7-4&from=paste&height=1084&id=ud33aef11&originHeight=1084&originWidth=723&originalType=binary&ratio=1&rotation=0&showTitle=false&size=532096&status=done&style=none&taskId=u0c195fd1-5f7e-498c-89f8-1eedb3c90d2&title=&width=723)

## 根据显卡搭配CPU（天才赵德柱）
> 以i9-13900K为100%，能达到它的95%就算合格

### RTX4090
如果使用RTX4090显卡，13900K为顶级，12700KF以上的才能达到13900K的95%以上，所以RTX4090最低搭配12700KF，或放低点标准，12600KF起步
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686933620746-fba6af10-9df9-45dc-91cf-65a6be8e5c41.png#averageHue=%2328343a&clientId=u51801108-81cd-4&from=paste&height=889&id=lTi9Q&originHeight=889&originWidth=1844&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1194064&status=done&style=none&taskId=u96679c87-bbd7-4b88-b41a-254a9c379bc&title=&width=1844)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686933462848-b2ffa917-84b9-4cfd-9fcb-c4c45c187100.png#averageHue=%23233338&clientId=u51801108-81cd-4&from=paste&height=839&id=KHSIT&originHeight=839&originWidth=1198&originalType=binary&ratio=1&rotation=0&showTitle=false&size=351576&status=done&style=none&taskId=u97eb9e77-5c83-4387-aced-7ae3bb4eadf&title=&width=1198)
 
### RTX3090Ti
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686933857934-8149b866-370c-4be5-9a55-4dd049127074.png#averageHue=%232b2b28&clientId=u51801108-81cd-4&from=paste&height=881&id=u3977bb05&originHeight=881&originWidth=1802&originalType=binary&ratio=1&rotation=0&showTitle=false&size=900269&status=done&style=none&taskId=uafaa19fd-69e5-44b3-9dae-7ebfc7718c7&title=&width=1802)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934009828-37ddcd47-cbc6-45af-9acc-74b9adb68d27.png#averageHue=%23539853&clientId=u51801108-81cd-4&from=paste&height=836&id=u2f869222&originHeight=836&originWidth=1203&originalType=binary&ratio=1&rotation=0&showTitle=false&size=378976&status=done&style=none&taskId=u44b4327b-1369-4fd2-bce1-87cb3b21e4a&title=&width=1203)

### RTX3090
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934113482-081174db-de40-47f9-a618-485d3ea6ea50.png#averageHue=%23544c2a&clientId=u51801108-81cd-4&from=paste&height=879&id=u18f7c16d&originHeight=879&originWidth=1853&originalType=binary&ratio=1&rotation=0&showTitle=false&size=952794&status=done&style=none&taskId=u9fea2395-668f-4c6b-852d-3223ac488af&title=&width=1853)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934173840-50614c51-5853-489e-bb41-ef266750215c.png#averageHue=%233d8679&clientId=u51801108-81cd-4&from=paste&height=853&id=u3144a088&originHeight=853&originWidth=1223&originalType=binary&ratio=1&rotation=0&showTitle=false&size=389654&status=done&style=none&taskId=u9c31a83e-57f2-427c-b8a4-7c41bda4bac&title=&width=1223)

### RTX3080
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934245454-9935a9de-2873-45ee-870a-989e93e511cc.png#averageHue=%235b512b&clientId=u51801108-81cd-4&from=paste&height=883&id=ua75d65d3&originHeight=883&originWidth=1824&originalType=binary&ratio=1&rotation=0&showTitle=false&size=956309&status=done&style=none&taskId=u9436cd8f-4941-46d0-932c-9d42695f509&title=&width=1824)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934258366-f41ec497-ec63-4e84-adbc-f1e34591deab.png#averageHue=%23419281&clientId=u51801108-81cd-4&from=paste&height=824&id=AKZfi&originHeight=824&originWidth=1183&originalType=binary&ratio=1&rotation=0&showTitle=false&size=372082&status=done&style=none&taskId=u372d0fdd-ee67-4eaa-96a8-1f691dcf508&title=&width=1183)

### RTX3070Ti
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934380788-f8e072d1-2b5e-4883-94f4-e98b13b13072.png#averageHue=%232b2a28&clientId=u51801108-81cd-4&from=paste&height=886&id=ud6d6030c&originHeight=886&originWidth=1823&originalType=binary&ratio=1&rotation=0&showTitle=false&size=854301&status=done&style=none&taskId=u31f87c19-82eb-4e90-842c-3fe5f05aa6f&title=&width=1823)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934415962-b41106f6-0844-4c21-a3e3-8481d4c7c038.png#averageHue=%23428d7b&clientId=u51801108-81cd-4&from=paste&height=852&id=u138fd0b7&originHeight=852&originWidth=1236&originalType=binary&ratio=1&rotation=0&showTitle=false&size=383448&status=done&style=none&taskId=uf90cdf57-bf1a-4b2c-b954-b769d94a5d0&title=&width=1236)

### RTX3060Ti
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934456263-bf72502f-2641-4ca8-a571-24fa157893ad.png#averageHue=%232a2926&clientId=u51801108-81cd-4&from=paste&height=879&id=u42a2b6ce&originHeight=879&originWidth=1805&originalType=binary&ratio=1&rotation=0&showTitle=false&size=981351&status=done&style=none&taskId=u6061f8de-2c5e-4b8e-9664-33d135877e1&title=&width=1805)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934507828-b0e99d41-2278-493b-bc4e-2112fd4771f0.png#averageHue=%23479d6c&clientId=u51801108-81cd-4&from=paste&height=855&id=u2e750544&originHeight=855&originWidth=1210&originalType=binary&ratio=1&rotation=0&showTitle=false&size=396592&status=done&style=none&taskId=u4549f2f7-c058-4bef-93b6-f4caadd6d88&title=&width=1210)

### RTX3060
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934580071-ba841b2a-017f-465d-83ab-4a6575606ad1.png#averageHue=%232a2926&clientId=u51801108-81cd-4&from=paste&height=873&id=uc773beb7&originHeight=873&originWidth=1805&originalType=binary&ratio=1&rotation=0&showTitle=false&size=877965&status=done&style=none&taskId=ud30026b6-4458-4111-8b08-b41eaa0471c&title=&width=1805)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934618405-f0664314-56ad-413b-9ae9-9053f8125107.png#averageHue=%233b8a74&clientId=u51801108-81cd-4&from=paste&height=840&id=u181a1f96&originHeight=840&originWidth=1234&originalType=binary&ratio=1&rotation=0&showTitle=false&size=384590&status=done&style=none&taskId=ub28c9a7e-bd4b-411a-a713-8d0e2d497f9&title=&width=1234)

### RTX3050
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934656337-90080bbe-d2fc-433d-833a-bf23700e30f3.png#averageHue=%232b2a28&clientId=u51801108-81cd-4&from=paste&height=891&id=ucaaa11d2&originHeight=891&originWidth=1819&originalType=binary&ratio=1&rotation=0&showTitle=false&size=922552&status=done&style=none&taskId=u3b816dfa-48f4-4461-a4e8-8fa8a1162e1&title=&width=1819)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686934682010-3a9f2953-1a1c-46bb-bc87-85ba8138b5ba.png#averageHue=%233b937c&clientId=u51801108-81cd-4&from=paste&height=844&id=u22f5f134&originHeight=844&originWidth=1198&originalType=binary&ratio=1&rotation=0&showTitle=false&size=365430&status=done&style=none&taskId=u43b77b6a-3a9d-4f4f-80e9-7390ecd24c3&title=&width=1198)



# 显卡
做<mark style="background: #ABF7F7A6;">显卡核心</mark>的两大厂家：NVIDIA 和 AMD
> 以前 Intel做的显卡核心都放到自家CPU里了
> 2022年3月30日，一直只有核显的**英特尔发布了自家的独立显卡**。名字叫做**Intel ARC**，中文名字叫做**“锐炫**
> 现在除了英伟达和AMD外，终于有**第三家独立显卡**加入了竞争团队


## 公版、非公版、N卡、A卡
NVIDIA 和 AMD做出显卡核心，叫公版显卡，然后在把显卡核心给到其他合作伙伴，做出的显卡叫非公版显卡，市面上的显卡用的都是NVIDIA和AMD的显卡核心，所以基本可分为N卡和A卡

例如，英伟达做出**公版显卡**，**RTX 3060 Ti**，然后华硕根据RTX 3060 Ti的核心做出新的显卡：
**华硕 ROG RTX3060/Ti D6X GAMING猛禽**
**华硕 (ASUS）TUF GeForce RTX 3060 Ti-O8GD6X-GAMING**
这两个就是**非公版显卡**，它们的核心都是**RTX 3060 Ti**

## 命名：
N卡以NVIDIA Geforce RTX 4070Ti为例
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686759385826-d77a2628-4064-4c0b-85ca-3a806a848b7f.png#averageHue=%23dedfd9&clientId=u24350b65-99c9-4&from=paste&height=966&id=u5a2dc685&originHeight=966&originWidth=1730&originalType=binary&ratio=1&rotation=0&showTitle=false&size=552694&status=done&style=none&taskId=ub59ebbda-2abb-4546-b82b-f088acacbb5&title=&width=1730)

NVIDIA：英伟达，品牌名、厂商
Geforce：系列，有Geforce （更适合游戏）, Quadro，TIRAN……
RTX：定位，RTX （光追高端）> GTX (高端） > GTS (中端） > GT (低端）
40：代数，第40代，之前还有30、20、16、10...
70：性能等级，<mark style="background: #BBFABBA6;">50入门低端，60甜品，70中端，80高端，90旗舰</mark>
Ti：后缀，Ti 性能加强版；S性能增强版；  <mark style="background: #FF5582A6;">OC超频版</mark>， 性能关系：<mark style="background: #D2B3FFA6;">Ti > Super > OC </mark>

## OC后缀

1. OC后缀显卡有更高的默认频率且支持自动超频，不带OC后缀的显卡需要手动超频
2. OC后缀显卡散热更强大，用料更好
3. OC后缀显卡寿命更长
## DLSS 超分辨率技术
AI技术，DLSS可以在维持显示质量的同时显著提高游戏的性能

## RTX 30系
显卡对于电脑性能的提高非常巨大，**尤其是游戏方面**，但是要看整体性能是否可以正常发挥，比如1080P分辨率的显示器，顶级显卡会浪费性能，有时候升级都不一定可以提升游戏体验，许多设备也要同步升级

目前电脑市场，显示器已经开始普及<mark style="background: #FF5582A6;">2K/4K+高刷</mark>，而市场的3A大作的特效表现也一年比一年精细，对于显卡的性能需求也变得更高，而我们在追求游戏体验的时候，会特别关注游戏的特效和帧数表现，特别是游戏高特效下的帧数表现，<mark style="background: #D2B3FFA6;">能玩(30FPS)、流畅（60FPS）、电竞（144FPS）、专业（240FPS）</mark>
RTX 30系列的中高端显卡(RTX 3070Ti、RTX 3080 Ti、RTX 3090Ti)，在目前许多大热门3A大作表现优异

众所周知，二手显卡是极为不靠谱的，很多显卡可能经过了高负荷的锻炼后续翻新，既然都掏钱了，比较建议官方推荐的购买渠道，特别是这种高价位产品，直接上显卡品牌的京东自营店最靠谱

## 显卡各品牌等级
> 图片来源于up主天才赵德柱，其中没有御三家中的技嘉，估计是因为技嘉之前的言论...
> 注意：不同品牌的相同段位不一定水平相同，比如华硕的旗舰猛禽，和映众的旗舰超级冰龙，肯定猛禽牛逼

N卡：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686938206954-f70d06f3-2c64-4f43-b416-1b42b08f8dae.png#averageHue=%233d4149&clientId=u542c054f-1480-4&from=paste&height=724&id=ufe911ae7&originHeight=724&originWidth=1810&originalType=binary&ratio=1&rotation=0&showTitle=false&size=616589&status=done&style=none&taskId=uc3a0616e-1a89-4399-872a-16067529ca5&title=&width=1810)
各AIC厂家品牌分级：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686935975848-e39702d7-0245-4ea2-8b99-7a3fc452797c.png#averageHue=%232b3438&clientId=u542c054f-1480-4&from=paste&height=793&id=uc90da76f&originHeight=793&originWidth=1833&originalType=binary&ratio=1&rotation=0&showTitle=false&size=503076&status=done&style=none&taskId=u3b6b5d07-de14-4a0b-96bf-ad1d7f9acbc&title=&width=1833)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936591014-28c382c5-e5b9-4e0d-9b40-b595bc53613a.png#averageHue=%23262d38&clientId=u542c054f-1480-4&from=paste&height=807&id=u24bf7273&originHeight=807&originWidth=1831&originalType=binary&ratio=1&rotation=0&showTitle=false&size=421816&status=done&style=none&taskId=uc8284012-c814-4a79-9c37-b610be27c42&title=&width=1831)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936703912-8ba3efd4-d782-4505-a878-56b6a10d0a96.png#averageHue=%23323b47&clientId=u542c054f-1480-4&from=paste&height=792&id=u6d412771&originHeight=792&originWidth=1842&originalType=binary&ratio=1&rotation=0&showTitle=false&size=687315&status=done&style=none&taskId=u762c0867-9b47-4529-a1a2-5f42bfcb1c7&title=&width=1842)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936761584-ec5a8e77-0f86-45b8-8ee3-414ec9ade7b3.png#averageHue=%232b333e&clientId=u542c054f-1480-4&from=paste&height=804&id=ua21fa574&originHeight=804&originWidth=1835&originalType=binary&ratio=1&rotation=0&showTitle=false&size=626233&status=done&style=none&taskId=u6c6a997f-b76b-4077-9e2c-13587562acf&title=&width=1835)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936812355-856bbc5b-105c-4092-8fc1-a85bed48aaef.png#averageHue=%232d343d&clientId=u542c054f-1480-4&from=paste&height=800&id=ub8917c38&originHeight=800&originWidth=1849&originalType=binary&ratio=1&rotation=0&showTitle=false&size=462320&status=done&style=none&taskId=u7a3bdfe6-fd78-44d3-8e09-384816b85b9&title=&width=1849)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936862484-a75da505-ed33-4bc4-8d9b-95a0dee15d69.png#averageHue=%232d353f&clientId=u542c054f-1480-4&from=paste&height=791&id=u9d33bdc4&originHeight=791&originWidth=1836&originalType=binary&ratio=1&rotation=0&showTitle=false&size=511352&status=done&style=none&taskId=u6d9c9db4-7660-46bc-9052-8a9657a38fb&title=&width=1836)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936912732-c664ebc9-cdd2-42c2-9c75-031f3c94c0f3.png#averageHue=%2328303b&clientId=u542c054f-1480-4&from=paste&height=807&id=u24dc85f1&originHeight=807&originWidth=1836&originalType=binary&ratio=1&rotation=0&showTitle=false&size=446936&status=done&style=none&taskId=u338b249b-78cf-4da6-88c8-337d48cf21f&title=&width=1836)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686936967349-4c337c5d-66b5-48f6-bf5b-86108e67f514.png#averageHue=%2329303a&clientId=u542c054f-1480-4&from=paste&height=792&id=u3451e0e7&originHeight=792&originWidth=1836&originalType=binary&ratio=1&rotation=0&showTitle=false&size=444332&status=done&style=none&taskId=u3994159b-c836-4b50-9306-22c4af91cee&title=&width=1836)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937008167-166e9ab1-d5e6-41cd-b7ff-126955c9cbb9.png#averageHue=%23272e39&clientId=u542c054f-1480-4&from=paste&height=790&id=u391de8a3&originHeight=790&originWidth=1834&originalType=binary&ratio=1&rotation=0&showTitle=false&size=356889&status=done&style=none&taskId=u2dfd3678-cad4-4e77-817b-4107b3c6661&title=&width=1834)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937066809-64ef97d7-52d9-4b81-a110-55204975fcc4.png#averageHue=%23252d38&clientId=u542c054f-1480-4&from=paste&height=793&id=u19b3ed3b&originHeight=793&originWidth=1847&originalType=binary&ratio=1&rotation=0&showTitle=false&size=369875&status=done&style=none&taskId=u463c2b25-e904-4d8b-a504-40f1e6aba5d&title=&width=1847)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937098203-78efb604-84a2-4a74-979f-1f513ac40776.png#averageHue=%232b313b&clientId=u542c054f-1480-4&from=paste&height=791&id=uc5f85316&originHeight=791&originWidth=1816&originalType=binary&ratio=1&rotation=0&showTitle=false&size=372175&status=done&style=none&taskId=u987d4527-fd17-4852-b2e8-efb3b9f7f4b&title=&width=1816)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937137078-18a69dce-8349-4339-913d-cfcf66a7f1dc.png#averageHue=%23252c37&clientId=u542c054f-1480-4&from=paste&height=797&id=ub4592972&originHeight=797&originWidth=1850&originalType=binary&ratio=1&rotation=0&showTitle=false&size=329720&status=done&style=none&taskId=u9af01278-90d7-42f5-9263-86b7791761f&title=&width=1850)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937180161-07686bcc-1b10-4e16-a5bb-1ec603ff312e.png#averageHue=%23242c37&clientId=u542c054f-1480-4&from=paste&height=787&id=u76b721f6&originHeight=787&originWidth=1829&originalType=binary&ratio=1&rotation=0&showTitle=false&size=366162&status=done&style=none&taskId=u306facf6-1752-4d9a-a665-502f4800930&title=&width=1829)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686937198922-f8cd13c6-2ccf-480d-b3f1-f373b1321e38.png#averageHue=%23262e39&clientId=u542c054f-1480-4&from=paste&height=800&id=ue04a5cbd&originHeight=800&originWidth=1846&originalType=binary&ratio=1&rotation=0&showTitle=false&size=377448&status=done&style=none&taskId=u3b0f77dc-7596-42af-9426-7281f2780ae&title=&width=1846)

A卡
情况比较特殊，因为A卡的合作伙伴本来就少，AIB就那么几家，
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686938353531-086dd57f-0b8a-426e-84a3-c5442682101b.png#averageHue=%23383d46&clientId=u542c054f-1480-4&from=paste&height=667&id=ua1071b48&originHeight=667&originWidth=1884&originalType=binary&ratio=1&rotation=0&showTitle=false&size=411671&status=done&style=none&taskId=u8c36bbc7-caa2-4211-b2f7-daccbe809c0&title=&width=1884)

## CPU显卡搭配：
> 办公或多开，CPU可以好一点，多开可能对内存有要求，把内存配大一点
> 游戏，尽量显卡好一点，大多数游戏对显卡要求比较高，可能cpu占用率不到50%，显卡占用率99%，显卡性能直接决定游戏FPS


<mark style="background: #BBFABBA6;">顶级显卡通常需要较好的CPU搭配才能更好发挥显卡的性能</mark>，12代酷睿处理器i5-12600KF和i9-12900K搭配RTX 3080 Ti，大概会产生10-20%的性能差距，其他的情况下，只要CPU性能不是太差配中端以上的显卡问题不大

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686814380302-8c33f60a-7645-471c-bfaf-6a4244588155.png#averageHue=%2398ca50&clientId=u3f2a2254-babf-4&from=paste&height=635&id=u37b1c21a&originHeight=635&originWidth=1828&originalType=binary&ratio=1&rotation=0&showTitle=false&size=346050&status=done&style=none&taskId=ueb208ecb-e1d2-4aba-ac99-f38f1799f22&title=&width=1828)

i3-12100F 搭配 3060 及以下的显卡
i5-12400F 搭配 3060Ti 及以下的显卡
i5-12600K 搭配 3080 及以下的显卡，超频可以带3080Ti

## 显示器1K 2K 4K不同画质下，各个显卡游戏性价比
图中的参数是3A大作下的显卡参数，如果不玩游戏，显卡就不那么重要了
图中包含N卡A卡，只谈N卡...
<mark style="background: #ADCCFFA6;">能玩(30FPS)、流畅（60FPS）、电竞（144FPS）、专业（240FPS）</mark>
<mark style="background: #ABF7F7A6;"></mark>横坐标，60FPS之后是能在当前画质下畅玩的显卡，纵坐标越高，性价比越高（价格越低）

1K中等画质：
1650supper就能在60FPS以上
如果要144FPS，3060Ti 性价比比较高
144FPS以上，再贵的显卡对1080P来说已经没有意义了，每张显卡之间的差距也不会太大，这时候瓶颈就来到CPU和内存这边了
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686914189384-997b86d9-e07d-4578-b620-d60c46afcdcc.png#averageHue=%23444444&clientId=ue0b53e01-e94a-4&from=paste&height=896&id=ngVjV&originHeight=896&originWidth=1895&originalType=binary&ratio=1&rotation=0&showTitle=false&size=371043&status=done&style=none&taskId=u065234f9-6191-44ca-91b2-c7ea38817bb&title=&width=1895)

1080P高画质
60FPS左边的显卡都已经不能满足3A流畅运行的需求了
3060、3060Ti性价比高
要玩1080P高刷，推荐3080，更高端的在这个画质下性能过剩了
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686915117804-0299577c-3360-474d-a131-47b3e2096f30.png#averageHue=%23444444&clientId=ue0b53e01-e94a-4&from=paste&height=889&id=u5b1bbd47&originHeight=889&originWidth=1875&originalType=binary&ratio=1&rotation=0&showTitle=false&size=366620&status=done&style=none&taskId=u9b4b7582-2f66-4d82-8a0c-b70527b6834&title=&width=1875)

当画质来到2K
这个时候2000元以内的卡均不能满足流畅运行的标准，不过如果原因降低一点画质，并且选择开启各家的DLSS超分辨率技术，挣扎在生死线上的显卡还是可以抢救一下的，比如3060
如果不想降低画质来提升帧率，最低需求3060Ti
高刷，推荐4070Ti
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686915687082-c09df471-49ec-439c-9b89-6e439b3dbe99.png#averageHue=%23444444&clientId=ue0b53e01-e94a-4&from=paste&height=899&id=QYEa0&originHeight=899&originWidth=1878&originalType=binary&ratio=1&rotation=0&showTitle=false&size=345853&status=done&style=none&taskId=u52e94ffb-9dfa-44a9-bc4c-3f5986b0dae&title=&width=1878)

当来到4K高画质
能够流畅运行的显卡已经不多了，60FPS左右，4070、3080、4070Ti差距不算太大，均在流畅运行和稍微流畅运行之间徘徊，3080还是能60FPS以上，性价比最高
降低一点画质并开启超采样技术，4060Ti 、3060Ti、3070、3070Ti还能再抢救一下
在未开启DLSS的情况下，4060Ti在4K下是跑不过3060Ti的，因为8G显存对于4K高画质来说，几乎都要吃满了
4090依旧非常强悍，这个状况可能一直要持续到4090Ti发布
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686916454599-9d460d27-1d51-457a-bd3d-e10866f4d6b1.png#averageHue=%23444444&clientId=ue0b53e01-e94a-4&from=paste&height=920&id=u377b3f9b&originHeight=920&originWidth=1885&originalType=binary&ratio=1&rotation=0&showTitle=false&size=360390&status=done&style=none&taskId=u01f4db60-990f-4e4b-b811-6ee6ae8af65&title=&width=1885)

> 以上的参数对比仅限于常规的渲染场景，接下来看光追性能排行
> 如果要在2K下畅玩**3A的光追大作**，就只剩下4080、4090两张显卡了
> 更高分辨率就只能是4090了

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686917298079-0b5add3c-272f-4212-9b25-3ad60e0112cc.png#averageHue=%23444444&clientId=ue0b53e01-e94a-4&from=paste&height=915&id=ubdb97ef7&originHeight=915&originWidth=1865&originalType=binary&ratio=1&rotation=0&showTitle=false&size=334664&status=done&style=none&taskId=ua5ded0ac-9c8d-438b-b432-0994a57339b&title=&width=1865)

## 3A大作根据显示器选择显卡
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686634279406-def3cd9c-440b-4b7e-980e-a273ed5cb217.png#averageHue=%23827c2f&clientId=ubff19bce-2bb4-4&from=paste&height=863&id=G0hkg&originHeight=863&originWidth=1779&originalType=binary&ratio=1&rotation=0&showTitle=false&size=392689&status=done&style=none&taskId=u69499685-fa2a-4ba3-b49d-58b2352aa9d&title=&width=1779)
玩3A大作
2K分辨率：RTX2080S、RTX2080Ti、RTX3060Ti 、RTX3070 、RTX3070Ti 
4K分辨率：RTX3080 、RTX3080Ti 、RTX3090 、RTX3090Ti 

## 3060Ti G6X和4060Ti
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687012404369-cca55ed5-c48b-4bda-8eac-e186580f755e.png#averageHue=%234fb0eb&clientId=u9fa9484b-dbcd-4&from=paste&height=433&id=u7045a27f&originHeight=433&originWidth=854&originalType=binary&ratio=1&rotation=0&showTitle=false&size=195555&status=done&style=none&taskId=u491a2083-96b4-4bc9-80ba-40c44b62ddc&title=&width=854)
跟旧版的3060Ti比，4060Ti性能提升15%
跟新版3060Ti G6X比，4060Ti性能提升不到10%
如果不玩游戏，直接3060Ti

但这是在老的光栅类游戏，4060Ti乃至整个40系都是针对光追类游戏优化，如果测光追类游戏，4060Ti比3060Ti提升就大了，打败3070也不是问题，这还是在不开启DLSS3的情况下，如果开了，那3070Ti都不够看
如果要玩新的光追类游戏，上4060Ti，目前4060Ti也就比3060Ti贵300~500左右
如果玩的游戏支持DLSS3，或者未来支持DLSS3，毫无疑问，肯定上4060Ti




**以下3张表是根据显卡配置玩3A大作配什么显示器比较理想，如果不玩大型游戏，配啥都行**
RTX 3080 Ti 的性能强悍(游戏表现与RTX 3090差不多)，但是购买RTX 3080 Ti显卡的用户一定要确保电源在850W左右，对于使用4K分辨率显示器的用户来说，RTX 3080 Ti这是一个必须的升级型号
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686788234027-005a5add-e08a-4954-aa53-135d57ecddb4.png#averageHue=%23bcc815&clientId=u2ce3af9c-b41b-4&from=paste&height=733&id=tgtlY&originHeight=733&originWidth=557&originalType=binary&ratio=1&rotation=0&showTitle=false&size=508387&status=done&style=none&taskId=u8fbd3cc7-71de-4c4b-8354-3cf22af4c8c&title=&width=557)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686788262964-1be7472d-b9cc-40e0-bc91-ddde6d5ddb7e.png#averageHue=%23dce609&clientId=u2ce3af9c-b41b-4&from=paste&height=729&id=nJGFK&originHeight=729&originWidth=575&originalType=binary&ratio=1&rotation=0&showTitle=false&size=477707&status=done&style=none&taskId=u96f23cd5-6b8e-4793-bf31-ca711c23982&title=&width=575)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686788287323-9eb43b2e-de79-47db-9b21-87e7c166a1ab.png#averageHue=%23375b1c&clientId=u2ce3af9c-b41b-4&from=paste&height=737&id=vWWpB&originHeight=737&originWidth=563&originalType=binary&ratio=1&rotation=0&showTitle=false&size=367985&status=done&style=none&taskId=ud2215995-8411-4d46-9d0d-1621b5055ec&title=&width=563)

## 办公专业软件对显卡的需求
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686634579079-f5df301b-0e0c-4fcc-9715-6462d63a82e9.png#averageHue=%2375722f&clientId=ubff19bce-2bb4-4&from=paste&height=924&id=lC9wk&originHeight=924&originWidth=1835&originalType=binary&ratio=1&rotation=0&showTitle=false&size=526989&status=done&style=none&taskId=uec4ddd0c-bd59-404f-8f88-b29084cf15b&title=&width=1835)

## 矿卡
之前虚拟货币兴起，一些人用显卡组成矿机，通过显卡的算力来挖矿
2022年9月15号， 以太坊停止挖矿，现在挖矿已经结束了
100%无矿：
<mark style="background: #BBFABBA6;">40系全系无矿卡</mark>
<mark style="background: #FFB8EBA6;">**GDDR6X**显存的3060Ti</mark>，2022年10月上市的，100%无矿，目前性价比还行，怕矿卡可以考虑入手这张
3060 8G，2022年10月上市的，100%无矿，比3060 12GB弱近15%，性能十分拉跨，也就主打一个无矿
3050，2023年1月上市的，基本无矿，性能也比较拉跨，挖矿性能也垃圾，没人拿他挖矿

常见的矿卡
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687002693158-61c2dbfb-2997-4e17-8662-862f2f2dafe7.png#averageHue=%233a3734&clientId=ua0a88d58-f645-4&from=paste&height=800&id=u0f034e34&originHeight=800&originWidth=1354&originalType=binary&ratio=1&rotation=0&showTitle=false&size=821948&status=done&style=none&taskId=u3a9d5055-80e6-4e85-adf7-d67d78bf2d6&title=&width=1354)


# 主板
> 主板是电脑其他硬件的载体，所有的硬件都要安装或连接到主板上，主板本身并不提供性能，但主板能决定其他硬件性能，所以选择合适的主板就很重要了
> 主板过低，跑不满CPU
> 主板过高，不会有任何性能的提升
> 小知识：<mark style="background: #FFB8EBA6;">双内存槽主板的内存超频能力强于四内存插槽主板</mark>，目前最强的超频主板Z790 APEX就是双槽主板

## 版型：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686842677837-644c6491-e1bb-4748-a072-d298e7cc75e3.png#averageHue=%2353605f&clientId=u20a8a4d7-c497-4&from=paste&height=614&id=u16d88475&originHeight=614&originWidth=1895&originalType=binary&ratio=1&rotation=0&showTitle=false&size=936798&status=done&style=none&taskId=u6c7525bf-c92c-48ca-83db-2cb738967ca&title=&width=1895)
> EATX：普遍应用于<mark style="background: #FF5582A6;">服务器</mark>领域，另外少量消费级主板也会采用EATX版型，如玩家国度Z690水冷
> ATX：<mark style="background: #D2B3FFA6;">大版</mark>，普遍应用于高端芯片组，多数都是大版，如Z690
> MATX：<mark style="background: #FFB8EBA6;">中版</mark>，普遍应用于中端芯片组，如B660，另外还有阉割的MATX版型，比MATX还小一些，叫小版，应用于低端芯片组，如H610
> mini-ITX：<mark style="background: #D2B3FFA6;">小版</mark>


## PCI-E：
全名叫**PCI Express**，简称**PCI-E**，官方简称**PCIe**，他是计算机内部的一种高速总线

### 通道/接口
<mark style="background: #FF5582A6;">PCI-E既是通道，也是接口</mark>，
当**PCI-E**<mark style="background: #D2B3FFA6;">接口／插槽</mark>形式存在的时候，就是我们主板上那长长的槽
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686840264670-aa516198-b8da-4080-9a12-32912888cac6.png#averageHue=%234d4d2c&clientId=u872c5211-e7ca-4&from=paste&height=405&id=u2ea92172&originHeight=670&originWidth=785&originalType=binary&ratio=1&rotation=0&showTitle=false&size=635477&status=done&style=none&taskId=u56eeba5a-1027-4916-9324-e9d34a99732&title=&width=475)
目前的声卡和网卡都是主板集成了，不需要我们额外再插，所以**PCI-E插槽目前最大的作用就是插显卡**
PCI-E接口也可以转接成很多接口，比如USB3.0，Type-c，雷电3，又或者U.2，M.2

上面介绍的是PCI-E以接口形式存在，还有另一个情况，<mark style="background: #FFB8EBA6;">PCI-E以通道形式</mark>存<mark style="background: #BBFABBA6;"></mark>在
传统的SATA3接口固态硬盘采用的是AHCI协议，比如金士顿A400，三星860EVO，intel545S使用的都是SATA3接口，这种接口速率上限的理论值是750MB/S，但是实际上就只有600MB/S左右，所以这种固态硬盘速度都不超过600MB/S，这就是被SATA3这个接口的带宽限制了。
而为了摆脱限制，我们只能考虑换接口，PCI-E速率不是很快么，我们就用PCI-E好了，但是PCI-E体积太大怎么办，那么我们就缩小体积换个样子，这就是M.2接口，M.2接口你可以理解为他就是PCI-E接口，只是换了个形状而已。
所以这个时候，接口就是M.2，PCI-E在这里的作用就是扮演传输数据的通道了，而不是直接以接口存在

各代PCIe
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1686833145787-819acc8a-13f5-4fc8-bd7b-a1b0c6b2561c.png#averageHue=%23c3d6eb&clientId=u872c5211-e7ca-4&from=paste&id=uf7546bb0&originHeight=464&originWidth=834&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u90ed5a24-d886-49db-8d1f-50b29434db5&title=)

> PCIe所能承受的带宽一般以版本和长度来区分，PCIe3.0，X1长度所能承受的带宽是1GB/S，X2长度就是2GB/S，X4长度就是4GB/S，那X16长度就是16GB/S
> 几乎任何长度的PCIE设备只需要X1就可以运行，你可以把X16的显卡插在X1槽中(尾部非闭合)，你也可以把X1的设备插在X16槽中，这都是可以运行的，只是可能会带宽不足或者浪费带宽了
> 如果将PCIe 2.0卡放入PCIe 3.0插槽中，那么就只能使用到PCIe 2.0性能，是达不到PCIe 3.0的效果的


### 南桥芯片组、直连PCI-E、绕道PCI-E
<mark style="background: #D2B3FFA6;">我们不可能让所有的设备都直接去找CPU通讯</mark>，那我们就给CPU安排一个下手，显卡和内存由于对于延迟和带宽要求很高，还是由CPU来直接通讯，但是键盘鼠标，声卡网卡这些，就让这个下属去管，然后这个下属再给CPU汇报数据。这个用来交互数据的下属，就是主板南桥芯片组
CPU和南桥芯片组通过DMI总线（PCIe通道）交互
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686838115940-81c19217-6c81-46ee-ad18-b0bd22e0ddf9.png#averageHue=%23559933&clientId=u872c5211-e7ca-4&from=paste&height=818&id=uaedde507&originHeight=818&originWidth=1418&originalType=binary&ratio=1&rotation=0&showTitle=false&size=344452&status=done&style=none&taskId=ua14e360c-0733-4f93-ad9d-4132e0e4ae4&title=&width=1418)
上图 南桥芯片组和CPU之间不过也就PCIE4.0x8或PCIE4.0x4的带宽，怎么敢扩展出那么多的PCIE3.0  PCIE4.0来呢？因为现实中不太可能出现连接芯片组的扩展一起跑满，拥堵DMI的情况

### 具体主板举例
两个x16插槽的，比如微星 Z690 UNIFY DDR5 暗影主板
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686836983546-8712520f-f287-43b7-b1c7-4ffb3bf62c04.png#averageHue=%233a3d2b&clientId=u872c5211-e7ca-4&from=paste&height=317&id=u8f23031c&originHeight=405&originWidth=467&originalType=binary&ratio=1&rotation=0&showTitle=false&size=227749&status=done&style=none&taskId=uad9cfa4f-5733-476a-a83a-0d26fa2a7e0&title=&width=366)
这块主板有两个PCIE5.0 x16的插槽，都是直连CPU的，当把显卡插到第一个PCIE插槽时，就会把所有的x16带宽分配给显卡，但是，当再把任何PCIE设备，如显卡 声卡 网卡插到第二个PCIE插槽时，分配机制就变成了各自拥有x8的带宽，1X16变成2X8
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686836957207-f77f80df-5c26-4683-a99b-7227941a30a7.png#averageHue=%23616129&clientId=u872c5211-e7ca-4&from=paste&height=312&id=X6gjF&originHeight=391&originWidth=482&originalType=binary&ratio=1&rotation=0&showTitle=false&size=225546&status=done&style=none&taskId=ub9a576b7-e04a-4531-8363-34fdec350e3&title=&width=385)


只有一个PCIEx16插槽，其他PCIE插槽都是通过南桥芯片组扩展出来的，例如：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686837560931-197cfdea-391f-4775-bf44-b022d1d1a951.png#averageHue=%23277f7e&clientId=u872c5211-e7ca-4&from=paste&height=458&id=udb750236&originHeight=458&originWidth=955&originalType=binary&ratio=1&rotation=0&showTitle=false&size=493845&status=done&style=none&taskId=uf4b412fe-fa2b-4edb-abd0-5192e0116d1&title=&width=955)

微星Z690 TOMAHAWK WIFI DDR4 战斧主板
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686839911278-2b55fdb8-86b3-4fec-9913-69a912362be0.png#averageHue=%23288787&clientId=u872c5211-e7ca-4&from=paste&height=786&id=u49d80a8b&originHeight=786&originWidth=1106&originalType=binary&ratio=1&rotation=0&showTitle=false&size=810020&status=done&style=none&taskId=u9be95064-e520-42df-bbfc-fc726efa329&title=&width=1106)

## Intel芯片组
> Intel和AMD每发布一代CPU都会随之发布新的芯片组

高端芯片组Z系列：Z790
中端芯片组B系列：B760
低端芯片组H系列：H710
<mark style="background: #D2B3FFA6;">H和B系列不支持CPU超频，只有Z系列支持CPU超频（要超频还得CPU带K）</mark>

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686819946981-18f1b413-2d8e-4883-b275-91edb81343f4.png#averageHue=%23bbcdd6&clientId=u3f2a2254-babf-4&from=paste&height=1353&id=RaWS2&originHeight=1353&originWidth=693&originalType=binary&ratio=1&rotation=0&showTitle=false&size=514728&status=done&style=none&taskId=u88cb5056-c789-4dbc-83a4-a687f925de4&title=&width=693)

## H610 H670 B660 B760 Z690 Z790对比
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686823223113-66326875-cb8f-478c-a353-2337f7862911.png#averageHue=%23282535&clientId=u872c5211-e7ca-4&from=paste&height=624&id=mzBbs&originHeight=624&originWidth=1187&originalType=binary&ratio=1&rotation=0&showTitle=false&size=400444&status=done&style=none&taskId=u424b13f1-b308-484f-8584-a7c13f28543&title=&width=1187)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686841729803-2878acba-cf75-43df-a01b-425b3fbc1ee1.png#averageHue=%23303841&clientId=u20a8a4d7-c497-4&from=paste&height=732&id=kNaen&originHeight=732&originWidth=1556&originalType=binary&ratio=1&rotation=0&showTitle=false&size=417545&status=done&style=none&taskId=ufcfd38b7-87f1-4f69-86f4-3ee0381186e&title=&width=1556)

## 主板供电
> 定好CPU后，就要看主板的供电是否够用，主板供电如果不行，CPU就不能发挥全部性能，所以主板供电是否够用，是重中之重

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686844797634-77bba422-2e37-4e3b-9193-21dcbdbaf0a1.png#averageHue=%233d403e&clientId=u20a8a4d7-c497-4&from=paste&height=726&id=ufb03dbc0&originHeight=726&originWidth=1760&originalType=binary&ratio=1&rotation=0&showTitle=false&size=222079&status=done&style=none&taskId=u9ed9604b-46cc-47ea-b28f-9fb48ce9e29&title=&width=1760)

### 直出供电
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686847215290-482b389c-70e1-45e6-8f74-dfef908ff2f6.png#averageHue=%23494a49&clientId=u271066e3-b1ee-4&from=paste&height=110&id=uf53268b2&originHeight=110&originWidth=742&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35652&status=done&style=none&taskId=u79ae7fe2-7745-4a96-b576-91917899059&title=&width=742)
案例：
微星H410 BOMBER
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845047309-d8f49ab6-0ec8-42f8-b24e-7c263ca9bb8e.png#averageHue=%23247726&clientId=u20a8a4d7-c497-4&from=paste&height=771&id=u2f33b1ce&originHeight=771&originWidth=1013&originalType=binary&ratio=1&rotation=0&showTitle=false&size=844431&status=done&style=none&taskId=u00f9215f-40e1-4ac2-894c-5c759d52d2e&title=&width=1013)

华硕PRIME H410M-K
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845112641-062c9e1f-9a0e-473f-a0d2-cc36acb634ce.png#averageHue=%2337393e&clientId=u20a8a4d7-c497-4&from=paste&height=668&id=u66340d49&originHeight=668&originWidth=1237&originalType=binary&ratio=1&rotation=0&showTitle=false&size=763572&status=done&style=none&taskId=uabc0623d-0684-4fcd-9715-ffb76f6d54e&title=&width=1237)

微星B660M MORTAR WIFI DDR4 迫击炮
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845165708-2db9a1c8-81a4-4c8b-86fa-ada53237c9bd.png#averageHue=%23525963&clientId=u20a8a4d7-c497-4&from=paste&height=700&id=u6d65b8f9&originHeight=700&originWidth=1176&originalType=binary&ratio=1&rotation=0&showTitle=false&size=887608&status=done&style=none&taskId=ue675e21c-dabc-4267-bf75-1bcbd92899f&title=&width=1176)

### 并联供电
直出供电是PWM + MOS + 1个电感 + 电容构成
并联供电直接再加一个电感，每相供电搞两个电感分摊压力，这种设计不能增加供电能力，只能分摊供电压力
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845319890-ea022990-4c9a-4b10-ab69-9d590d80a9fc.png#averageHue=%23616363&clientId=u20a8a4d7-c497-4&from=paste&height=762&id=NkdtG&originHeight=762&originWidth=1750&originalType=binary&ratio=1&rotation=0&showTitle=false&size=268072&status=done&style=none&taskId=u258ccad3-2945-434e-8db5-c85d94bbf38&title=&width=1750)

案例：
微星H410M BOMBER
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845540192-9dd15e64-3fe8-4cf1-834a-14f4094b3e36.png#averageHue=%23298549&clientId=u20a8a4d7-c497-4&from=paste&height=704&id=u83478e06&originHeight=704&originWidth=1194&originalType=binary&ratio=1&rotation=0&showTitle=false&size=938051&status=done&style=none&taskId=ud6cb8b35-1a0a-4d36-af97-b5b6a2b2cf3&title=&width=1194)

### 倍相供电
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686845605914-66e66da8-3ad8-4d55-a826-7fd83dc47782.png#averageHue=%235e605f&clientId=u20a8a4d7-c497-4&from=paste&height=758&id=u49013ede&originHeight=758&originWidth=1768&originalType=binary&ratio=1&rotation=0&showTitle=false&size=288194&status=done&style=none&taskId=u3ec2c413-2284-42d7-ba0b-12d85eb54bc&title=&width=1768)

供电也不能单看相数，MOS和电感的规格也决定了供电能力，
另外散热片对供电也很重要，现在中高端主板基本都普及了散热片

## 其他参数规格
### 内存插槽数量
> 双内存槽、四内存插槽
> 小知识：<mark style="background: #BBFABBA6;">双内存槽主板的内存超频能力强于四内存插槽主板</mark>，目前最强的超频主板Z790 APEX就是双槽主板


### PCIE插槽
> PCIE插槽数量和布局
> 比如双显卡，就需要多个PCIE插槽
> 再比如显卡太厚，会挡住下面的PCIE插槽


### M.2插槽
> H610不会给PCIE4.0版本的M.2插槽，如果想用PCIE4.0版本的M.2插槽，最低也要B660

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686843615507-78431b61-eb62-4754-a72d-4e364daa3eda.png#averageHue=%23326f39&clientId=u20a8a4d7-c497-4&from=paste&height=732&id=uedfe407d&originHeight=732&originWidth=1714&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1284000&status=done&style=none&taskId=ue4ee04d3-ab74-4ffc-9b3e-666d5b38f94&title=&width=1714)

### 板载网卡
> 有线网卡、无线网卡

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686843809599-35626a65-670e-4d36-9adf-9ca719a4ded9.png#averageHue=%23324855&clientId=u20a8a4d7-c497-4&from=paste&height=537&id=u542e2cab&originHeight=537&originWidth=1726&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1221033&status=done&style=none&taskId=ub03159ee-f7a2-4a44-8f44-afcdb9cd0fb&title=&width=1726)

### SATA接口
> 现在m.2固态广泛普及，很多人不用机械硬盘和SATA固态硬盘了，一般都会给4或6个SATA接口，够用就行


### 前置Type-c接口
> 如果机箱支持type c，就需要主板支持，不然机箱的type c 就无用了


### 小4 pin pwm接针
> 风扇都是要接到小4 pin pwm接针上的，不过这个不太重要，就算不够，也可以用一分二、一分三的线去扩展

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686844227746-c884a664-5999-4988-97d5-a92321f54fb0.png#averageHue=%23383a41&clientId=u20a8a4d7-c497-4&from=paste&height=666&id=u5c727556&originHeight=666&originWidth=1592&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1227105&status=done&style=none&taskId=u56ed9e72-b462-4c0a-b059-a806959c26d&title=&width=1592)

### 5V3针ARGB接口
> 想要玩光，首选华硕，其次微星，别的一概不考虑，其次需要主板有5V3针ARGB接口，有些低端主板没有这接口，买之前看清楚


### 主板I/O接口
> 按需选择

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686844519018-a2f6d90d-8bad-4c69-845e-5dec9b59525c.png#averageHue=%23565a58&clientId=u20a8a4d7-c497-4&from=paste&height=784&id=ud9131554&originHeight=784&originWidth=1678&originalType=binary&ratio=1&rotation=0&showTitle=false&size=800007&status=done&style=none&taskId=u0ec9342d-16ab-44a4-b2c7-053e696afff&title=&width=1678)

## CPU主板搭配
> 13代CPU配套并同步上市的主板是700系列主板
13代CPU可以继续用B660和Z690，但是一定要让商家帮你升级BIOS，否则会点不亮
> 由于H710没上市（有人说称H710主板继续由入门级H610来担当），H610的m.2插槽不支持Pcie4.0
> B760与上一代B660一样，依然只支持超频内存，不支持对CPU进行超频，而H770这种中间定位比较尴尬的主板，基本是被市场忽视的产品，也是不支持CPU超频
CPU带K，选择Z系列主板，CPU不带K，选择B、H系列主板

i3-12100/F、i3-13100/F——H610主板
i5-12400/F、i5-12490F、——B660主板
i5-13400/F、i5-13490F、i7-12700/F——B660或B760主板
i5-12600K/F、i7-12700K/F、i9-12900K/F、i9-12900KS	——Z690主板
i7-13700K/F、i9-13900K/F——Z790主板

## 常见主板品牌分级
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686828505644-e432c283-b1a2-4fe0-991b-51bfc9eeb712.png#averageHue=%23406f6d&clientId=u872c5211-e7ca-4&from=paste&height=411&id=u7a78785d&originHeight=411&originWidth=926&originalType=binary&ratio=1&rotation=0&showTitle=false&size=198464&status=done&style=none&taskId=u9199c6ef-04c0-4602-9d9d-1d0dcbacfdb&title=&width=926)

### 华硕主板系列：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686827475110-b031cb6b-51ad-4f6b-883e-50ba4620dfe9.png#averageHue=%232b3f42&clientId=u872c5211-e7ca-4&from=paste&height=787&id=ubc31d7df&originHeight=787&originWidth=1851&originalType=binary&ratio=1&rotation=0&showTitle=false&size=874457&status=done&style=none&taskId=ub41560f6-816b-4997-8271-e0811475ee4&title=&width=1851)
> 售后政策：凭SN码个人送保，无需发票，使用ASUS华硕服务公众号进行售后申请及处理
> 质保年限：3年


华硕主板额外后缀含义：

- 芯片组带后M：MATX版型
- 芯片组带后i：ITX版型
- 后缀带D4：DDR4内存版本
- 后缀带D5：DDR5内存版本
- 后缀带R2.0：第二代版本
- 后缀带罗马数字Ⅱ：第二代版本
- 后缀带WIFI：板载无线网卡
- 后缀带GMZR：鬼灭之刃换皮联名版
- 后缀带ZAKU：高达扎古换皮联名版
- 后缀带GUNDAM：高达换皮联名版
- 后缀带GUNDAM EDITION：高达换皮联名版
### 微星主板系列：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686827894123-2839f886-2b1c-4ffc-868d-a37f004e7e96.png#averageHue=%232c4747&clientId=u872c5211-e7ca-4&from=paste&height=782&id=u57b6be80&originHeight=782&originWidth=1865&originalType=binary&ratio=1&rotation=0&showTitle=false&size=541206&status=done&style=none&taskId=u7d9cf068-b9fc-4826-a5e2-a45210e90b5&title=&width=1865)
> 售后政策：个人送保，无需发票
> 质保年限：3年
> 丐中丐 高丐，厂家没有针对这个系列出产品线，不代表没有丐版



# 内存
## DDR内存时代
> DDR=Double Data Rate 也就是双倍速率的意思
> 目前正在处于DDR4主流，DDR5崛起的时代，DDR技术每一次技术迭代，都基本实现了频率翻倍，读写速度越来越快，工作电压越来越低

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686940537301-136d7e34-469e-4cff-a879-46de840bec64.png#averageHue=%2329292f&clientId=u542c054f-1480-4&from=paste&height=731&id=u02a1b3c2&originHeight=731&originWidth=1469&originalType=binary&ratio=1&rotation=0&showTitle=false&size=252783&status=done&style=none&taskId=u221e840f-17fc-4e17-91ab-b0f414bc633&title=&width=1469)
购买时要看主板支持DDR4还是DDR5

## 内存容量
> 绝大多数游戏都是吃不满16G内存的，16G内存能满足目前99%的游戏需求

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686940794757-6ddef23d-7ee4-4f37-b8d4-61b86b0b2f04.png#averageHue=%233a3937&clientId=u542c054f-1480-4&from=paste&height=765&id=u158da860&originHeight=765&originWidth=1834&originalType=binary&ratio=1&rotation=0&showTitle=false&size=403638&status=done&style=none&taskId=uf7bef828-9fe2-4fa0-b365-d56f5742341&title=&width=1834)

## 内存频率和时序
频率：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686940918640-109d954b-c6a2-4110-8b62-4af9fbb00278.png#averageHue=%2328282d&clientId=u542c054f-1480-4&from=paste&height=616&id=u8ecd9b4b&originHeight=616&originWidth=1322&originalType=binary&ratio=1&rotation=0&showTitle=false&size=216012&status=done&style=none&taskId=u6d79d59d-0318-45cf-8889-e11db536499&title=&width=1322)
> 频率越高，数据的传输速率越高，但是不用一味的追求频率
> 目前的DDR4内存，综合价格和性能，3200Mhz和3600Mhz是比较甜品的频率，建议不会超频，不想折腾的玩家买这两种即可，前提是主板支持这个频率


时序：
> 可以简单理解为内存的延迟，延迟越低，意味着CPU与内存交换数据间隔时间越短，性能相对越强

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686941293147-dc0e96ff-4b40-48dd-82c7-b239e6dadf2a.png#averageHue=%23292a30&clientId=u542c054f-1480-4&from=paste&height=493&id=ua058eff3&originHeight=493&originWidth=1663&originalType=binary&ratio=1&rotation=0&showTitle=false&size=176097&status=done&style=none&taskId=ue1058427-1597-4543-8782-d49f71ca5ac&title=&width=1663)
> 建议不会超频，不想折腾的玩家买C16甜品时序

时序不变，频率越高越好，频率不变，时序越低越好
频率和时序，主要针对游戏玩家，如果只是办公，考虑容量即可

## 内存颗粒
颗粒是内存上最重要，科技含量最高的组成成分，目前能制造内存颗粒的厂家全世界都不多，主要有<mark style="background: #FF5582A6;">三星、镁光、海力士、合肥长鑫</mark>等等，其中三星、镁光、海力士最为强悍，属于是内存颗粒界的御三家，加一起占了90%，像金士顿、芝奇、威刚这些内存厂商都要依赖御三家或者长鑫的内存颗粒，他们自己没有能力生产内存颗粒
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686942033042-adb5394d-0cfa-4408-8609-90e602104660.png#averageHue=%23292e38&clientId=u542c054f-1480-4&from=paste&height=422&id=u4419949d&originHeight=422&originWidth=1625&originalType=binary&ratio=1&rotation=0&showTitle=false&size=163089&status=done&style=none&taskId=u1a6c8fa6-6940-4451-a635-9727edd704e&title=&width=1625)

颗粒不同，体质不同，最终会影响内存的频率和时序，颗粒越牛逼，越能超频

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686942469954-014a2ed9-fe7a-401a-947d-dee20f4b190f.png#averageHue=%23383a3f&clientId=u542c054f-1480-4&from=paste&height=796&id=u15faca49&originHeight=796&originWidth=1184&originalType=binary&ratio=1&rotation=0&showTitle=false&size=317630&status=done&style=none&taskId=ue501573e-184e-4534-aa63-bcbf520c842&title=&width=1184)
颗粒是很重要的，当你看到一根2666Mhz，但是采用三星B-die颗粒，请不要怀疑它的实力，他的真实能力可以秒杀一大票市面上高频内存
但是对于不超频的普通用户来说，颗粒就显得不那么重要了

## XMP
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686943357280-b2fdea47-29b6-4435-a019-4cb29f8620d4.png#averageHue=%23fbfafa&clientId=u542c054f-1480-4&from=paste&height=525&id=u49b4e1f7&originHeight=525&originWidth=1070&originalType=binary&ratio=1&rotation=0&showTitle=false&size=48730&status=done&style=none&taskId=uae323b4b-dad0-4799-84d3-c73ae08f519&title=&width=1070)

高频内存并不是天生的，内存厂商经过测速，将一套比较安全合理的频率和时序写到内存的SPD信息中，把内存买回来用的时候，需要进到<mark style="background: #D2B3FFA6;">主板BIOS里开启XMP功能</mark>，去读取厂商预设的这套高频数值，才能让高频内存生效

## 内存通道/双通道优先24其次13
主流消费级主板，CPU和内存之间都是双通道设计，如果是2个插槽，则每个插槽各是一个通道，如果是4个插槽，则每2个插槽一个通道
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686943819735-66d0d2bc-4764-4c7d-995f-a2b252a8e7f4.png#averageHue=%232a6e4b&clientId=u542c054f-1480-4&from=paste&height=667&id=u6e2406dc&originHeight=667&originWidth=1315&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1324114&status=done&style=none&taskId=udbf68719-12db-4527-849c-7e06240bec3&title=&width=1315)
建议买内存的时候，<mark style="background: #FFB8EBA6;">能双不单，能2不4：</mark>
如果只有1根内存，就只能走单通道，性能是完全不如双通道的，虽然现在DDR5内存可以实现单根内存走双通道，但本质上是残缺的双通道，仍然需要两根内存才能享受满血的双通道所以双8G比单根16G内存效能高很多
能2不4，对于追求高频或者手动超频的玩家，能插两根就尽量别插4根，比如要32G，建议买两根16G，不要买4根8G，因为内存数量越多，同步就越难，也就越难冲高频（玩灯除外）

两根内存插在2 4或者1 3上形成双通道，24为优先插槽，其次是13
主要是因为主板的内存走线，Z490以后，主板大多都采用了一种名为菊花链型D-type的内存走线方式，就是从CPU出引出两条内存线路，一个接在1槽上，然后再从1槽连一根线连到2槽，这是一个内存通道，第二个内存通道则是连接到3槽上，然后再转接到4槽
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686948804363-5fcda3d2-85f9-4b6f-bd71-639075bdc0f3.png#averageHue=%23c9c6ce&clientId=u88f3de78-2c1b-4&from=paste&height=403&id=ubcf2b651&originHeight=588&originWidth=825&originalType=binary&ratio=1&rotation=0&showTitle=false&size=43926&status=done&style=none&taskId=u9290b019-728c-4afa-9cd8-1dda94dd3bd&title=&width=565)

如果插1 3 就会有2条残线，导致并行的串扰，所以会导致电气性能的降低
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686949482127-6dcb7f02-35df-4ee9-a194-b40e314fb224.png#averageHue=%23c9c7ce&clientId=u88f3de78-2c1b-4&from=paste&height=410&id=OIp8Y&originHeight=597&originWidth=805&originalType=binary&ratio=1&rotation=0&showTitle=false&size=68153&status=done&style=none&taskId=u764bf124-db82-4a91-8a41-7f77cd06199&title=&width=553)

如果插2 4，两个通道都完整，没有残线，此时电气性能最大
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686949433683-ee31aac2-cbc2-44f0-9ffa-d6575499e4bb.png#averageHue=%23c9c6ce&clientId=u88f3de78-2c1b-4&from=paste&height=461&id=u9b55167d&originHeight=599&originWidth=728&originalType=binary&ratio=1&rotation=0&showTitle=false&size=62240&status=done&style=none&taskId=uce748062-84d3-4c24-b82d-ff51ffe714c&title=&width=560)

如果插满4根，通道1的两条内存到达CPU的物理距离不同，通道2的两条内存到达CPU的物理距离也不同，并行受到外部干扰，这种情况下，4条内存就不如两条内存了
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686949095796-cf6008cc-0867-40f1-92d2-5344c716e5e3.png#averageHue=%23585366&clientId=u88f3de78-2c1b-4&from=paste&height=443&id=u2ad1dfd0&originHeight=443&originWidth=1253&originalType=binary&ratio=1&rotation=0&showTitle=false&size=275986&status=done&style=none&taskId=u4d1e2376-9962-45e7-b760-aa8c584da83&title=&width=1253)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686949774284-b5e5d4ff-ccb7-4050-b5af-75dda8dc51e6.png#averageHue=%23b9b7c0&clientId=u88f3de78-2c1b-4&from=paste&height=311&id=u0a7baca8&originHeight=311&originWidth=1524&originalType=binary&ratio=1&rotation=0&showTitle=false&size=600799&status=done&style=none&taskId=u9b53f98e-b39d-4ca0-bbb4-9b6aa02305f&title=&width=1524)

在大部分用途中，<mark style="background: #FF5582A6;">双条内存这种选择更具有性价比</mark>，也是D-type布线表现更好的搭配

双通道双内存条的主板<mark style="background: #FF5582A6;">更容易超频</mark>，因为没有残线产生的干扰，并且CPU到内存插槽的距离比4插槽的距离短一些，所以信号强度就比较高了

## 套条和连号内存
超频爱好者可以关注，原因就是颗粒体质问题，套装和连号的内存条，套条可以保证这两根内存条体质差异很小，更易于超频，SN码连号，说明这两根内存大概率是前后脚从生产线上下来的，体质更接近
不超频的不需要关注，基本没什么用，用不着讲究这个，只需要注意，买同品牌、同容量、同型号、同频率的内存即可，否则可能造成兼容性问题

## 马甲条和灯条
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686944448388-cf909a91-7f2a-4f30-95fc-2c205622cfbc.png#averageHue=%2354585c&clientId=u542c054f-1480-4&from=paste&height=731&id=ub7bffe8f&originHeight=731&originWidth=1119&originalType=binary&ratio=1&rotation=0&showTitle=false&size=544505&status=done&style=none&taskId=u83b20f9e-0a73-4fb6-b29c-7c2fe49f3a9&title=&width=1119)
马甲可以辅助散热，灯条有灯光
注意：灯条需要搭配合适的主板才能实现神光同步，一般在详情页可以找到该内存所能支持的主板品牌等效软件，玩灯，首选华硕，其次微星

## 根据CPU搭配内存
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686944819173-76c30881-f97b-4505-a385-48d7d653ff00.png#averageHue=%2345494e&clientId=u542c054f-1480-4&from=paste&height=793&id=ua1a5f349&originHeight=793&originWidth=1809&originalType=binary&ratio=1&rotation=0&showTitle=false&size=516012&status=done&style=none&taskId=u80c02f9a-e494-42e9-952c-444e594cfca&title=&width=1809)

## 内存品牌
> 网上看了一些品牌排行和推荐，虽然大家说法不一，但是也能看出一些东西
> 主要品牌有：金士顿、芝奇、海盗船、威刚、英睿达、光威、影驰、金百达等


一些评价和排行：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951474412-394b2feb-ae52-44c4-92cf-08ac6ed02a59.png#averageHue=%233c1d11&clientId=u88f3de78-2c1b-4&from=paste&height=120&id=ub68dfbee&originHeight=120&originWidth=958&originalType=binary&ratio=1&rotation=0&showTitle=false&size=112709&status=done&style=none&taskId=uf8217542-74ee-4dda-8bb8-07a50a43b0b&title=&width=958)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951513957-9fab3edc-2103-434a-a350-7844ff7bb7e2.png#averageHue=%230b0c09&clientId=u88f3de78-2c1b-4&from=paste&height=127&id=u274d22d3&originHeight=127&originWidth=938&originalType=binary&ratio=1&rotation=0&showTitle=false&size=121817&status=done&style=none&taskId=uc1f82c1e-e870-488a-9ac9-80f062e86f0&title=&width=938)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951661216-11c7454f-e7d3-4605-aae7-9d98e9955041.png#averageHue=%23291b12&clientId=u88f3de78-2c1b-4&from=paste&height=64&id=u16be1057&originHeight=64&originWidth=888&originalType=binary&ratio=1&rotation=0&showTitle=false&size=37290&status=done&style=none&taskId=u732133e8-b375-45b6-aca0-f41415c6356&title=&width=888)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951675410-9081622b-9a64-4a43-8127-9166c4821a20.png#averageHue=%231a0c0c&clientId=u88f3de78-2c1b-4&from=paste&height=55&id=u7591e151&originHeight=55&originWidth=854&originalType=binary&ratio=1&rotation=0&showTitle=false&size=39074&status=done&style=none&taskId=u1f404ee5-f1bb-418e-8ef3-7097290f3da&title=&width=854)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951718887-5fa98aa6-ba39-41b9-ada2-29a15d4e0135.png#averageHue=%233c2314&clientId=u88f3de78-2c1b-4&from=paste&height=136&id=u01e05b45&originHeight=136&originWidth=949&originalType=binary&ratio=1&rotation=0&showTitle=false&size=133585&status=done&style=none&taskId=u48b23b5c-2347-43e0-bdb4-5a893265f3c&title=&width=949)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951762649-9b9f62b7-4077-4939-ad4c-b28cfb1427d8.png#averageHue=%230c0c0a&clientId=u88f3de78-2c1b-4&from=paste&height=84&id=u82a4fbe4&originHeight=84&originWidth=950&originalType=binary&ratio=1&rotation=0&showTitle=false&size=76824&status=done&style=none&taskId=u1194d3b3-e136-45a9-8f25-3892d7982ba&title=&width=950)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951799469-c6d7c7e1-5fa8-47c9-84c7-96558ef6ac6c.png#averageHue=%23411e12&clientId=u88f3de78-2c1b-4&from=paste&height=88&id=ue4d26d27&originHeight=88&originWidth=955&originalType=binary&ratio=1&rotation=0&showTitle=false&size=92949&status=done&style=none&taskId=u6f7a92a0-bbc0-4fd4-a1b1-592f4456e08&title=&width=955)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951825562-7b756f63-f512-49fd-98a9-77d081cfbdb5.png#averageHue=%23060d06&clientId=u88f3de78-2c1b-4&from=paste&height=86&id=ud36eefdf&originHeight=86&originWidth=938&originalType=binary&ratio=1&rotation=0&showTitle=false&size=87743&status=done&style=none&taskId=u79508e67-6796-4c2b-8d2a-1bf5d354c21&title=&width=938)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951851996-6405dfe2-81d0-4121-8bb0-0b4d7ca09a51.png#averageHue=%23392215&clientId=u88f3de78-2c1b-4&from=paste&height=121&id=u86d4ed4c&originHeight=121&originWidth=937&originalType=binary&ratio=1&rotation=0&showTitle=false&size=117776&status=done&style=none&taskId=u43a01674-9d5c-4477-8cc6-d86e85df85b&title=&width=937)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951929228-126ddbf0-a357-48aa-83ac-3aa78fca31a7.png#averageHue=%230b0c09&clientId=u88f3de78-2c1b-4&from=paste&height=57&id=uc08f694c&originHeight=57&originWidth=940&originalType=binary&ratio=1&rotation=0&showTitle=false&size=45106&status=done&style=none&taskId=uffeccec2-8863-42bb-83ff-bbaadfebf77&title=&width=940)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686951987874-42a10469-242b-4d98-a349-c35979ebc1d6.png#averageHue=%23200c0c&clientId=u88f3de78-2c1b-4&from=paste&height=187&id=ubc5387f1&originHeight=187&originWidth=795&originalType=binary&ratio=1&rotation=0&showTitle=false&size=65484&status=done&style=none&taskId=u65dda879-d402-4254-b39a-aa9a66a55a0&title=&width=795)



![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686950989487-a7947c19-d4b7-4b4a-95ba-2b0dd2cff9a5.png#averageHue=%23106098&clientId=u88f3de78-2c1b-4&from=paste&height=769&id=udc98a430&originHeight=769&originWidth=1784&originalType=binary&ratio=1&rotation=0&showTitle=false&size=977700&status=done&style=none&taskId=u33760a43-5cf5-447e-9cd6-5bb9d892031&title=&width=1784)


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954264456-f8f034b8-33a1-481b-ab38-8d2b0da35929.png#averageHue=%238db8b9&clientId=u88f3de78-2c1b-4&from=paste&height=573&id=u9f76857b&originHeight=573&originWidth=557&originalType=binary&ratio=1&rotation=0&showTitle=false&size=324834&status=done&style=none&taskId=u2ad91636-320d-4a5d-b879-fcfdce674fe&title=&width=557)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954288257-0555a03e-c74d-4b4d-95bd-34a56f413d7a.png#averageHue=%238db5b7&clientId=u88f3de78-2c1b-4&from=paste&height=586&id=u7fd82786&originHeight=586&originWidth=572&originalType=binary&ratio=1&rotation=0&showTitle=false&size=382509&status=done&style=none&taskId=u555e13ba-420b-461e-a451-5c653652d9f&title=&width=572)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954303567-779a91f8-6e0a-4865-940d-ca8c7408f81e.png#averageHue=%2389b2b4&clientId=u88f3de78-2c1b-4&from=paste&height=587&id=ua26f0096&originHeight=587&originWidth=567&originalType=binary&ratio=1&rotation=0&showTitle=false&size=360065&status=done&style=none&taskId=u6130dde3-1c0e-4726-a03e-0cfe4b9d79f&title=&width=567)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954323449-da10a7e6-8c95-4da5-8ee0-4dd9103a98b2.png#averageHue=%2386acae&clientId=u88f3de78-2c1b-4&from=paste&height=584&id=uec20c6cf&originHeight=584&originWidth=566&originalType=binary&ratio=1&rotation=0&showTitle=false&size=361530&status=done&style=none&taskId=u64345b34-d0c8-43da-90da-4de51eeec33&title=&width=566)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954336219-819c86f6-9670-43a1-b60b-9808eb6bba42.png#averageHue=%238fa8b0&clientId=u88f3de78-2c1b-4&from=paste&height=579&id=u65e409f3&originHeight=579&originWidth=566&originalType=binary&ratio=1&rotation=0&showTitle=false&size=351058&status=done&style=none&taskId=ufd39f796-135e-4de8-b90e-0ff547b647a&title=&width=566)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954355690-48130a62-dcd9-4368-beac-39e1b5088a11.png#averageHue=%238ea5af&clientId=u88f3de78-2c1b-4&from=paste&height=586&id=uc764520a&originHeight=586&originWidth=567&originalType=binary&ratio=1&rotation=0&showTitle=false&size=373401&status=done&style=none&taskId=u341a9b35-3c9c-4815-88d1-6d114766a23&title=&width=567)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686954368058-086d9db4-be6a-4a14-b3af-3cd043792290.png#averageHue=%238da4ae&clientId=u88f3de78-2c1b-4&from=paste&height=584&id=uf639ef30&originHeight=584&originWidth=567&originalType=binary&ratio=1&rotation=0&showTitle=false&size=362404&status=done&style=none&taskId=u90608da3-effa-4ed4-9cdb-2b2799f4f2b&title=&width=567)


# 关于超频
> 一台电脑可以超频的硬件有**CPU、显卡和内存**，所以只有CPU超频、显卡超频、内存超频

> 人为的提高硬件的出厂频率，从而得到性能的提升，<mark style="background: #FF5582A6;">压榨</mark>硬件的性能
> 以前的硬件超频后性能提升比较大，所以玩家热衷于超频，然而随着技术的发展，可超频的空间越来越小，厂商的官方自动超频技术越来越成熟，现在产品分级更细了，非生产力的性能已经过剩，超频后功耗会增加，为了那点很小的提升，还不如直接升级硬件，现在超频就是给有兴趣爱好的玩家折腾的，好玩有趣大于实用

## cpu超频：
Intel芯片组，H和B系列不支持CPU超频，<mark style="background: #FF5582A6;">只有Z系列支持CPU超频</mark>。
CPU超频需要CPU和主板同时支持才行。
比方说i5 7500不能超频，配上z270支持超频的主板，还是不能超频。
反过来，i5 7600k能超频，但配上不支持超频的b250主板，还是不能超频。
<mark style="background: #FF5582A6;">只有主板和CPU两者同时支持超频时，才能超频</mark>

## 显卡超频：
<mark style="background: #FF5582A6;">显卡超频跟主板无关</mark>
显卡能不能超频？可以 , 但要看<mark style="background: #FF5582A6;">体质</mark>跟版本
一般来说，<mark style="background: #D2B3FFA6;">OC版</mark>，非公版的都可以超
公版，高频版的都超不了多少就不能超了!
显卡超频能力，和显卡自身体质，原厂工作频率超过公版频率多少，超频后的功耗、温度，还有电源额定功率有很大关系

## 内存超频：
> 内存都会标注频率，2666MHz、3200MHz、3600MHz、4800MHz、5600MHz、6000MHz等，根据需求选。（注：高频内存需要进bios开启xmp，不然<mark style="background: #FF5582A6;">D4默频2666MHz运行，D5默认4800MHz运行</mark>）
> （超频党是选内存颗粒，不超频就是直接选频率）

内存在出厂的时候就会有一个默认内存频率，也就是我们买内存的时候看到标签上的频率参数。

不同的<mark style="background: #ADCCFFA6;">CPU对内存频率的支持不同</mark>，<mark style="background: #ABF7F7A6;"></mark>例如i3-9350K支持的最大内存频率2400MHz，i7-8700支持的最大则可以达到2666MHz

<mark style="background: #BBFABBA6;">主板上同样有内存频率的限制</mark>

CPU和主板，哪一个才是内存频率真正的主导者？
这里分为两者情况——超频和不超频
<mark style="background: #FFB8EBA6;">不超频，“最低原则”决定内存频率</mark>
就是说在不超频的情况下，内存可以运行多高的频率，由<mark style="background: #BBFABBA6;">CPU支持的最大频率</mark>、<mark style="background: #BBFABBA6;">主板支持的最大频率</mark>、<mark style="background: #BBFABBA6;">内存自身的默认频率</mark>三者中的最低频率决定
假如内存默认频率2133MHz，CPU是i7-7700K（支持内存频率2400MHz）,主板是Z270（支持内存频率2400MHz）,那么内存频率只能运行在2133MHz；
假如内存默认频率2400MHz，CPU是i7-7700K（支持内存频率2400MHz）,主板是Z170（支持内存频率2133MHz）,那么内存频率也只能运行在2133MHz；
假如内存默认频率3600MHz，CPU是i9-9900K（支持内存频率2666MHz）,主板是Z390（支持内存频率2666MHz）,那么内存频率以CPU和主板支持的频率为准，即2666MHz

<mark style="background: #D2B3FFA6;">超频，内存本身最大的频率和主板超频的最大频率决定内存频率</mark>
我们以Intel平台为例。因为Intel平台的B系列和几乎全部的H系列主板无法对内存超频，就按以上的不超频，”最低原则“决定内存频率，能超频的基本是Z系列，如果想要使用高频内存或者超频，务必要配备Z系列主板。
如果你的主板和内存都支持超频，那么内存的默认频率、主板支持的默认内存频率和CPU支持的默认内存频率都将被忽略不计。这时候限制条件只有2个：内存条最大频率和主板超频的最大频率。
内存条最大频率很大程度上由内存体质决定。例如同样是DDR4-3600 8G*2内存，有些只能超到4000MHz，而有些可以超到4600MHz+（此处影驰HOF Ⅱ DDR4-3600 8G*2应该有掌声）。
但即便内存本身可以超到那么高的频率，也不意味着内存就一定能以运行得了那么高的频率。因为主板能支持内存频率多高是关键。
举个例子，假如主板最高只支持内存超到4000MHz，即便影驰HOF Ⅱ DDR4-3600 本身可以达到4600MHz+，但迫于主板的限制，最高也只能超到4000MHz+。
最后，我们来总结一下：主板、CPU和内存本身这三条是限制内存默认频率的关键；而在超频的时候，内存本身和主板支持的最高内存频率，决定了内存可以运行的最高频率。


# 硬盘
## 分类
> 4种
> 机械硬盘（3.5/2.5寸）
> 2.5寸固态
> PCIe固态
> M.2固态（当前主流）

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686850109237-7d371b29-2d3c-4c5d-bcd2-abf06b9312f5.png#averageHue=%23d1d1d1&clientId=u271066e3-b1ee-4&from=paste&height=550&id=B1okV&originHeight=550&originWidth=1656&originalType=binary&ratio=1&rotation=0&showTitle=false&size=320537&status=done&style=none&taskId=u45094719-7b8f-485e-aa6e-6eace9a72be&title=&width=1656)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686955369245-19263d5a-0761-4b59-9832-38bab386bee1.png#averageHue=%232c2524&clientId=u88f3de78-2c1b-4&from=paste&height=885&id=ub3e1a617&originHeight=885&originWidth=1861&originalType=binary&ratio=1&rotation=0&showTitle=false&size=492979&status=done&style=none&taskId=u595d6363-2a38-4b38-aed0-a791b9c4ad8&title=&width=1861)
> 如果选PCIe4.0x4的硬盘，前提是主板要支持PCIe4.0
> 另外，PCIe4.0是向下兼容的，如果主板和CPU是支持PCIe4.0的，还是可以在主板上用PCIe3.0的固态，不用担心不兼容


## 品牌排行
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686956793226-0bd6d8ff-82e4-4dd3-9ed0-515369d68ead.png#averageHue=%23ebe8e8&clientId=u88f3de78-2c1b-4&from=paste&height=706&id=u1ad514a8&originHeight=706&originWidth=1119&originalType=binary&ratio=1&rotation=0&showTitle=false&size=452833&status=done&style=none&taskId=u4507ff0e-e689-4eed-b41e-d302f8ae5c0&title=&width=1119)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686956814430-f9a2c18c-7e87-4eaf-b80a-394fd4bece96.png#averageHue=%23edeaea&clientId=u88f3de78-2c1b-4&from=paste&height=714&id=u8b93f46d&originHeight=714&originWidth=1162&originalType=binary&ratio=1&rotation=0&showTitle=false&size=433736&status=done&style=none&taskId=u564c78d2-0ca3-4c27-81e6-2b591f15d9d&title=&width=1162)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686956831237-64fb7c21-8eb9-4bf9-abb3-f661450df681.png#averageHue=%23f3f2f2&clientId=u88f3de78-2c1b-4&from=paste&height=702&id=u08d8bf04&originHeight=702&originWidth=1121&originalType=binary&ratio=1&rotation=0&showTitle=false&size=187879&status=done&style=none&taskId=u6b1901a1-d89b-47df-bfd5-bae99fe253a&title=&width=1121)


![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686956987497-c7858242-4a52-4bb5-9178-1fa4da2c6b42.png#averageHue=%23e8e7e7&clientId=u88f3de78-2c1b-4&from=paste&height=550&id=u4c949731&originHeight=550&originWidth=575&originalType=binary&ratio=1&rotation=0&showTitle=false&size=224164&status=done&style=none&taskId=u14adb155-f329-4eaa-a267-3487e679270&title=&width=575)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686957006608-a57c3792-28ff-4496-9de5-8d96814946c3.png#averageHue=%23e7e5e5&clientId=u88f3de78-2c1b-4&from=paste&height=617&id=ub8c95410&originHeight=617&originWidth=579&originalType=binary&ratio=1&rotation=0&showTitle=false&size=254236&status=done&style=none&taskId=u02b6fd14-6363-4867-ae36-0e3f8750233&title=&width=579)



# 电源
> 电脑里两个吃电大户， **cpu**和**显卡**，电源的选择只要根据这两的功耗决定
> cpu和显卡占据了90%的功耗，（cpu功耗+显卡功耗+100）* 1.2 = 所需要的电源瓦数


## CPU功耗对照表
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686820601259-6970868f-ae25-4023-8f87-5e827886b676.png#averageHue=%231a1a1a&clientId=u3f2a2254-babf-4&from=paste&height=793&id=ua5617e10&originHeight=793&originWidth=1291&originalType=binary&ratio=1&rotation=0&showTitle=false&size=444413&status=done&style=none&taskId=u20918d7f-ce1d-47a1-aaa0-cfd05c9ce3f&title=&width=1291)

## 显卡功耗对照表
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686820664457-09053887-2a02-4cf8-a465-153f67f238ae.png#averageHue=%231c1c1c&clientId=u3f2a2254-babf-4&from=paste&height=828&id=ubb154222&originHeight=828&originWidth=1310&originalType=binary&ratio=1&rotation=0&showTitle=false&size=490232&status=done&style=none&taskId=u2fe8215e-6db0-4693-ac8e-e9b421510f6&title=&width=1310)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686820692235-cf1da5de-3d05-4b64-bc63-7f33d31c7ef6.png#averageHue=%23181818&clientId=u3f2a2254-babf-4&from=paste&height=815&id=ufa53d07c&originHeight=815&originWidth=1319&originalType=binary&ratio=1&rotation=0&showTitle=false&size=417509&status=done&style=none&taskId=ub4d6610b-6ec3-464a-a01a-d6a1a64f39e&title=&width=1319)

## 华硕官方电源功率参考建议
电源功率选择可以直接参考华硕官方给出的电源功率参考建议
![](https://cdn.nlark.com/yuque/0/2023/png/663445/1686812068399-4a2b1f68-9028-48dc-aca9-43da500924da.png#averageHue=%23795b43&clientId=u3f2a2254-babf-4&from=paste&id=ua3db6f59&originHeight=916&originWidth=720&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=u19dbfb17-f554-4105-a894-700e46a58d0&title=)

![](https://cdn.nlark.com/yuque/0/2023/png/663445/1686812305040-35b350a5-1dd1-4942-922b-46b8c983109e.png#averageHue=%237c573f&clientId=u3f2a2254-babf-4&from=paste&id=u69b391bc&originHeight=1007&originWidth=720&originalType=url&ratio=1&rotation=0&showTitle=false&status=done&style=none&taskId=uebb008ab-1cf6-498d-b979-8e0047ee4ab&title=)

## 电源品牌
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686637131820-2a1064dd-6761-45c0-b4f1-3516ca1135b4.png#averageHue=%232e2f4c&clientId=ubff19bce-2bb4-4&from=paste&height=600&id=u88391419&originHeight=600&originWidth=1727&originalType=binary&ratio=1&rotation=0&showTitle=false&size=690287&status=done&style=none&taskId=u742cf0df-4f33-46fa-9d2e-2bfe7bb9ab7&title=&width=1727)


# 散热器
> 帮助CPU散热
> 如果CPU自带了散热器，可以使用自带的散热器。自带的散热是能够满足正常使用需求的


## 种类
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686637240365-bab238be-f0e2-438d-ad75-3d88a5e43d61.png#averageHue=%23737340&clientId=ubff19bce-2bb4-4&from=paste&height=728&id=u77e3394c&originHeight=728&originWidth=1868&originalType=binary&ratio=1&rotation=0&showTitle=false&size=496188&status=done&style=none&taskId=uca0f46be-9638-46f5-a47d-073a8bb55d7&title=&width=1868)
> <mark style="background: #FF5582A6;">散热器不等于风扇</mark>

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686849162197-880d264c-f548-40a1-bd01-2eb0ee657888.png#averageHue=%23cdd1d0&clientId=u271066e3-b1ee-4&from=paste&height=338&id=u34f3d287&originHeight=338&originWidth=1023&originalType=binary&ratio=1&rotation=0&showTitle=false&size=342649&status=done&style=none&taskId=u7d1d0eea-ffd9-4714-9def-fadbfd52036&title=&width=1023)
## CPU与散热器搭配
> 由于机箱兼容问题，买的时候要看下机箱支持的散热系统尺寸，机箱的规格参数中会标注


### 风冷
入门级风冷--适合搭配 i5-13400/F，5600X，i5-12400/F，12490F等1500元以下价位的处理器
可选择**九州风神的玄冰400**，**雅浚B3**和**利民的AS120**

双风扇紧凑型风冷--适合搭配 5600X或i5-13490F，i7-12700，i5-12600KF等处理器
**雅浚G3**，**九州风神玄冰400双刃**，**利民AS120PLUS**。紧凑型的双风扇散热相对小巧,不易挡住内存

大型风冷--适合搭配 12600K，13600K，12700，5700X，5800X，7600X，7700X
大型风冷比较臃肿,适合不想使用水冷的用户。可以搭配intel i7处理器和AMD的5800X等8核的处理器。对于intel带K的i7处理器，还是建议使用更好的风冷或360水冷。

中高端风冷散热--适合搭配 i7-12700K，i7-13700K，5800X，7700X
300元附近的风冷建议考虑**利民的FC140，FS140，U120EX，九州风神 冰立方**等。

高端风冷--适合搭配 i7-12700K，i7-13700K，5800X，5900X，7900X
目前顶级的大型风冷有**九州风神的阿辛3代**，**利民银箭**，**猫头鹰NH-D15**。建议搭配8核心的处理器。这类型的风冷散热性能也就和好点的240水冷差不多，接近于主流的360散热水平。8核以上的处理器还是建议使用360水冷。
九州风神的阿辛3代采用的是7热管。利民银箭采用的是8热管。猫头鹰NH-D15是6热管。猫头鹰NH-D15的静音性能比较出色。

### 水冷
120水冷推荐--适合搭配 13490F，12600K，5600X
120水冷属于有点鸡肋的产品，使用120水冷的好处在于可以使机箱更整洁，更有利于侧透机箱展现ARGB光效。建议4核及6核的处理器使用120水冷。目前市面上的大部分机箱都支持120水冷(安装在机箱后部)。
120水冷推荐EK的AIO 120 D-RGB和恩杰的海妖M22。EK的AIO 120 D-RGB的冷头和风扇带有RGB灯效。恩杰海妖M22的冷头带有RGB光效。


240水冷推荐--适合搭配 12600K，13600K，13700，12700K，5800X，7600X，7700X。
240水冷的选择比较多，比较热门的有九州风神的堡垒240。利民的冰封系列240水冷也不错。高端的有海盗船的H100i，恩杰X53等等。建议搭配8核处理器和6核带K的处理器。如13600K,13700，12700K,12600K,11600K,AMD的5800X等。

360水冷推荐--适合搭配 i7,i9带K或X的处理器，5900X，5950X
比较热门的360水冷有堡垒360，恩杰海妖X73，海盗船H150I，华硕ROG的飞龙系列。
性价比高的360水冷（500元左右）可以选择利民的冰封系列，酷冷至尊的B360系列，以及网红瓦尔基里。瓦尔基里的水冷价格不贵，而且提供5年的质保。
高端360水冷可以选择恩杰的Z73或ROG的龙神二代。
360水冷长度比较长，选择机箱的时候建议选择支持顶部安装360水冷的机箱，这样有利于组将一个优良的风道，可以让空气从机箱前部进入，从顶部及尾部排出，这样显卡就不会吃CPU的热气。

280水冷推荐--适合搭配 i7-13700K，5800X，5900X
280水冷尺寸间于240和360水冷之间。280水冷采用的是140MM风扇，240和360水冷采用的是120MM风扇。使用280水冷的场合不多，有些特殊设计的机箱搭配280水冷比较合适，如酷冷的NR200P这款ITX机箱。280水冷推荐使用恩杰的海妖X63及海盗船的H115i。


# 机箱
## 规格参数
如：
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686829862141-93dba112-c4ab-406c-9448-279fd5230626.png#averageHue=%23212320&clientId=u872c5211-e7ca-4&from=paste&height=844&id=zPGWJ&originHeight=844&originWidth=663&originalType=binary&ratio=1&rotation=0&showTitle=false&size=354275&status=done&style=none&taskId=ubc7142b7-7e66-448b-93ca-d0f71a2646e&title=&width=663)

## 搭配兼容性

1. 主板兼容性
2. 显卡兼容性
3. 散热器
4. 硬盘位数量
5. 机箱是否闷罐

## 机箱风扇
需要区分一下，散热器上的风扇是用于将热空气排除散热塔，或将热量从冷排吹离，而机箱风扇是安装在机箱上，用于往机箱内吸入冷空气，并往机箱外排出热空气，二者不是一个概念
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686637543086-421c7d58-18e8-4449-9b87-2da40587d3ef.png#averageHue=%23bcc9d2&clientId=ud5916679-300b-4&from=paste&height=779&id=u4109f411&originHeight=779&originWidth=1802&originalType=binary&ratio=1&rotation=0&showTitle=false&size=631272&status=done&style=none&taskId=u46d041c4-195d-4a59-b83c-e766a8d0154&title=&width=1802)



# 显示器
## 分辨率

### 刷新率
越高的刷新率代表1秒可以显示的画面越多，画面就会越流畅
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686860166875-9df4fec3-961f-4c7f-b603-2e146dd02d80.png#averageHue=%233b3a39&clientId=u82f54f34-083c-4&from=paste&height=890&id=uf197c676&originHeight=890&originWidth=1547&originalType=binary&ratio=1&rotation=0&showTitle=false&size=570689&status=done&style=none&taskId=u5eccfa8f-501a-4b7b-a140-4eccef96d0b&title=&width=1547)
> 刷新率其实是可以作假的，有些商家宣传144Hz，但实际上只是支持144Hz的信号输入，最终呈现的还是60Hz的画面

如何检测144Hz是否真的支持144Hz?
testufo网站[https://testufo.com/](https://testufo.com/)
如果刷新率造假，比如相信了4K60Hz和2K144Hz双模自由切换，但它实际只是一个普通的4K60Hz显示器，然后真的打游戏的适合把显示器切换到了2K144Hz模式，最终获得的画面也只是2K60Hz，由于2K和4K不是整数倍，缩放的时候还会产生模糊，所以是既丢了西瓜也丢了芝麻

### 显示器搭配显卡


# 装机
### 安装cpu
### 安装内存
双内存槽：
如果是1根内存，插第1槽
如果是2根内存，插满就好

四内存槽：
从左往右，第2 4为优先插槽，第1 3为次要插槽
只有1根内存，插到<mark style="background: #FF5582A6;">第2槽</mark>内
有2根内存，优先<mark style="background: #D2B3FFA6;">2，4</mark>插槽
<mark style="background: #BBFABBA6;">不推荐3根</mark>内存，有概率出现不稳定和无法开机的情况
4根内存，<mark style="background: #ADCCFFA6;">插满</mark>就好

### 安装固态硬盘
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686638049175-e5a6cf30-6195-46d9-b783-0ac24e7bbaf3.png#averageHue=%23090908&clientId=ud5916679-300b-4&from=paste&height=865&id=ua56371d9&originHeight=865&originWidth=1664&originalType=binary&ratio=1&rotation=0&showTitle=false&size=219974&status=done&style=none&taskId=u60fa3204-996e-4a8b-8b07-42b8d71dc65&title=&width=1664)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686638106474-dee78fc2-63eb-4f2b-a9f6-de7012e09481.png#averageHue=%232e2928&clientId=ud5916679-300b-4&from=paste&height=680&id=uaf7d2a8c&originHeight=680&originWidth=1203&originalType=binary&ratio=1&rotation=0&showTitle=false&size=820496&status=done&style=none&taskId=uab3d2136-1be9-4fe3-91a5-e121fedafd6&title=&width=1203)
第一个M.2接口是和<mark style="background: #FF5582A6;">CPU直连</mark>的PCIe4.0 x4通道，有着所有M.2接口中最低的延迟和独立的带宽，将<mark style="background: #FF5582A6;">系统盘</mark>安装在这里
剩下的M.2接口来自南桥芯片组，共享南桥到CPU的总带宽的，延迟会比直连高
另外，挂载在南桥上的M.2接口能承载的速率和协议也是不一样的
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686851715955-22a256ac-2e95-41f6-8466-b6055404095e.png#averageHue=%239ea086&clientId=u271066e3-b1ee-4&from=paste&height=854&id=uf5e3fa72&originHeight=854&originWidth=1757&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1402010&status=done&style=none&taskId=u7cf29f46-0abc-404d-a0f4-b259ca78dda&title=&width=1757)
> 注意: 有一些主板的SATA接口和M.2接口是共享带宽的，例如

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686851907973-2d5cfc23-7caf-4cce-a743-ce22e651ebaf.png#averageHue=%23a89f94&clientId=u271066e3-b1ee-4&from=paste&height=925&id=u8bad6607&originHeight=925&originWidth=1652&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1323784&status=done&style=none&taskId=u36e8dc05-41e7-4444-b0b0-c1af43a019d&title=&width=1652)
  
### 安装风冷散热器
> 水冷散热器要等主板固定到机箱后再安装

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686852367832-a9a2caff-4562-4433-a024-078df5280ab2.png#averageHue=%23969591&clientId=u271066e3-b1ee-4&from=paste&height=680&id=u485d5006&originHeight=680&originWidth=1689&originalType=binary&ratio=1&rotation=0&showTitle=false&size=565970&status=done&style=none&taskId=u5259d079-f6f4-45c3-9d10-d90abf4e696&title=&width=1689)

### 固定主板到机箱
需要确认IO挡板是否需要独立进行安装
一些高端主板的IO挡板和主板是一体的，就不需要，而一些低端主板就需要独立安装，可以在主板盒子里找到IO挡板
螺丝柱，防止主板与机箱直接接触

### 安装水冷散热器
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686853038979-b6fdeca3-950a-4935-b82b-203646ec4b07.png#averageHue=%23b89174&clientId=u271066e3-b1ee-4&from=paste&height=879&id=u92052661&originHeight=879&originWidth=1451&originalType=binary&ratio=1&rotation=0&showTitle=false&size=975120&status=done&style=none&taskId=u78329291-38a5-44ed-80a4-e91b99ef2a5&title=&width=1451)
具体可以在机箱详情页查到
水冷散热器风扇接CPU_FAN
水泵接PUMP_FAN
RGB灯光，有两种接口，12V 4针对应主板的JRGB, 5v 3针对应主板的JRAINBOW/JARGB
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686853536567-079f0bae-bc29-402d-9273-1ea92511196c.png#averageHue=%23d8d8d8&clientId=u271066e3-b1ee-4&from=paste&height=494&id=u075ad458&originHeight=494&originWidth=1391&originalType=binary&ratio=1&rotation=0&showTitle=false&size=158257&status=done&style=none&taskId=u3e4d8ca5-8128-4bab-a5e7-101921d0ebf&title=&width=1391)

### 安装SATA接口硬盘
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686854063093-570a46c8-14a2-44b2-8e0a-5f2c773a2838.png#averageHue=%23676666&clientId=u271066e3-b1ee-4&from=paste&height=550&id=uf2669bdf&originHeight=550&originWidth=1378&originalType=binary&ratio=1&rotation=0&showTitle=false&size=243805&status=done&style=none&taskId=ubc6cc112-66f9-425a-876a-286f8b2fc69&title=&width=1378)
注意M.2和SATA接口冲突的问题

### 安装机箱风扇
需要区分一下，散热器上的风扇是用于将热空气排除散热塔，或将热量从冷排吹离，而机箱风扇是安装在机箱上，用于往机箱内吸入冷空气，并往机箱外排出热空气，二者不是一个概念
绝大多数低端机箱不配机箱风扇，需要自己额外购买，很多中高端机箱出厂会自带1把或3把风扇，当然也可以自己花钱买更多的风扇，但是要注意，水冷冷排会占用原本的风扇位
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686854558179-2c34b5e9-7b76-4b46-8ce1-86a9fe8f96ad.png#averageHue=%239c9a98&clientId=u271066e3-b1ee-4&from=paste&height=695&id=u25a1624f&originHeight=695&originWidth=1776&originalType=binary&ratio=1&rotation=0&showTitle=false&size=531557&status=done&style=none&taskId=u5f6e122a-44f4-44bf-a7c7-e222b7f4060&title=&width=1776)
i3+XX50，不需要机箱风扇，本身发热就不大
i5 + XX60，安装一个在尾部即可（7号位），如果有条件，再加一个在前面（2号位）
i7 + XX70，前面两个进风（1，2），顶部一个出风（6），尾部一个出风（7）
i9 + XX80，装满

### 安装电源
注意：
不同品牌，甚至同品牌不同型号的电源的模组线的线序可能不一样，千万不要混用模组线
可能导致硬件烧毁，升级电源时不能只换电源不换线

### 接驳线缆
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686855638628-78383cff-0c38-4631-9c62-d4ec8372e43c.png#averageHue=%23959595&clientId=u271066e3-b1ee-4&from=paste&height=611&id=u2e0385e4&originHeight=611&originWidth=1683&originalType=binary&ratio=1&rotation=0&showTitle=false&size=448782&status=done&style=none&taskId=u9760b630-2353-411a-b51b-60653fff160&title=&width=1683)
先接驳供电线缆
再接驳数据线缆，也就是机箱上的前置面板线，这个线是在机箱上的，要把对应的插槽插到主板对应的接口上

### 安装显卡

### 显示器连接
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686856737052-4a27c3da-36dc-4ee3-a811-343e69d5801a.png#averageHue=%23a3a5a3&clientId=u271066e3-b1ee-4&from=paste&height=611&id=u342e220a&originHeight=611&originWidth=1227&originalType=binary&ratio=1&rotation=0&showTitle=false&size=449750&status=done&style=none&taskId=u57cb66c4-ca55-4ea7-a8a2-4c61fa81e07&title=&width=1227)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686856907564-e95ebabb-fc0a-42a3-96d2-a064da32fafb.png#averageHue=%23c3cbca&clientId=u271066e3-b1ee-4&from=paste&height=879&id=uf648c51a&originHeight=879&originWidth=1654&originalType=binary&ratio=1&rotation=0&showTitle=false&size=733612&status=done&style=none&taskId=u391a079d-f8d6-4b51-bbee-398cb57a0e1&title=&width=1654)
如果接口不匹配，可以买转接头

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686857085061-b49324cb-06e0-40da-8a84-5b536de11bb4.png#averageHue=%23c6c8c8&clientId=u271066e3-b1ee-4&from=paste&height=854&id=ua70967a4&originHeight=854&originWidth=1459&originalType=binary&ratio=1&rotation=0&showTitle=false&size=668279&status=done&style=none&taskId=u22327f8a-71d1-41cb-8ac9-4c9f373f55c&title=&width=1459)
HDMI和DP都是用来传输视频和音频数据的，只要接口的带宽能承载起显示器的最佳分辨率和最佳刷新率以及色深，那对于绝大多少人来讲，这两个接口就没有好坏之分，用哪个都可以
但是需要注意的是：不同版本的HDMI和DP，所能支持的最大分辨率和最大刷新率和色深是不同的，如果使用HDMI发现分辨率刷新率达不到显示器的最佳分辨率最佳刷新率，那就换DP看看，如果是DP达不到，那就换HDMI看看
连接鼠标、键盘.......

### 开机
先接通显示器的电源，开启显示器
再接通主机的电源，开机
如果安装全部正常，就会有三种情况：
界面一：进入BIOS
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686857953801-c3397c83-4cc4-400a-8677-096c64280d9d.png#averageHue=%2317181a&clientId=u271066e3-b1ee-4&from=paste&height=701&id=u170801ac&originHeight=701&originWidth=1244&originalType=binary&ratio=1&rotation=0&showTitle=false&size=374361&status=done&style=none&taskId=ucae038ed-a679-4b5d-97cf-0cc1821407d&title=&width=1244)

界面二：配置画面，按F1执行默认初始化，或者按F2直接进入BIOS
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686858046038-54e0da2c-6285-45f5-bc1d-53234461f4ef.png#averageHue=%23010101&clientId=u271066e3-b1ee-4&from=paste&height=709&id=ucac34b49&originHeight=709&originWidth=1258&originalType=binary&ratio=1&rotation=0&showTitle=false&size=85386&status=done&style=none&taskId=u74a7f8c2-ef33-4adf-8616-03c644b8463&title=&width=1258)

界面三：boot启动错误
> 直接进入了硬盘内，但是硬盘没有安装系统，所以提升boot启动错误

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686858134886-4d92dc7b-2091-4c4f-972b-01e08c27583d.png#averageHue=%23000000&clientId=u271066e3-b1ee-4&from=paste&height=706&id=u055c10a8&originHeight=706&originWidth=1251&originalType=binary&ratio=1&rotation=0&showTitle=false&size=20255&status=done&style=none&taskId=ud7bf1393-2249-4bdd-8980-413179ca5ae&title=&width=1251)
以上三种情况都代表安装没有错误，接下来安装系统就可以开始使用了

如果没有上述的画面
情况一：一堆英文报错
> 尝试翻译，一步步解决

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686858298152-c78ff6b6-aa1f-4bc6-9cb8-245e6245ccc6.png#averageHue=%23060606&clientId=u271066e3-b1ee-4&from=paste&height=701&id=u5f2ddc56&originHeight=701&originWidth=1241&originalType=binary&ratio=1&rotation=0&showTitle=false&size=169648&status=done&style=none&taskId=u8c1d6fd1-137f-4565-ae19-f40588041cd&title=&width=1241)

情况二：开机黑屏
> 打开显示器菜单，检查显示器的视频信号源，要和显示器背面接口的数字一致

![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686858451231-64b4ebba-c1d1-4961-828c-1cbe4efec614.png#averageHue=%23141518&clientId=u271066e3-b1ee-4&from=paste&height=603&id=uedc1d718&originHeight=603&originWidth=1053&originalType=binary&ratio=1&rotation=0&showTitle=false&size=77297&status=done&style=none&taskId=u57997a05-70c9-4a36-8275-c2edfccb72d&title=&width=1053)

如果还是不行，检查主板上的debug灯
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1686858639676-7f1f0a7a-a888-4fa0-94b4-14c004c0d1ad.png#averageHue=%23ccc5b7&clientId=u271066e3-b1ee-4&from=paste&height=826&id=uc5fd8844&originHeight=826&originWidth=1277&originalType=binary&ratio=1&rotation=0&showTitle=false&size=490917&status=done&style=none&taskId=u153351b2-36b7-4794-90eb-54c3c99b99b&title=&width=1277)


# 推荐文章和up主

- CPU： [2023年8月CPU选购指南及推荐 - 知乎](https://zhuanlan.zhihu.com/p/268642936)
- 散热器： [2023年7月台式电脑CPU散热器选购指南 - 知乎](https://zhuanlan.zhihu.com/p/258379061)
- 主板： [2023年8月主板推荐及选购攻略 - 知乎](https://zhuanlan.zhihu.com/p/344503535)
- 显卡： [2023年8月显卡推荐及选购攻略 - 知乎](https://zhuanlan.zhihu.com/p/269635708)
- 内存： [2023年8月电脑内存选购指南及推荐，如何选择性价比内存条（内存天梯） - 知乎](https://zhuanlan.zhihu.com/p/183249476)
- 固态硬盘：[2023年8月固态硬盘推荐 - 知乎](https://zhuanlan.zhihu.com/p/165266063)
- 机械硬盘：[2023年8月机械硬盘选购指南及推荐 - 知乎](https://zhuanlan.zhihu.com/p/356118338)
- 电源： [2023年8月电脑电源选择指南与推荐 - 知乎](https://zhuanlan.zhihu.com/p/179066013)
- 机箱： [2023年8月电脑机箱推荐 - 知乎](https://zhuanlan.zhihu.com/p/337206779)
- 显示器： [2023年8月显示器选购指南 - 知乎](https://zhuanlan.zhihu.com/p/194297824)
- 散热风扇：[2023年8月机箱散热风扇推荐及选购指南 - 知乎](https://zhuanlan.zhihu.com/p/259600857)


# 配置单
> 2023-6-17，配件价格（京东自营或官方旗舰店）

## CPU、散热
官方价格：

|  | 京东自营 | 官方旗舰店 |
| --- | --- | --- |
| **i5-12400F/13400F** | 1049/1299 | 1269 / 1519 |
| **i5-12490F/13490F** | 1149 / 无 | 1219 / 1549 |
| **i5-12400/13400** | 无 | 1599 / 1729 |
| **i5-12600KF/13600KF** | 1799 / 2099 | 2019 / 2319 |
| ** i5-12600K/13600K** | 2299 / 2299 | 2149 / 2469 |
| **i7-12700F/13700F** | 2169 / 2449 | 2369 / 2749 |
| **i7-12700KF/13700KF** | 2289 / 2799 | 2249 / 3199 |
| ** i7-12700/13700** | 2609 /  3099 | 2599 / 2999 |
| ** i7-13790F** | 无 | 2999 |
| ** i7-12700K/13700K** | 2969 / 2849 | 3199 / 3299 |
| **i9-12900F/13900F** | 无/3999 | 3599 / 4399 |
| **i9-12900/i9-13900** | 无/4199 | 3699 / 4599 |
| **i9-12900KF/13900KF** | 无/4599 | 4099 / 5099 |
| **i9-12900K/13900K** | 无/4899 | 4299 / 5999 |
| **i9-12900KS/13900KS** | 无/6699 | 3999 / 无 |

<mark style="background: #D2B3FFA6;">i7在 2000 以上，所以 CPU 考虑 i5</mark>
预算 1500 以内，考虑下面四个：
<mark style="background: #BBFABBA6;">i5-12400F/13400F、i5-12490F/13490F</mark>
<mark style="background: #BBFABBA6;"></mark>综合性价比，选 <mark style="background: #BBFABBA6;">i5-13400F</mark>
![image.png](https://cdn.nlark.com/yuque/0/2023/png/663445/1687089045757-5684b4e7-e6ae-4e92-9711-2ec560250879.png#averageHue=%231f1e20&clientId=ud37dc73b-79af-4&from=paste&height=810&id=hhflV&originHeight=810&originWidth=1271&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1128341&status=done&style=none&taskId=u06b17df8-5cd7-4011-bf51-3da69cbf8ce&title=&width=1271)

散热：<mark style="background: #FF5582A6;">雅俊 B3 ARGB</mark>

## 显卡
3060Ti 、3070 、3070Ti 、3080 、3080Ti 、4060 、4060Ti
预算 3000 以内，3060Ti起步

![IMG_0959.JPG](https://cdn.nlark.com/yuque/0/2023/jpeg/663445/1688204455787-d75698ca-ef2d-4d6a-9084-18f1b069fb12.jpeg#averageHue=%23ccdfe5&from=url&id=woBGZ&originHeight=1093&originWidth=597&originalType=binary&ratio=1&rotation=0&showTitle=false&size=280452&status=done&style=none&title=)

![IMG_0961.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204461411-dc657cf1-7511-4b9b-972b-5ce64375ef7d.png#averageHue=%23d4e9ef&from=url&id=n7C0C&originHeight=802&originWidth=590&originalType=binary&ratio=1&rotation=0&showTitle=false&size=206663&status=done&style=none&title=)

![IMG_0965.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204458119-01bd3314-be8b-489f-937f-4971bd771926.png#averageHue=%23d3e9ef&from=url&id=wm275&originHeight=1126&originWidth=587&originalType=binary&ratio=1&rotation=0&showTitle=false&size=295682&status=done&style=none&title=)
![IMG_0964.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204459194-38fd1c3d-65b1-4d35-83f6-a0624b188813.png#averageHue=%23d0e7ef&from=url&id=VlaIh&originHeight=970&originWidth=589&originalType=binary&ratio=1&rotation=0&showTitle=false&size=244939&status=done&style=none&title=)

![IMG_0960.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204460321-3bf16785-6eda-4078-a582-9c8e7ac734da.png#averageHue=%23cde4ec&from=url&id=Qv2Zq&originHeight=969&originWidth=710&originalType=binary&ratio=1&rotation=0&showTitle=false&size=287189&status=done&style=none&title=)


![IMG_0963.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204454649-63697dc2-5aa5-4982-911f-d49a0fef0423.png#averageHue=%23c9e2ec&from=url&id=BZykD&originHeight=479&originWidth=839&originalType=binary&ratio=1&rotation=0&showTitle=false&size=144405&status=done&style=none&title=)

![IMG_0962.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204462495-025a97a0-7e4f-4ef8-a6b3-f7ec949875fb.png#averageHue=%23cfe7ef&from=url&id=f4aoT&originHeight=1072&originWidth=714&originalType=binary&ratio=1&rotation=0&showTitle=false&size=313704&status=done&style=none&title=)

![IMG_0966.PNG](https://cdn.nlark.com/yuque/0/2023/png/663445/1688204456859-d8684fb5-b718-4865-9c51-a34aaa77c6dd.png#averageHue=%23cee5ee&from=url&id=r4EO7&originHeight=773&originWidth=719&originalType=binary&ratio=1&rotation=0&showTitle=false&size=223248&status=done&style=none&title=)

## 主板：
重炮手和天选价格一样，天选颜值绿色二次元
+WIFI	50-70 元
D4-D5	50-100 元
B660-B760  50-100 元
Z690 和 Z790 都比较贵，cpu 不超频就不考虑
综合可以考虑，**B660M WIFI D5、B760M WIFI D5**

| **B760M D4** | 1079 |
| --- | --- |
| **B760M D5** | 1149 |
| **B760M WIFI D4** | 1149 |
| **B760M WIFI D5** | 1249 |
| **B660M D4** | 1049 |
| **B660M WIFI D4** | 1099 |
| **B660M WIFI D5** | 1149 |
| **ROG STRIX B760-A GAMING WIFI 吹雪主板 支持DDR5** | 1699 |
| **ROG STRIX B760-G GAMING WIFI D4 小吹雪主板** | 1299 |
| **ROG STRIX B760-G GAMING WIFI 小吹雪主板 支持DDR5** | 1399 |
| **ROG STRIX B760-A GAMING WIFI D4 吹雪主板** | 1599 |
| Z790 | 比较贵，最便宜也是1699 |
| **PRIME Z690-A D5** | 1799 |



## 内存
套条 16G* 2、DDR5
都在 600 以上，选一个便宜的就行

| 金士顿 (Kingston) FURY 32GB(16G×2)套装 DDR5 6000 台式机内存条 Beast野兽系列 骇客神条 | 649 |
| --- | --- |
| **芝奇（G.SKILL）32GB(16Gx2)套装 DDR5 6400频率 台式机内存条-幻锋戟RGB灯条(黯雾黑)/C32** | 879 |
| **芝奇（G.SKILL）32GB(16Gx2)套装 DDR5 6000频率 台式机内存条-幻锋戟RGB灯条(黯雾黑)/C36** | 799 |
| **芝奇（G.SKILL）32GB(16Gx2)套装 DDR5 6400频率 台式机内存条-焰刃(黯夜黑)/C32** | 799 |
| **金百达（KINGBANK）32GB(16GBX2)套装 DDR5 6400 台式机内存条海力士A-die颗粒银爵系列 C32** | 649 |
| 金百达（KINGBANK）32GB(16GBX2)套装 DDR5 6000 台式机内存条 三星B-die颗粒 RGB灯条刃系列 C36 | 698 |

## 硬盘
1T 及以上 ，M.2 NVMe 协议 PCIe4.0

## 电源

## 机箱


## 配置单
![a6933807f5386692bf4793b1d28785e.jpg](https://cdn.nlark.com/yuque/0/2023/jpeg/663445/1687275306522-23f743f1-204d-4451-b687-be720a3a0c16.jpeg#averageHue=%23f2f6f3&clientId=u7fb8b557-c6d2-4&from=paste&height=800&id=u172af5a9&originHeight=800&originWidth=800&originalType=binary&ratio=1&rotation=0&showTitle=false&size=282495&status=done&style=none&taskId=u4d4da45c-20ef-451e-bd52-e6d93f8462a&title=&width=800)
