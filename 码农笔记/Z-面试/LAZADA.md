
# 业务
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


# 表达架构
表达应用：
启动器，global-expression-s
中台地址 global-supplychain-expression
站点地址 lazada-expression-ns-s 
rc lazada-resource-center

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



# 需求案例，做了哪些事
## 赔付

## G1、FullGC问题


# 遇到的问题

## HSF 租户标被重置导致 LSF 调用表达失败



# GC
CMS

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309260151327.png)

G1







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

