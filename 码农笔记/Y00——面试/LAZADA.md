
# 业务
物流：LEL 官方物流  LEX 自营的末端物流派送

表达：中台化应用，交易前拆单、下单服务决策、服务承诺列表及运费计算
rc:管理供应链中涉及到的资源


rc: capacity容量管理，资源管理、费卡管理、规则管理



P2P（几个小时） 
Express 1-2天
STD 3-10 天(也是兜底线路)
Economy 10-20天  

pre-order: 搜索、PDP、购物车、交易、支付
表达：delivery option/Promise deleiver time/shipping fee/add-on service(COD，G)
Post-order: goup、seller center、WHC、

表达整块给到交易、交易整块给到履约


上下游依赖：
普通渲染场景：
1 用户浏览 pdp 或购物车，或者下单
2 调用我们表达，请求物理选项
	3 调 ==ASC==，查询卖家类型、 卖家holiday
	4 如果是 P2P 场景，调==Address==服务，根据经纬度，查询距离
	5 调资源中心（rc),查询线路、容量、计算、过滤、计算运费
6 返回给上游物流选项
7 用户看到物流选项信息


下单场景：
1 用户下单，选择物流选项
2 调用表达，重新计算物流选项
	3 调 ==ASC==，查询卖家类型、 卖家holiday
	4 如果是 P2P 场景，调==Address==服务，根据经纬度，查询距离
	5 调资源中心（rc),查询线路、容量、计算、过滤、计算运费
	6 占用容量（写数据库）
7 返回结果
...


业务、代码 逻辑：
split拆包
按卖家+仓库，digital、渠道 等维度，把一个交易订单，拆成n个逻辑包裹，


queryForSource交易根据拆包结果，调==表达==请求物流选项：
物理选项：
1. 缓存 ==Tair== 中，查询 ==override rule==，如果没有，查 ==DB==，（tair 缓存一小时）
2. 缓存 ==Tair== 中，查询==卖家类型、卖家 holiday==（tair 缓存一小时），如果 tair 没有，调 ==ASC== 查询卖家类型，卖家holiday
3. 缓存 ==Tair== 中，查卖家==履约==阶段、==运输==阶段的数据，（Tair 缓存 4 小时），如果没有，查 ==DB==
4. 计算履约阶段数据（使用 holiday,override rule)，如果没有，补充 default 值
5. 计算运输阶段数据....
6. 过滤线路类型，dimensions， pickuptype,过滤买家地址，卖家地址
7. 如果是 P2P场景，调 ==Address== 服务计算经纬度==距离==，==强依赖==，==阻断下单==
8. 合并履约阶段和运输阶段的数据
运费：
9. ==Tair== 查询==价卡==订阅关系，（缓存 1 小时），如果没有，查 ==DB==，如果还是没有，==阻断下单==
10. 根据 max(体积重)算运费，运费通过个数或者重量分摊到每个商品
11. 合并运费和路线
12. 返回给上游物流选项

下单confirm
用户选择物流选项，下单，交易 带上用户选择的物流选项请求 confirm 接口
重新计算时效和运费（如上）
返回物流选项，交易校验选择的运费和物流选项是否一致，如果不匹配，阻断下单



拆包
交易的拆包、运费拆包

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309242113317.png)

商品添加到购物车
购物车中多选商品
拆包
redmart、digital、preSale、sof、sellerId、channel


