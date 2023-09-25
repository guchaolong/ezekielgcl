
# 业务
P2P（几个小时） 
Express 1-2天
STD 3-10 天
Economy 10-20天  

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309242113317.png)

商品添加到购物车
购物车中多选商品
拆包
redmart、digital、preSale、sof、sellerId、channel


# 技术栈

## 云原生
[[Lazada云原生]]

## 中间件
Diamond 
~~Mcms~~
Metaq
Tair
Schedule X

hsf
mq
精卫
ODPS
sls



## Pandora

Pandora Boot可以认为是Spring Boot的增强

pandora boot starters
* pandora-hsf-spring-boot-starter
* pandora-diamond-spring-boot-starter
* pandora-metaq-spring-boot-starter
* pandora-notify-spring-boot-starter
* pandora-tddl-spring-boot-starter
* pandora-tair-spring-boot-starter


## HSF
[HSF 基础记录\_落小渔的博客-CSDN博客](https://blog.csdn.net/weixin_35821291/article/details/122978538)

[使用HSF开发应用\_企业级分布式应用服务 EDAS-阿里云帮助中心](https://help.aliyun.com/zh/edas/developer-reference/use-hsf-to-develop-applications/?spm=a2c4g.11186623.0.0.1115514bGTkkOe)











轻量级配置中心（Diamond）是淘宝内部广泛使用的配置中心，提供持久化管理和动态配置推送服务。应用方发布的配置会通过持久化存储保存，与发布者的生命周期无关

轻量级注册中心（ConfigServer）

分布式消息系统Notify
分布式RPC框架HSF提供地址发现服务。

metaq
精卫
schedulex
hsf
tail
流程引擎 smartEngine
TMF
rest2hsf
odps

TDDL 分布式数据库中间件

HSF、，MetaQ、TDDL、Diamond、Tair、TXC 等

sls 是看线上日志的日志系统，就是 kafuka

Arthas 问题排查工具

eagleeye、xflush
业务监控系统 Sunfire,前身是蚂蚁的 xflush,支持应用标准化监控，如操作系统，JVM，中间件等,除此之外还有更强大的日志监控能力，大多数业务的监控指标都从应用的日志中抽取。目前覆盖了集团几乎所有 BU 和绝大多数业务，每分钟处理 TB 级日志。


docker 镜像
hubernetes 部署、动态编排



切流/灰度方案










ODPS 同步数据





# 预案降级：
* 购物车降级，appName是 CART，采用默认时效
* 增加 RC 数据缓存的相关存活时间 比如，240->2880
* 停止所有的从 ODPS 同步数据的自动任务 
* 降级代码中部分方法打印的日志，防止磁盘被打爆 
* 降级通过经纬度查距离，执行后，影响 VN，MY,ID部分的 P2场景线路透出 
* degradeSellerHolidayQuery 
* 对查询卖家类型接口进行降级，采用默认的卖家类型， 
* o2o 商品选中 pickup in store 物流选项获取的门店列表信息都不回透出距离信息，下单业务不收影响，执行后，不会再去调地址接口，门店列表信息正常，距离信息为空


lazada-rc-s:管理供应链中涉及到的资源

lazada-expression-ns-s:中台化应用，交易前拆单，下单服务决策，服务承诺列表及运费计算




# 作战手册
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


# WorkGuide

表达应用：
启动器，global-expression-s
中台地址 global-supplychain-expression
站点地址 lazada-expression-ns-s 
rc lazada-resource-center



# 部署、机器、环境

两个机房：印尼、新加坡
印尼ID 部署在国际化印尼
SG PH TH VN MY 部署在国际化新加坡

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202309242045016.png)


预发环境

生产环境
ID137
74台
94 台

ID35
41 台
56 台



OS30
70 台
150 台


SG52
40 台
98台



OS30-simulator
2 台

发布系统：satellite


# 限流配置
sentinel

1.query for item
DeliveryOptionFacade:queryShippingOptionForItem

2.query for source
FulfillmentServiceFacade:queryFulfillmentGroupService

3.confirm，写，很少

4.split纯内存计算，不需要配置


# 数据库
逻辑库
global_expression_lazada_sg
global_expression_lazada_id
global_expression_lazada_th
global_expression_lazada_ph
global_expression_lazada_vn
global_expression_lazada_my

物理库就是后面加上 0000-0063，比如global_expression_lazada_0000 这种





# 压测
cpu:五六十有问题，三四十没问题

扩容




# 贡献
## 赔付

