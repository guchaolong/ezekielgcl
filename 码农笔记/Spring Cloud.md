
# 项目架构演变：

* 单体：all in one
* 垂直：一个应用<mark style="background: #FF5582A6;">拆</mark>成<mark style="background: #FF5582A6;">互不相干</mark>的几个应用，系统间<mark style="background: #FF5582A6;">相互独立</mark>，有<mark style="background: #FF5582A6;">重复代码</mark>
* 分布式服务：将重复的代码<mark style="background: #FF5582A6;">抽取</mark>出来，做成统一的业务层作为独立的<mark style="background: #FF5582A6;">服务</mark>
* SOA 架构：
* 微服务架构

# 服务远程调用：

方式：
* RPC （如 dubbo)
* HTTP

HTTP客户端工具：HttpClient、OKHttp、URLConnection

而Spring也有对http的客户端进行封装，提供了工具类叫 <mark style="background: #FF5582A6;">RestTemplate</mark>
```java
User user = restTemplate.getForObject("http://localhost/user/8", User.class);
```


# Spring Cloud

涉及的组件包括：
* Eureka：注册中心 
* Zuul、Gateway：服务网关 
* Ribbon：负载均衡 
* Feign：服务调用 
* Hystrix或Resilience4j：熔断器

# Eureka
* Eureka：就是服务注册中心（可以是一个集群），对外暴露自己的地址 
* 提供者：启动后向Eureka<mark style="background: #FF5582A6;">注册</mark>自己信息（地址，提供什么服务） 
* 消费者：向Eureka<mark style="background: #FF5582A6;">订阅</mark>服务，Eureka会将对应服务的所有提供者地址列表发送给消费者，并且定期更新 
* 心跳(续约)：提供者定期通过http方式向Eureka<mark style="background: #FF5582A6;">刷新</mark>自己的<mark style="background: #FF5582A6;">状态</mark>