# 技术栈
[阿里云文档-阿里云文档中心-阿里云帮助中心-阿里云，领先的云计算服务提供商](https://help.aliyun.com/?spm=a2c4g.120868.0.0.6bca2ee06Amy1p)

## 云原生
[[Lazada云原生]]


## HSF
[HSF 基础记录\_落小渔的博客-CSDN博客](https://blog.csdn.net/weixin_35821291/article/details/122978538)

[使用HSF开发应用\_企业级分布式应用服务 EDAS-阿里云帮助中心](https://help.aliyun.com/zh/edas/developer-reference/use-hsf-to-develop-applications/?spm=a2c4g.11186623.0.0.1115514bGTkkOe)

HSF旨在为阿里巴巴的应用提供一个分布式的服务框架，HSF从分布式应用层面以及统一的发布/调用方式层面为大家提供支持，从而可以很容易的开发分布式的应用以及提供或使用公用功能模块，而不用考虑分布式领域中的各种细节技术，例如远程通讯、性能损耗、调用的透明化、同步/异步调用方式的实现等等问题。

## Pandora

Pandora，中文名潘多拉，是淘宝网中间件团队打造的，基于HSF隔离技术构建的全新一代隔离容器。从解决二方包依赖冲突出发，致力于统一管理通用的二方包，包括方便的二方包升级管理，监控和管理，建立统一的二方包扩展编程方式等。

## Pandora Boot

Pandora Boot 是在 Pandora 的基础之上，发展出的更轻量使用 Pandora 的方式；它基于 Pandora 和 Fat Jar 技术，可以直接在 IDE 里启动 Pandora 环境，开发调试等效率都大大提高；同时与 Spring Boot AutoConfigure 深度集成，让用户在使用中间件的同时充分享受 Spring Boot 框架带来的便利。

Pandora Boot可以认为是Spring Boot的增强

pandora boot starters
* pandora-hsf-spring-boot-starter
* pandora-diamond-spring-boot-starter
* pandora-metaq-spring-boot-starter
* pandora-notify-spring-boot-starter
* pandora-tddl-spring-boot-starter
* pandora-tair-spring-boot-starter


## Notify

分布式消息系统Notify

Notify是一个消息中间件。应用程序或组件之间可以使用消息中间件进行可靠的异步通讯来降低系统之间的耦合度，从而提高整个系统的可扩展性和可用性。Notify具有以下特点，可以说是互联网时代的消息中间件：高性能，无限扩展、可靠、与发送端业2务相结合(分布式事务)、支持发送者集群和订阅者集群、发送和接收消息的流量控制。

## MetaQ

MetaQ是一款分布式、队列模型的消息中间件。分为Topic与Queue两种模式，Push和Pull两种方式消费，支持严格的消息顺序，亿级别的堆积能力，支持消息回溯和多个维度的消息查询。

## Configserver

轻量级注册中心（ConfigServer）

ConfigServer中文名为==非持久配置中心==，主要用于非持久数据的发布和订阅，数据的生命周期和TCP连接生命周期绑定，产品架构基于发布订阅模型，去中心无master设计，保证了系统的可扩展性、高可用。在集团内部主要场景为分布式消息系统Notify、分布式RPC框架HSF提供地址发现服务。

## Diamond

Diamond是一个持久==配置管理==中间件.可以实现==分布式==场景下，==中心化==的==持久配置管理==，同时也支持基于发布订阅模型配置动态变更推送.
轻量级配置中心（Diamond）是淘宝内部广泛使用的配置中心，提供持久化管理和动态配置推送服务。应用方发布的配置会通过持久化存储保存，==与发布者的生命周期无关==


## Vipserver

通过集中式的配置向客户提供路由信息，以非网关的形式实现负载均衡功能；支持多种映射策略（轮询、轮询+同机房、轮询+同网段）；通过健康探测机制，自动剔除不健康的机器，实现集群之间调用的透明化；对调用量、调用方等数据也有一定程度的反馈

## TDDL
TDDL 分布式数据库中间件

TDDL旨为用户提供在线数据库服务。TDDL部分兼容MySQL关系型数据库，并提供数据库在线扩容、性能监测及分析功能。TDDL支持弹性扩容.

## 数据库

逻辑库
global_expression_lazada_sg
global_expression_lazada_id
global_expression_lazada_th
global_expression_lazada_ph
global_expression_lazada_vn
global_expression_lazada_my

物理库就是后面加上 0000-0063，比如global_expression_lazada_0000 这种

每个站点 64 个物理库
global_expression_lazada_ph_0008中
`rc_capacity_reservation_[0512-0575]` 64张表
`rc_capacity_reservation_details_[0512-0575]` 64张表
`rc_delivery_lane_[0512-0575]` 64张表
`rc_delivery_sla_[0512-0575]` 64张表

## SchedulerX

SchedulerX是一整套分布式任务调度的解决方案，是dts的下一代产品，目前已经在集团内大规模应用，schedulerx提供单机，并发，脚本任务等多种任务类型调度，基本覆盖所有的调度场景。

## 精卫

精卫填海（简称精卫）是一个数据同步产品，数据源主要包含mysql的全量+增量，支持方便的订阅binlog，内置多种消息的处理场景，远期目标是构建一个完善的数据处理平台

## TXC 分布式事务

TXC是一个分布式事务中间件，主要用来解决业务服务化后和分库分表后操作不同数据库的分布式事务问题，严格保证多数据源操作的数据一致性。

## Tair 分布式缓存

tair是一个高性能、分布式、可扩展、高可靠的Key-Value结构存储系统，专注于高速缓存场景。该项目诞生于淘宝，并在阿里巴巴集团内部大规模使用，是集团内调用量最大的系统之一。在多年的阿里巴巴“双十一”全球狂欢节上，为了承受数亿次的调用服务， Tair部署了将上百个集群，数千台的物理机，单节点QPS峰值近百万次，集群缓存命中率达90%以上，承担了天猫、淘宝、聚划算主站的大多数访问压力



## Arthas 在线诊断

问题排查工具

Arthas 是一款线上监控诊断产品，通过全局视角实时查看应用 load、内存、gc、线程的状态信息，并能在不修改应用代码的情况下，对业务问题进行诊断，包括查看方法调用的出入参、异常，监测方法执行耗时，类加载信息等，大大提升线上问题排查效率

## HOTCODE2 JAVA热部署

HotCode2，一个纯Java实现的热部署工具，对java文件，资源文件以及框架的配置文件的修改可立即生效，无需重新打包部署，同时支持远程部署，有效提高开发效率

## ODPS

ODPS 同步数据

## SmartEngine 流程引擎

一款业务治理和服务编排引擎

业务治理引擎专注于解决互联网场景下和传统工作流行业的流程相关问题，服务编排引擎专注于用统一的标准来解决复杂链路服务上的服务编排问题

## TMF

## sls、eagleeye

sls是看线上日志的日志系统，就是 kafuka

## docker 镜像
## hubernetes 部署、动态编排

## xflush、Sunfire集团监控


# 表达技术架构
表达应用：
启动器，global-expression-s
中台地址 global-supplychain-expression
站点地址 lazada-expression-ns-s 
rc lazada-resource-center


metaq:
LNP同步过来的 shipping provider数据
同步 DGCOD 数据
同步 LogisticsCategory 数据
同步 LNP 物流数据（包括线路、容量、地址、seller group)


## 预案降级：
* 购物车降级，appName是 CART，采用==默认时效==
* 增加 RC 数据缓存的相关存活时间 比如，240->2880
* 停止所有的从 ODPS 同步数据的自动任务 
* 降级代码中部分方法打印的日志，防止磁盘被打爆 
* 降级通过经纬度查距离，执行后，影响 VN，MY,ID部分的 P2场景线路透出 
* degradeSellerHolidayQuery 
* 对查询卖家类型接口进行降级，采用默认的卖家类型， 
* o2o 商品选中 pickup in store 物流选项获取的门店列表信息都不回透出距离信息，下单业务不收影响，执行后，不会再去调地址接口，门店列表信息正常，距离信息为空


lazada-rc-s:管理供应链中涉及到的资源

lazada-expression-ns-s:中台化应用，交易前拆单，下单服务决策，服务承诺列表及运费计算



# 我做了哪些事
## 赔付迁移
Lazada在不同国家地区上线【==慢必赔==】业务，即用户收到快递包裹==超时==场景，触发==自动赔付==。
根据国家地区不同，向用户赔付==券==或==积分==，并通过站内消息通知用户

对接上游赔付场景（承诺达），赔付客户券或平台积分，并发送站内信

之前的架构：
1. ==履约==创建赔付任务，通过==定时任务==触发
2. globa-uop通过hsf调用==赔付平台==(compensationplatform)进行赔付
3. 赔付平台会创建工单，发送消息，消费消息的时候调==资金中台==(capial-platform-i18n)进行赔付
4. 资金中台调==领券==或者==积分==接口（根据赔付方式不同，调不同的接口）
5. 赔付完成之后，调xspace-email发送站内信

业务变更时，需要向 CCO（资金中台）侧提需求，由资金中台侧进行配置或开发
然后 CCO 他们不干了，他们说这个业务场景是可以在业务侧完成的闭环操作

所以进行了迁移
在业务侧完成闭环操作，降低系统间依赖
减少开发周期、降低运营维护成本

迁移完成后,不再依赖compensationplatform. capital-platform-il8n、 xspace-email

赔付方式：
voucher: 调 Promotion
rebate:调Alipay


业务方面多跟接口人沟通，需求评估、方案设计的时候尽量考虑全面

调Aalipay的时候引用了二方包AlipayToolKit，跨单元跨应用读取Demond配置报NPE
方案1
因为调Alipay底层其实是发送了—个http请求，可以把相关的方法放到global-uop，不在依赖二方包
缺点：会引入很多和本应用不相关的代码，提升了系统复杂性，后期维护困难

方案2
申请对应二方包代码权限，把原来的二方包中读配置改成global-uop应用读配置，把配置信息传递到二方包


## DG_COD
1、90%的印尼订单都采用COD支付-线上支付形式很少 1100w会员不能使用COD支付购买DG
2、采用COD支付的买家并不能购买数字产品
3、我们愿为数字产品提供COD的支付方式以便更多的买家购买线上数字产品

印尼每日1.3M买家，9成是使用COD进行支付。并且有在线支付能力的买家只有30%。
由于DG商品都是要求用户使用在线支付，所以平台大部分用户是无法购买DG商品的

一期
表达时效min、max都固定为N+1 没有考虑到非工作日和COT时间

二期，时效考虑到 工作日 和 COT，提高时效的==准确率==，提升==用户体验==
工作日和COT皆可配置，提升业务灵活性


效果：


技术设计：
交易打上标：supportDgCod?

表达：根据买家地址，调 RC 查询是否有 hub
是否有对应的价卡

## rc_performance分库分表、数据清理
原来查时效的时候，无论是卖家履约段还是配送段的时效数据都是在同一张表中

背景：
算法优化过后的ffm sla 会==膨胀数据量级==，1D会到==800w==左右。如果按保留3个版本，会有==2400w==数据，这样对==单表==压力较大，需要拆分一下。

考虑直接建1024 张表的逻辑表 rc_pefommenoe：

迁移schedule×对应的任务产生的==数据流向==，切到rc_performance。做开关切换读写

ro_ability_lane表中，Last Mile和Seller SLA的数据由定时任务从中间表rc_ability_lane_intermediate中同步过来。目前rc_ability_lane数据量已有16042191，单表压力大，需要把Seller SLA的数据存储到一个新表中


表结构设计：

分库分表：

分表键：sellerId, 表达式#seller_id#%1024
0000库：rc_performance_0000、...rc_performance_0063
...
0015库：rc_performance_0960、...rc_performance_1023

TDDL 规则配置


表达新逻辑，查新表，加缓存tair


## 深分页慢 sql 问题
`select from ... where ... limit pageStart, 5000;`

这是一个经典的“深分页〞问题，这种分页查询方式会从数据库==第一条记录开始扫描==所以越往后，查询速度越慢，而且查询的数据越多，也会拖慢总查询速度，如图，每次查5000行，随着查询偏移的增大，耗时越来越大，特别是上百万后，更是急剧增加

优化：
先使用子查询查出对应偏移量所在行的id，再where >= id limit 5000;


## 次日达 next day
LNP 通过 MQ 同步线路数据到 rc, 线路打上标



## 兜底网络裁剪全域方案设计
表达有一个兜底的物流选项，目的地禁售

然后发现用户下单后，没有 3PL 能上面揽收

RC ： 配置 non_default area 不兜底区域，

ASC ：新用户注册的时候，订阅物流选项，页面选择仓库地址，调 RC 查询是否是不兜底区域，然后调 LNP 分配 3PL，如果分配失败，提示用户

已经存在的卖家，如果仓库地址不在 LNP converage, 则判断地址是不是不兜底区域




## RC 解决缓存空对象问题






# 其他需求案例
## 卖家调表达仓库地址接口 FGC 问题排查
==交易==强依赖==卖家==仓库地址的服务，卖家仓库地址迁移后，接口流量切流转发到RC，Promise和RC合并部署在表达应用中。

交易-->卖家-->表达。由于表达压测期间有机器FGC，STW会有RT尖刺，间接造成交易调用卖家服务超时。
交易调用卖家的成功率有99.99%

表达系统FGC的STW，卖家调用表达系统的RT少量请求超时。间接对交易调用卖家服务的成功率造成影响。

GC 情况描述：
日常流量 GC 的情况：
YGC ==每分钟==最高5次，正常处==3-4==次之间，总耗时大约在==200ms==/分钟 
FGC ==一天==一共发生了==3次==，耗时大约==300ms/次==

压测流量 GC 情况
YGC ==每分钟==最高==26==次，总耗时最高在==764ms==/分钟。压测期间一共产生了==7次FGC==，FGC的最长时间是500ms


问题总结：
表达应用==日常偶发FGC==(24小时＜1次），==压测期间频率升高==。
YGC在压测的流量下，==每分钟==的次数从日常的==4次==增加到峰值的==26==次。
压测期间FGC的耗时在300ms左右，不影响交易的下单

排查过程：
1. 先确认是否存在内存泄漏（内存泄漏指的是**JVM中某些不再需要使用的对象，仍然存活于JVM中而不能及时释放而导致内存空间的浪费**），从监控图中可以看到，==FGC==之后，==OLD==区的内存都可以回到~500M，内存==可正常回收==，==排除内存泄露的可能==。
2. 查看内存的对象实例分布情况
   在查找内存是程序中的什么对象占用时，需要分析内存的具体消耗状况，对于有图形界面可用的情况，VisualVM是常用的选择；对于不能采用图形界面方式的，可通过`jmap dump`生成文件后，再通过MAT进行分析是常用的选择
   经过分析：
   instances of **com.google.common.cache.LocalCache**$StrongAccessWriteEntry, loaded by com.taobao.pandora.boot.loader.LaunchedURLClassLoader @ 0x6a0821060 occupy **1,981,469,376** (==57.13==%) bytes.   （1.8G）

   instances of com.google.common.cache.LocalCache＄StrongValueReference, loaded by com.taobao.pandora.boot.loader.LauncheduRLClassLoader @ 0x6a0821060 occupy 436,718,392(==12.59%==) bytes..   （420MB）
   
   总占用了70%多，所以可以基本确认是由于==localcache==导致的FGC.直接通过支配树查看具体关联的==业务对象==.


localcache导致FGC主要是因为==YGC==无法回收的cache对象（达到在YGC的最大的年龄或者大对象直接沉到OLD 区），慢慢被沉到Old区，在OLD区累积，到达==FGC的阈值==之后（当前配置的是内存占用的80%）便会触发 FGC。

先查看JVM对于Young区对象的年龄的配置，JVM的参数中没有显式的配置对象在Y区存活的年龄，默认15次。

当前大部分的Localcache的过期时间设置为5分钟。日常每分钟3-次的YGC，部分的localcache可能会在Y区就被GC掉。不会下沉到OLD区，所以日常的OLD区的内存占用率上升缓慢，达到阈值需要较长的一段时间。

而在压测流量时，YGC最高时，一分钟最高26次，设置为5分钟的localcache会全部沉入到OLD区，使得OLD的内存占用率上升较快，短时间内触发FGC。

结论：
应用中发生FGC主要的根本原因是localcache的使用，压测期间由于流量的增加，YGC频率较高，大部分配置 localcache 5分钟过期时间，在YGC发生15次之后（约30秒），会沉入到old区，内存占用触发阈值之后，发生 FGC。


优化方案：
1. 将卖家的调用的流量切流到 lazada-rc-s 应用，确保 lazada-rc-s应用无FGC的问题。
2. 按照内存快照排查是否存在localcache使用不合理的情况
	1. 查各个本地缓存日常状态下的==缓存命中率==，命中率低的本地缓存需要调整缓存时间。
	2. 查存在==重复==的缓存的场景是否合理，Holiday / holidayDTO --没有重复缓存 - HolidayDTO包含了 siteid， version和status。Holiday参数更少，查询直接对外返回HolidayDTO转换后的Holiday 
3. 将localcache的使用的场景梳理清楚，根据YGC的规律，合理配置好过期时间
4. 更改更符合表达应用内存管理特点的G1 垃圾处理器，通过压测验证GC的是否有优化

代码优化及验证方法：
正确的使用本地缓存，调整缓存时间，尽量在YGC的时候将缓存回收。
单机场景下压测、使用单机压测的方案看YGC的频率及OLD区增长的速度。


## G1 解决本地缓存FullGC问题
结论：
使用==G1==会解决表达本地缓存==fullgc==问题，经过预发和正式环境压测对比，G1在压测过程中没出现fullgc，==CMS==在白加黑中大概==一个小时出现一次fullgc==（每次 400ms 左右），但是cpu会比之前高，峰值大概高10%左右。

原理：
表达==本地缓存==大多数设置==5分钟==，数量==50000==个，涉及==卖家相关数据==，==线路相关数据==（==地址级别==），平时==young gc== 大概==20-30秒一次==（每分钟 3-4 次），5分钟释放后不会进入老年代（因为进入老年代需要年龄超过15）。压测时候加剧young gc 速度，大概==3秒一次==（每分钟 20 几次），导致失效时候基本都是要直接==进入老年代==的，所以压测时候old 区会一直增加，直到fullgc。

G1为什么能解决问题？
G1可以==设置==一个==垃圾回收==的==预期停顿时间==，制定一个目标，规定在一个时间内，垃圾回收引起的停顿时间不能超过多久，之后就由G1来全权负责，保证达到该目标。对于表达，老年代基本都是过期对象，非大对象，之前 fullgc后基本回到很低的水平。证明只要有提前gc(mixed GC)还有控制STW 时间的机制，是能解决表达的问题的。

验证：持续压测 20 小时
G1无 fullgc

正式压测结论：
使用G1回收器的，比较符合预期，没有fullgc，young GC 耗时比其他机器较高，1000ms，young ge 次数比其他机器少一些，不过都是22次最高。

机房其他CMS机器，有发生3次fullgc，大概一小时一次。所以其实G1应该是比较符合表达当前场景的，可以考虑大促前发布。


升级 G1

背景：双十一我们压测过程我们遇到一个问题。表达发生fullgc（每次500ms 左右），造成提供给卖家查询仓库地址的接口超时，当时有超时配置不合理问题，造成阻断交易

本质上查询仓库地址失败，阻断交易是合理的，之前的问题主要是fullgc问题。所以表达这边做了两个action改造
1。 升级G1解决fullgc 问题（现在已经没有fullgc了）
2。把查询仓库地址接口迁移到rc避免表达fullge 影响这个接口可用性

## JVM 参数配置
CMS

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309260151327.png)

```
-Xms4g 堆的最大值
-Xmx4g 堆的初始化大小
-Xmn2g 新生代大小，建议取值范围在1~3g，比如32g堆大小时可以设为1g，64g堆大小时可以设为2g
-XX:SurvivorRatio=10 新生代中 Eden 区与 Survivor 区的比值，默认8
-XX:MetaspaceSize=512m
-XX:???zize=512m
-XX:MaxDirectMemorySize=768m
-XX:+UseConcMarkSweepGC
```

G1

```
 -server 
 -Xms10g
 -Xmx10g
 -XX:MaxNewSize=5g 
 -XX:ReservedcodeCachesize=2m 
 -XX:MetaspaceSize=512m 
 -XX:MaxMetaspaceSize=512m 
 -XX:MaxDirectMemorySize=1g 
 -XX:SurvivorRatio=10 
 -XX:+UseG1GC 
```


# 遇到的问题

## HSF 租户标被重置导致

## 线上死锁问题






# 机房环境、QPS、流量、机器、限流
两个机房：印尼、新加坡
印尼ID 部署在国际化印尼
SG PH TH VN MY 部署在国际化新加坡

OS30：70 台、150 台、170
SG52：40 台、98台、170 台
ID137：74台、94 台、 90 台
ID35：41 台、56 台、90 台
总：==220==台、 ==400== 台、 ==520== 台

OS30-simulator：2 台

发布系统：satellite
170台 lazada-expression-ns-s_rg_sg_online-==lazada-os30==_host
170台 lazada-expression-ns-s_lazada_sg_2_online-==lazada-sg52==_host
90台 lazada-expression-ns-s_rg_id_online-==lazada-id137==_host
90台 lazada-expression-ns-s_lazada_id_online-==lazada-id35==_host
其他还有 10 来个分组，每组 2 台

---

D9大促：

pdp（2K-6K）
ID=6000，
PH=6000，MY=2000，SG=1600，TH=6000，VN=3200
==总 QPS=25000==


queryForSource（3K-1W）

ID=5330， 限流 80对应 70 台机器，限流 120 对应 40 台机器
PH=15300，MY=3600，SG=2800，TH=10500，VN=5000，总 QPS=37200，限流 80 对应 465 台，限流 120 对应 310 台
==总 QPS=45000==， 限流 80 对应 ==520== 台，限流 120 对应 ==350== 台


confirm（200-900）
ID=260，
PH=830，MY=120，SG=170，TH=450，VN=250
==总 QPS= 2K==

---

sentinel 限流配置

1.query for item
DeliveryOptionFacade:queryShippingOptionForItem

2.query for source
FulfillmentServiceFacade:queryFulfillmentGroupService

3.confirm，写，很少

4.split纯内存计算，不需要配置

---

# 压测
cpu:五六十有问题，三四十没问题

扩容

# 作战手册

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309260113217.png)



cup水位

xflush,告警

cpu、jvm、tddl、tail、磁盘、内存、metaq

hsf接口上下游调用，hsf 提供者，消费者， rt, 成功率怎么看？
通过xflush、eagleeye

DB 监控，慢 sql

超卖

诺曼底，运维 ，dump 内存，分析、堆、栈

限流监控、xflush

中间件（satellite,diamond,sentinel，tddl等）

sls 日志，鹰眼，trace

hsf 下线

限流配置

预案操作

arthas 排查接口性能，排查接口报错

