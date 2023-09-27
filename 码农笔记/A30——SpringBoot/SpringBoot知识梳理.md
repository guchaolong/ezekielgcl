#SpringBoot 

# 概述
SpringBoot提供了一种快速使用Spring的方式，因为 Spring 需要大量的 xml 配置文件，配置繁琐，依赖繁琐

SpringBoot 基于约定优于配置，提高了开发效率

Spring Boot <mark style="background: #FF5582A6;">并不是</mark>对 Spring 功能上的<mark style="background: #FF5582A6;">增强</mark>，而是提供了一种<mark style="background: #FF5582A6;">快速使用</mark> Spring 的方式


# starter
Spring Boot 推荐的基础 POM 文件

|名称|说明|
|---|---|
|spring-boot-starter|核心 POM，包含自动配置支持、日志库和对 YAML 配置文件的支持。|
|spring-boot-starter-amqp|通过 spring-rabbit 支持 AMQP。|
|spring-boot-starter-aop|包含 spring-aop 和 AspectJ 来支持面向切面编程（AOP）。|
|spring-boot-starter-batch|支持 Spring Batch，包含 HSQLDB。|
|spring-boot-starter-data-jpa|包含 spring-data-jpa、spring-orm 和 Hibernate 来支持 JPA。|
|spring-boot-starter-data-mongodb|包含 spring-data-mongodb 来支持 MongoDB。|
|spring-boot-starter-data-rest|通过 spring-data-rest-webmvc 支持以 REST 方式暴露 Spring Data 仓库。|
|spring-boot-starter-jdbc|支持使用 JDBC 访问数据库。|
|spring-boot-starter-security|包含 spring-security。|
|spring-boot-starter-test|包含常用的测试所需的依赖，如 JUnit、Hamcrest、Mockito 和 spring-test 等。|
|spring-boot-starter-velocity|支持使用 Velocity 作为模板引擎。|
|spring-boot-starter-web|支持 Web 应用开发，包含 Tomcat 和 spring-mvc。|
|spring-boot-starter-websocket|支持使用 Tomcat 开发 WebSocket 应用。|
|spring-boot-starter-ws|支持 Spring Web Services。|
|spring-boot-starter-actuator|添加适用于生产环境的功能，如性能指标和监测等功能。|
|spring-boot-starter-remote-shell|添加远程 SSH 支持。|
|spring-boot-starter-jetty|使用 Jetty 而不是默认的 Tomcat 作为应用服务器。|
|spring-boot-starter-log4j|添加 Log4j 的支持。|
|spring-boot-starter-logging|使用 Spring Boot 默认的日志框架 Logback。|
|spring-boot-starter-tomcat|使用 Spring Boot 默认的 Tomcat 作为应用服务器。|

所有这些 POM 依赖的好处在于为开发 Spring 应用提供了一个良好的基础。Spring Boot 所选择的第三方库是经过考虑的，是比较适合产品开发的选择。但是 Spring Boot 也提供了不同的选项，比如日志框架可以用 Logback 或 Log4j，应用服务器可以用 Tomcat 或 Jetty。


# 配置文件
SpringBoot 是基于约定的，所以很多<mark style="background: #FF5582A6;">配置</mark>都有<mark style="background: #FF5582A6;">默认值</mark>，但如果想使用自己的配置替换默认配置的话，就可以使用application.properties或者application.yml（application.yaml）进行配置

# SpringBoot启动流程


# 事件监听
Java中的事件监听机制定义了以下几个角色：

①事件：<mark style="background: #FF5582A6;">Event</mark>，继承 java.util.EventObject 类的对象

②事件源：<mark style="background: #FF5582A6;">Source</mark> ，任意对象Object

③监听器：<mark style="background: #FF5582A6;">Listener</mark>，实现 java.util.EventListener 接口 的对象

SpringBoot 在<mark style="background: #FF5582A6;">项目启动</mark>时，会对几个<mark style="background: #FF5582A6;">监听器</mark>进行回调，我们可以<mark style="background: #FF5582A6;">实现</mark>这些监听器接口，在<mark style="background: #FF5582A6;">项目启动时完成一些操作</mark>。

- ApplicationContextInitializer
    
- SpringApplicationRunListener
    
- CommandLineRunner
    
- ApplicationRunner

> 自定义监听器的启动时机：MyApplicationRunner和MyCommandLineRunner都是当项目启动后执行，使用@Component放入容器即可使用


