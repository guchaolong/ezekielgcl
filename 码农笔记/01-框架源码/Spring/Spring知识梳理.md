#Spring 

# Spring概述 
## 什么是Spring框架


Spring 是<mark style="background: #FF5582A6;">开源</mark>的，最受欢迎的<mark style="background: #FF5582A6;">企业级 Java 应用</mark>程序<mark style="background: #FF5582A6;">开发框架</mark>，它的目标是简化企业级应用开发。

Spring 框架是一个<mark style="background: #FF5582A6;">轻量级</mark>的框架，它的核心容器非常小巧，只包含少量的类和接口，但它提供了很多<mark style="background: #FF5582A6;">可扩展</mark>的模块，可以根据需求灵活选择使用。Spring 框架采用<mark style="background: #FF5582A6;">松耦合</mark>的设计，可以和其他框架和库<mark style="background: #FF5582A6;">无缝集成</mark>，例如 Hibernate、MyBatis、Struts 等。

通过使用 Spring，开发者可以<mark style="background: #D2B3FFA6;">专注于业务逻辑</mark>的实现，而不需要关注一些<mark style="background: #D2B3FFA6;">底层的技术细节</mark>

>在Spring Framework基础上，又诞生了Spring Boot、Spring Cloud、Spring Data、Spring Security等一系列基于Spring Framework的项目


## Spring 的主要特性和优势：

从Spring 框架的**特性**来看：

1. **轻量级和非侵入性**：Spring 框架的核心容器非常<mark style="background: #FF5582A6;">小巧</mark>，不会强制开发者遵循特定的编程模型。基于Spring开发的应用中的对象可以<mark style="background: #FF5582A6;">不依赖于Spring的API</mark>
2. **控制反转**：IOC——Inversion of Control，指的是将<mark style="background: #FF5582A6;">对象的创建权</mark>交给 <mark style="background: #FF5582A6;">Spring</mark> 去创建。使用 Spring 之前，对象的创建都是由我们自己在代码中new创建。而使用 Spring 之后。对象的创建都是给了 Spring 框架
3. **依赖注入**：DI——Dependency Injection，是指依赖的对象不需要手动调用 setXX 方法去设置，而是<mark style="background: #FF5582A6;">通过配置</mark>赋值。通过<mark style="background: #FF5582A6;">依赖注入</mark>的方式<mark style="background: #FF5582A6;">管理对象之间的依赖关系</mark>，减少了类之间的耦合。
4. **面向切面编程**：Spring 框架提供了 AOP（面向切面编程）的支持，可以在<mark style="background: #FF5582A6;">不修改业务逻辑的情况下实现横切关注点</mark>的功能。
5. **事务管理**：Spring 框架提供了事务管理的支持，可以<mark style="background: #FF5582A6;">统一管理多个数据源的事务</mark>。
6. **Web 应用开发**：Spring 框架提供了 MVC（Model-View-Controller）的支持，可以方便地开发 Web 应用。
7. **容易测试**：Spring 框架的松耦合设计和依赖注入的支持，可以方便地进行单元测试和集成测试
8. **容器**：Spring 是一个容器，因为它包含并且管理应用对象的生命周期 
9. **组件化**：Spring 实现了使用简单的组件配置组合成一个复杂的应用。在 Spring 中可以使用XML和Java注解组合这些对象。 
10. **一站式**：在 IOC 和 AOP 的基础上可以整合各种企业应用的<mark style="background: #FF5582A6;">开源框架</mark>和优秀的<mark style="background: #FF5582A6;">第三方类库</mark>（实际上 Spring 自身也提供了表现层的 SpringMVC 和持久层的 Spring JDBC）

从使用Spring 框架的**好处**看：

- Spring 可以使开发人员使用 POJOs 开发企业级的应用程序。只使用 POJOs 的好处是你<mark style="background: #FF5582A6;">不需要一个 EJB 容器产品</mark>，比如一个应用程序服务器，但是你可以选择使用一个健壮的 servlet 容器，比如 Tomcat 或者一些商业产品。
- Spring 在一个单元模式中是有组织的。即使包和类的数量非常大，你只要担心你需要的，而其它的就可以忽略了。
- Spring 不会让你白费力气做<mark style="background: #FF5582A6;">重复工作</mark>，它真正的利用了一些现有的技术，像 ORM 框架、日志框架、JEE、Quartz 和 JDK 计时器，其他视图技术。
- 测试一个用 Spring 编写的应用程序很容易，因为环境相关的代码被移动到这个框架中。此外，通过使用 JavaBean-style POJOs，它在使用依赖注入注入测试数据时变得更容易。
- Spring 的 web 框架是一个设计良好的 web MVC 框架，它为比如 Structs 或者其他工程上的或者不怎么受欢迎的 web 框架提供了一个很好的供替代的选择。MVC 模式导致应用程序的不同方面(输入逻辑，业务逻辑和UI逻辑)分离，同时提供这些元素之间的松散耦合。模型(Model)封装了应用程序数据，通常它们将由 POJO 类组成。视图(View)负责渲染模型数据，一般来说它生成客户端浏览器可以解释 HTML 输出。控制器(Controller)负责处理用户请求并构建适当的模型，并将其传递给视图进行渲染。
- Spring 对 <mark style="background: #FF5582A6;">JavaEE</mark> 开发中非常难用的一些 <mark style="background: #FF5582A6;">API</mark>（JDBC、JavaMail、远程调用等），都<mark style="background: #FF5582A6;">提供了封装</mark>，使这些API应用难度大大降低。
- 轻量级的 IOC 容器往往是<mark style="background: #FF5582A6;">轻量</mark>级的，例如，特别是当与 EJB 容器相比的时候。这有利于在内存和 CPU 资源有限的计算机上开发和部署应用程序。
- Spring 提供了一致的<mark style="background: #FF5582A6;">事务管理</mark>接口，可向下扩展到（使用一个单一的数据库，例如）本地事务并扩展到全局事务（例如，使用 JTA）



Spring Framework主要包括几个模块：
- 支持<mark style="background: #FF5582A6;">IoC</mark>和<mark style="background: #FF5582A6;">AOP</mark>的<mark style="background: #FF5582A6;">容器</mark>；
- 支持<mark style="background: #FF5582A6;">JDBC</mark>和<mark style="background: #FF5582A6;">ORM</mark>的<mark style="background: #FF5582A6;">数据访问模块</mark>；
- 支持<mark style="background: #FF5582A6;">声明式事务</mark>的模块；
- 支持基于<mark style="background: #FF5582A6;">Servlet</mark>的MVC开发；
- 支持基于<mark style="background: #FF5582A6;">Reactive</mark>的Web开发；
- 以及集成<mark style="background: #FF5582A6;">JMS</mark>、<mark style="background: #FF5582A6;">JavaMail</mark>、<mark style="background: #FF5582A6;">JMX</mark>、缓存等其他模块


## Spring体系结构

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913102000.png)

### Core Container(核心容器)

核心容器由 spring-core，spring-beans，spring-context，spring-context-support和spring-expression（SpEL，Spring 表达式语言，Spring Expression Language）等模块组成，它们的细节如下：

- **spring-core** 模块提供了框架的基本组成部分，包括 <mark style="background: #FF5582A6;">IoC</mark> 和<mark style="background: #FF5582A6;">依赖注入</mark>功能。
- **spring-beans** 模块提供 <mark style="background: #FF5582A6;">BeanFactory</mark>，工厂模式的微妙实现，它移除了编码式单例的需要，并且可以把配置和依赖从实际编码逻辑中解耦。
- **context** 模块建立在由 **core**和 **beans** 模块的基础上建立起来的，它以一种类似于 JNDI 注册的方式访问对象。Context 模块继承自 Bean 模块，并且添加了国际化（比如，使用资源束）、事件传播、资源加载和透明地创建上下文（比如，通过 Servelet 容器）等功能。Context 模块也支持 Java EE 的功能，比如 EJB、JMX 和远程调用等。<mark style="background: #FF5582A6;">ApplicationContext</mark> 接口是 Context 模块的焦点。
- **spring-context-support** 提供了对第三方集成到 Spring 上下文的支持，比如缓存（EhCache, Guava, JCache）、邮件（JavaMail）、调度（CommonJ, Quartz）、模板引擎（FreeMarker, JasperReports, Velocity）等。
- **spring-expression** 模块提供了强大的<mark style="background: #FF5582A6;">表达式语言</mark>，用于在运行时查询和操作对象图。它是 JSP2.1 规范中定义的统一表达式语言的扩展，支持 set 和 get 属性值、属性赋值、方法调用、访问数组集合及索引的内容、逻辑算术运算、命名变量、通过名字从 Spring IoC 容器检索对象，还支持列表的投影、选择以及聚合等。
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913103630.png)


### Data Access/Integration（数据访问/集成）

数据访问/集成层包括 JDBC，ORM，OXM，JMS 和事务处理模块，它们的细节如下：

（注：JDBC=Java Data Base Connectivity，ORM=Object Relational Mapping，OXM=Object XML Mapping，JMS=Java Message Service）  

- **JDBC** 模块提供了 JDBC 抽象层，它消除了冗长的 JDBC 编码和对数据库供应商特定错误代码的解析。
    
- **ORM** 模块提供了对流行的对象关系映射 API 的集成，包括 JPA、JDO 和 Hibernate 等。通过此模块可以让这些 ORM 框架和 spring的其它功能整合，比如前面提及的事务管理。
    
- **OXM** 模块提供了对 OXM 实现的支持，比如 JAXB、Castor、XML Beans、JiBX、XStream 等。
    
- **JMS** 模块包含生产（produce）和消费（consume）消息的功能。从 Spring 4.1 开始，集成了 spring-messaging 模块。
    
- **事务**模块为实现特殊接口类及所有的 POJO 支持编程式和声明式事务管理。（注：编程式事务需要自己写 beginTransaction()、commit()、rollback() 等事务管理方法，声明式事务是通过注解或配置由 spring 自动处理，编程式事务粒度更细）

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913103130.png)



### Web

Spring 的 Web 层包括 Web、Servlet、WebSocket 和 Webflux 组件，具体介绍如下。

- **Web 模块**：提供了基本的 Web 开发集成特性，例如多文件上传功能、使用的 Servlet 监听器的 IOC 容器初始化以及 Web 应用上下文。
- **Servlet 模块**：提供了一个 Spring MVC Web 框架实现。Spring MVC 框架提供了基于注解的请求资源注入、更简单的数据绑定、数据验证等及一套非常易用的 JSP 标签，完全无缝与 Spring 其他技术协作。
- **WebSocket 模块**：提供了简单的接口，用户只要实现响应的接口就可以快速的搭建 WebSocket Server，从而实现双向通讯。
- **Webflux 模块**： Spring WebFlux 是 Spring Framework 5.x中引入的新的响应式web框架。与Spring MVC不同，它不需要Servlet API，是完全异步且非阻塞的，并且通过Reactor项目实现了Reactive Streams规范。Spring WebFlux 用于创建基于事件循环执行模型的完全异步且非阻塞的应用程序。

此外Spring4.x中还有Portlet 模块，在Spring 5.x中已经移除
- **Portlet 模块**：提供了在 Portlet 环境中使用 MVC 实现，类似 Web-Servlet 模块的功能。
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913103456.png)

### AOP、Aspects、Instrumentation和Messaging

在 Core Container 之上是 AOP、Aspects 等模块，具体介绍如下：

- **AOP 模块**：提供了面向切面编程实现，提供比如日志记录、权限控制、性能统计等通用功能和业务逻辑分离的技术，并且能动态的把这些功能添加到需要的代码中，这样各司其职，降低业务逻辑和通用功能的耦合。
- **Aspects 模块**：提供与 AspectJ 的集成，是一个功能强大且成熟的面向切面编程（AOP）框架。
- **Instrumentation 模块**：提供了类工具的支持和类加载器的实现，可以在特定的应用服务器中使用。
- **messaging 模块**：Spring 4.0 以后新增了消息（Spring-messaging）模块，该模块提供了对消息传递体系结构和协议的支持。
- **jcl 模块**： Spring 5.x中新增了日志框架集成的模块。

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913103828.png)


### Test模块

Test 模块：Spring 支持 Junit 和 TestNG 测试框架，而且还额外提供了一些基于 Spring 的测试功能，比如在测试 Web 框架时，模拟 Http 请求的功能。

包含Mock Objects, TestContext Framework, Spring MVC Test, WebTestClient。
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230913103945.png)



# Spring的核心要点
## 控制反转 - IOC
- Spring框架管理这些Bean的创建工作，即由用户管理Bean转变为框架管理Bean，这个就叫**控制反转 - Inversion of Control (IoC)**
- Spring 框架托管创建的Bean放在哪里呢？ 这便是**IoC Container**;
- Spring 框架为了更好让用户配置Bean，必然会引入**不同方式来配置Bean？ 这便是xml配置，Java配置，注解配置**等支持
- Spring 框架既然接管了Bean的生成，必然需要**管理整个Bean的生命周期**等；
- 应用程序代码从Ioc Container中获取依赖的Bean，注入到应用程序中，这个过程叫 **依赖注入(Dependency Injection，DI)** ； 所以说控制反转是通过依赖注入实现的，其实它们是同一个概念的不同角度描述。通俗来说就是**IoC是设计思想，DI是实现方式**
- 在依赖注入时，有哪些方式呢？这就是构造器方式，@Autowired, @Resource, @Qualifier... 同时Bean之间存在依赖（可能存在先后顺序问题，以及**循环依赖问题**等）
## 面向切面 - AOP
- Spring 框架通过定义切面, 通过拦截切点实现了不同业务模块的解耦，这个就叫**面向切面编程 - Aspect Oriented Programming (AOP)**
- 为什么@Aspect注解使用的是aspectj的jar包呢？这就引出了**Aspect4J和Spring AOP的历史渊源**，只有理解了Aspect4J和Spring的渊源才能理解有些注解上的兼容设计
- 如何支持**更多拦截方式**来实现解耦， 以满足更多场景需求呢？ 这就是@Around, @Pointcut... 等的设计
- 那么Spring框架又是如何实现AOP的呢？ 这就引入**代理技术，分静态代理和动态代理**，动态代理又包含JDK代理和CGLIB代理等


Spring设计的两个大的要点：IOC和AOP；从框架的设计角度而言，更为重要的是<mark style="background: #FF5582A6;">简化开发</mark>，最开始的<mark style="background: #FF5582A6;">xml配置</mark>,这种方式比较麻烦，然后就有了<mark style="background: #FF5582A6;">java配置</mark>方式（@Bean等注解）、<mark style="background: #FF5582A6;">注解配置方式</mark>（@Repository、@Service 等注解）、Springboot实际上通过 

Springboot通过<mark style="background: #FF5582A6;">约定大于配置</mark>的方式，使用xx-starter统一的<mark style="background: #FF5582A6;">对Bean进行默认初始化</mark>，用户只需要很少的配置就可以进行开发了

# IOC
## 什么是IOC？
Ioc—Inversion of Control，即“控制反转”，<mark style="background: #FF5582A6;">不是什么技术，而是一种设计思想</mark>。在Java开发中，Ioc意味着将你设计好的对象交给容器控制，而不是传统的在你的对象内部直接控制

## IoC和DI是什么关系
控制反转是通过依赖注入实现的，其实它们是同一个概念的不同角度描述。通俗来说就是<mark style="background: #FF5582A6;">IoC是设计思想，DI是实现方式</mark>。

## Spring IoC 容器
IOC 容器具有依赖注入功能的容器，它可以创建对象，IOC 容器负责实例化、定位、配置应用程序中的对象及建立这些对象间的依赖。通常new一个实例，控制权由程序员控制，而"控制反转"是指new实例工作不由程序员来做而是交给Spring容器来做。在Spring中<mark style="background: #FF5582A6;">BeanFactory</mark>是IOC容器的实际代表者

Spring实现IOC容器的方式有两种
1. <mark style="background: #FF5582A6;">BeanFactory</mark> 容器,spring框架的基础设施，<mark style="background: #FF5582A6;">面向spring本身</mark>
2. <mark style="background: #FF5582A6;">ApplicationContext</mark> 容器,BeanFactory的子接口，<mark style="background: #FF5582A6;">面向开发者</mark>，几乎所有的场合都可以使用ApprlicationContext而非底层的BeanFactory

### BeanFactory 容器
这是一个最简单的容器，它主要的功能是为依赖注入 （DI） 提供支持，这个容器接口在 org.springframework.beans.factory.BeanFactory中被定义。BeanFactory 和相关的接口，比如BeanFactoryAware、DisposableBean、InitializingBean，仍旧保留在 Spring 中，主要目的是向后兼容已经存在的和那些 Spring 整合在一起的第三方框架。

在 Spring 中，有大量对 BeanFactory 接口的实现。其中，最常被使用的是 **XmlBeanFactory** 类。这个容器从一个 XML 文件中读取配置元数据，由这些元数据来生成一个被配置化的系统或者应用。


在资源宝贵的移动设备或者基于 applet 的应用当中， BeanFactory 会被优先选择。否则，<mark style="background: #FF5582A6;">一般使用的是 ApplicationContext</mark>，除非你有更好的理由选择 BeanFactory

### ApplicationContext 容器
ApplicationContext 是 BeanFactory 的子接口，也被称为 <mark style="background: #FF5582A6;">Spring 上下文</mark>。  

ApplicationContext 是 spring 中<mark style="background: #FF5582A6;">较高级的容器</mark>。和 BeanFactory 类似，它可以加载配置文件中定义的 bean，将所有的 bean 集中在一起，当有请求的时候分配 bean。 另外，它增加了企业所需要的功能，比如，从属性文件中解析文本信息和将事件传递给所指定的监听器。

<mark style="background: #FF5582A6;">ApplicationContext 包含 BeanFactory 所有的功能</mark>，一般情况下，相对于 BeanFactory，ApplicationContext 会<mark style="background: #FF5582A6;">更加优秀</mark>。当然，BeanFactory 仍可以在轻量级应用中使用，比如移动设备或者基于 applet 的应用程序。

最常被使用的 ApplicationContext 接口实现：

- **FileSystemXmlApplicationContext**：该容器从 <mark style="background: #FF5582A6;">XML 文件中</mark>加载已被定义的 bean。在这里，你需要提供给构造器 <mark style="background: #FF5582A6;">XML 文件的完整路径</mark>。
    
- **ClassPathXmlApplicationContext**：该容器从 <mark style="background: #FF5582A6;">XML 文件中</mark>加载已被定义的 bean。在这里，你不需要提供 XML 文件的完整路径，只需正确配置 <mark style="background: #FF5582A6;">CLASSPATH</mark> 环境变量即可，因为，容器会从 CLASSPATH 中搜索 bean 配置文件。
    
- **XmlWebApplicationContext**：该容器会在一个 <mark style="background: #FF5582A6;">web 应用程序</mark>的范围内加载在 XML 文件中已被定义的 bean。

### BeanFactory和ApplicationContext的区别

`BeanFactory`和`ApplicationContext`的区别在于，`BeanFactory`的实现是<mark style="background: #FF5582A6;">按需创建</mark>，即<mark style="background: #FF5582A6;">第一次获取Bean时才创建这个Bean</mark>，而`ApplicationContext`会<mark style="background: #FF5582A6;">一次性创建所有的Bean</mark>。实际上，`ApplicationContext`接口是从`BeanFactory`接口继承而来的，并且，`ApplicationContext`提供了一些<mark style="background: #FF5582A6;">额外的功能</mark>，包括<mark style="background: #FF5582A6;">国际化支持</mark>、<mark style="background: #FF5582A6;">事件</mark>和<mark style="background: #FF5582A6;">通知机制</mark>等。通常情况下，我们总是使用`ApplicationContext`，很少会考虑使用`BeanFactory`


## Bean 定义（Ioc 配置的三种方式）
三个方法把配置元数据提供给 Spring 容器：
- 基于 XML 的配置文件
- 基于 Java 的配置（本质上就是把在XML上的配置声明转移到Java配置类中）
- 基于注解的配置

### XML配置：
顾名思义，就是将bean的信息配置.xml文件里，通过Spring加载文件为我们创建bean。这种方式出现很多早前的SSM项目中，将第三方类库或者一些配置工具类都以这种方式进行配置，主要原因是由于第三方类不支持Spring注解。

- **优点**： 可以使用于<mark style="background: #FF5582A6;">任何场景</mark>，结构清晰，通俗易懂
- **缺点**： <mark style="background: #FF5582A6;">配置繁琐</mark>，<mark style="background: #FF5582A6;">不易维护</mark>，枯燥无味，扩展性差
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
 http://www.springframework.org/schema/beans/spring-beans.xsd">
    <!-- services -->
    <bean id="userService" class="tech.pdai.springframework.service.UserServiceImpl">
        <property name="userDao" ref="userDao"/>
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>
    <!-- more bean definitions for services go here -->
</beans>
```

### Java配置：
将类的创建交给我们配置的JavcConfig类来完成，Spring只负责维护和管理，采用纯Java创建方式。其本质上就是把在XML上的配置声明转移到Java配置类中

- **优点**：适用于<mark style="background: #FF5582A6;">任何场景</mark>，配置方便，因为是纯Java代码，扩展性高，十分灵活
- **缺点**：由于是采用Java类的方式，声明不明显，如果大量配置，<mark style="background: #FF5582A6;">可读性比较差</mark>

1. 创建一个配置类， 添加<mark style="background: #FF5582A6;">@Configuration</mark>注解声明为配置类
2. 创建方法，方法上加上<mark style="background: #FF5582A6;">@Bean</mark>，该方法用于创建实例并返回，该实例创建后会交给spring管理，方法名建议与实例名相同（首字母小写）。注：实例类不需要加任何注解
```java
/**
 * @author 
 */
@Configuration
public class BeansConfig {

    /**
     * @return user dao
     */
    @Bean("userDao")
    public UserDaoImpl userDao() {
        return new UserDaoImpl();
    }

    /**
     * @return user service
     */
    @Bean("userService")
    public UserServiceImpl userService() {
        UserServiceImpl userService = new UserServiceImpl();
        userService.setUserDao(userDao());
        return userService;
    }
}
```

### 注解配置：
通过在类上加注解的方式，来声明一个类交给Spring管理，Spring会自动扫描带有<mark style="background: #FF5582A6;">@Component</mark>，<mark style="background: #FF5582A6;">@Controller</mark>，<mark style="background: #FF5582A6;">@Service</mark>，<mark style="background: #FF5582A6;">@Repository</mark>这四个注解的类，然后帮我们创建并管理，前提是需要先配置Spring的注解扫描器。

- **优点**：开发<mark style="background: #FF5582A6;">便捷</mark>，通俗易懂，方便维护。
- **缺点**：具有<mark style="background: #FF5582A6;">局限性</mark>，对于一些第三方资源，无法添加注解。只能采用XML或JavaConfig的方式配置

1. 对类添加@Component相关的注解，比如@Controller，@Service，@Repository
2. 设置ComponentScan的basePackage, 比如`<context:component-scan base-package='tech.pdai.springframework'>`, 或者`@ComponentScan("tech.pdai.springframework")`注解，或者 `new AnnotationConfigApplicationContext("tech.pdai.springframework")`指定扫描的basePackage.
```java
/**
 * @author pdai
 */
@Service
public class UserServiceImpl {

    /**
     * user dao impl.
     */
    @Autowired
    private UserDaoImpl userDao;

    /**
     * find user list.
     *
     * @return user list
     */
    public List<User> findUserList() {
        return userDao.findUserList();
    }

}
```


## Bean 作用域
Spring 框架支持以下五个作用域，分别为 singleton、prototype、request、session 和 global session

<mark style="background: #FF5582A6;">singleton</mark>：在spring IoC容器仅存在一个Bean实例，Bean以<mark style="background: #FF5582A6;">单例</mark>方式存在，是默认的作用域

<mark style="background: #FF5582A6;">prototype</mark>：每次从容器中调用Bean时，都返回一个<mark style="background: #FF5582A6;">新的实例</mark>，即每次调用getBean()时，相当于执行newXxxBean()

<mark style="background: #FF5582A6;">request</mark>：每次<mark style="background: #FF5582A6;">HTTP请求</mark>都会创建一个新的Bean，该作用域仅适用于WebApplicationContext环境

<mark style="background: #FF5582A6;">session</mark>:同一个<mark style="background: #FF5582A6;">HTTP Session</mark>共享一个Bean，不同Session使用不同的Bean，仅适用于WebApplicationContext环境 

<mark style="background: #FF5582A6;">global-session</mark>:一般用于<mark style="background: #FF5582A6;">Portlet</mark>应用环境，该作用域仅适用于WebApplicationContext环境 


Singleton 是单例类型，就是在创建起容器时就同时自动创建了一个 bean 的对象，不管你是否使用，他都存在了，每次获取到的对象都是同一个对象。注意，Singleton 作用域是 Spring 中的缺省作用域

Prototype 是原型类型，它在我们创建容器的时候并没有实例化，而是当我们获取bean的时候才会去创建一个对象，而且我们每次获取到的对象都不是同一个对象,根据经验，对有状态的 bean 应该使用 prototype 作用域，而对无状态的bean则应该使用 singleton 作用域

## Bean 生命周期

[请别再问Spring Bean的生命周期了！ - 简书](https://www.jianshu.com/p/1dec08d290c1)

<mark style="background: #FF5582A6;">只有四个！</mark>

1. 实例化 Instantiation
2. 属性赋值 Populate
3. 初始化 Initialization
4. 销毁 Destruction

实例化 -> 属性赋值 -> 初始化 -> 销毁

InstantiationAwareBeanPostProcessor作用于**实例化**阶段的前后，BeanPostProcessor作用于**初始化**阶段的前后
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230906110853.png)

<mark style="background: #FF5582A6;">InstantiationAwareBeanPostProcessor</mark>#postProcessBeforeInstantiation
Person()构造函数
<mark style="background: #FF5582A6;">InstantiationAwareBeanPostProcessor</mark>#postProcessAfterInstantiation

<mark style="background: #D2B3FFA6;">BeanNameAware</mark> setBeanName()  
<mark style="background: #D2B3FFA6;">BeanFactoryAware</mark> setBeanFactory()

<mark style="background: #FFB8EBA6;">BeanPostProcessor</mark>#postProcessBeforeInitialization
@<mark style="background: #BBFABBA6;">PostConstruct</mark> 注解的 自定义方法  
<mark style="background: #BBFABBA6;">InitializingBean</mark>接口afterPropertiesSet()  
<mark style="background: #FFB8EBA6;">BeanPostProcessor</mark>#postProcessAfterInitialization()！

@<mark style="background: #ADCCFFA6;">PreDestory</mark>注解自定义销毁方法
<mark style="background: #ADCCFFA6;">DisposableBe</mark>an接口destroy（）


## Bean 后置处理器
Bean 后置处理器允许在调用<mark style="background: #FF5582A6;">初始化方法前后</mark>对 Bean 进行额外的处理


# Spring依赖注入 DI

**Spring 中有这么3种依赖注入的方式**：
- 基于 field 注入（属性注入）
- 基于 setter 注入
- 基于 constructor 注入（构造器注入）

### 1. 基于 field 注入

所谓基于 field 注入，就是在bean的变量上使用注解进行依赖注入。本质上是通过反射的方式直接注入到field。这是我平常开发中看的最多也是最熟悉的一种方式，同时，也正是 Spring 团队所<mark style="background: #FF5582A6;">不推荐</mark>的方式。比如：

```java
@Autowired
private Svc svc;
```

好处:
简洁，代码看起来很<mark style="background: #FF5582A6;">简单</mark>，通俗易懂。你的类可以专注于业务而不被依赖注入所污染。你只需要把`@Autowired`扔到变量之上就好了，不需要特殊的构造器或者set方法，依赖注入容器会提供你所需的依赖

坏处：
基于 field 注入虽然简单，但是却会引发很多的问题。这些问题在我平常开发阅读项目代码的时候就经常遇见。
* <mark style="background: #FF5582A6;">容易违背了单一职责原则</mark> 使用这种基于 field 注入的方式，添加依赖是很简单的，就算你的类中有十几个依赖你可能都觉得没有什么问题，普通的开发者很可能会无意识地给一个类添加很多的依赖。但是当使用构造器方式注入，到了某个特定的点，构造器中的参数变得太多以至于很明显地发现something is wrong。拥有太多的依赖通常意味着你的类要承担更多的责任，明显违背了单一职责原则

* <mark style="background: #FF5582A6;">依赖注入与容器本身耦合</mark> 依赖注入框架的核心思想之一就是受容器管理的类不应该去依赖容器所使用的依赖。换句话说，这个类应该是一个简单的POJO(Plain Ordinary Java Object)能够被单独实例化并且你也能为它提供它所需的依赖。 这个问题具体可以表现在：你的类和依赖容器强耦合，<mark style="background: #FF5582A6;">不能在容器外使用</mark>，你的类不能绕过反射（例如单元测试的时候）进行实例化，必须通过<mark style="background: #FF5582A6;">依赖容器才能实例化</mark>，这更像是集成测试

* 不能使用属性注入的方式构建不可变对象(<mark style="background: #FF5582A6;">final</mark> 修饰的变量)


### 2. 基于 setter 方法注入
- **在XML配置方式中**，<mark style="background: #FF5582A6;">property</mark>都是setter方式注入，比如下面的xml:
```xml
    <bean id="userService" class="tech.pdai.springframework.service.UserServiceImpl">
        <property name="userDao" ref="userDao"/>
    </bean>
```
本质上包含两步：
1. 第一步，需要new UserServiceImpl()创建对象, 所以需要默认构造函数
2. 第二步，调用setUserDao()函数注入userDao的值, 所以`UserServiceImpl`中需要setUserDao()函数

> xml中的<mark style="background: #FF5582A6;">property</mark>，以及类中的<mark style="background: #FF5582A6;">setXXX</mark>函数



- **在注解和Java配置方式下**，通过对应变量的<mark style="background: #FF5582A6;">setXXX()</mark>方法以及在方法上面使用注解，来完成依赖注入。比如：

```java
private Helper helper;

@Autowired
public void setHelper(Helper helper) {
    this.helper = helper;
}
```

> 注：
> 1. 在Spring3.x刚推出的时候，推荐使用注入的就是这种, 但是这种方式比较麻烦，所以在Spring4.x版本中推荐构造函数注入。
> 2. 在 Spring 4.3及以后的版本中，setter 上面的 `@Autowired` 注解是<mark style="background: #FF5582A6;">可以不写</mark>的。



### 3. 基于 constructor 注入
**在XML配置方式中**，`<constructor-arg>`是通过构造函数参数注入，比如下面的xml:
```xml
    <bean id="userService" class="tech.pdai.springframework.service.UserServiceImpl">
        <constructor-arg name="userDao" ref="userDao"/>
    </bean>
```



将各个必需的依赖全部放在带有注解构造方法的参数中，并在构造方法中完成对应变量的初始化，这种方式，就是基于构造方法的注入。比如：
```java
private final Svc svc;

@Autowired
public HelpService(@Qualifier("svcB") Svc svc) {
    this.svc = svc;
}
```

> 在 `Spring 4.3` 及以后的版本中，如果这个类<mark style="background: #FF5582A6;">只有一个构造方法</mark>，那么这个构造方法上面也<mark style="background: #FF5582A6;">可以不写</mark> `@Autowired` 注解



## Spring 开发团队的建议

- 强制依赖就用构造器方式
- 可选、可变的依赖就用setter 注入

可以在同一个类中使用这两种方法。<mark style="background: #FF5582A6;">构造器注入</mark>更适合强制性的注入旨在<mark style="background: #FF5582A6;">不变性</mark>，<mark style="background: #FF5582A6;">Setter注入</mark>更适合<mark style="background: #FF5582A6;">可变性</mark>的注入

Spring 团队提倡使用基于构造方法的注入，因为这样一方面可以**将依赖注入到一个不可变的变量中 (注：`final` 修饰的变量)**，另一方面也可以**保证这些变量的值不会是 null**。此外，经过构造方法完成依赖注入的组件 (注：比如各个 `service`)，在被调用时可以**保证它们都完全准备好了**。与此同时，从代码质量的角度来看，**一个巨大的构造方法通常代表着出现了代码异味，这个类可能承担了过多的责任**。

而对于基于 setter 的注入，他们是这么说的：
基于 setter 的注入，则只应该被用于注入非必需的依赖，同时在类中应该对这个依赖提供一个合理的默认值。如果使用 setter 注入必需的依赖，那么将会有过多的 null 检查充斥在代码中。**使用 setter 注入的一个优点是，这个依赖可以很方便的被改变或者重新注入**。

spring推荐使用setter方法和构造器注入Autowired的bean对象，因此IDEA等工具中私有属性使用Autowired注入会提示警告。setter方法和构造器注入的方式，可以让对象不依赖于spring而独立使用，更加灵活；私有属性则只能通过spring上下文自动注入，一旦注入失败，没有重新注入的方式


## @Autowired, @Inject, @Resource  三个注解的区别
Spring 支持使用`@Autowired`, `@Resource`, `@Inject` 三个注解进行依赖注入

1 @Autowired

`@Autowired`为Spring 框架提供的注解

<mark style="background: #FF5582A6;">装配顺序</mark>：
1. 优先<mark style="background: #FF5582A6;">byType</mark>，其次<mark style="background: #FF5582A6;">byName</mark>
2. @Autowired 和 <mark style="background: #FF5582A6;">@Qualifier</mark> 结合使用时，自动注入的策略就从 byType 转变成 <mark style="background: #FF5582A6;">byName</mark> 了，按照`@Qualifier`指定的`name`进行匹配，如果没有，则按照<mark style="background: #FF5582A6;">变量名</mark>进行匹配，匹配不到，则报错。`@Autowired(required=false)`(默认为`true`)，如果设置`required`为`false`，则注入失败时不会抛出异常 


2 @Inject

在Spring 的环境下，**`@Inject`和`@Autowired` 是相同的**
如果硬要说两个的区别，首先`@Inject`是Java EE包里的，在SE环境需要单独引入。另一个区别在于`@Autowired`可以设置`required=false`而`@Inject`并没有这个属性

@Inject是根据<mark style="background: #FF5582A6;">类型</mark>进行自动装配的，如果需要按名称进行装配，则需要配合<mark style="background: #FF5582A6;">@Named</mark>
@Inject可以作用在变量、setter方法、构造函数上，和@Autowired一样
@Named("xxx") 中的 xxx是 Bean 的名称，所以 @Inject和 @Named结合使用时，自动注入的策略就从 byType 转变成 byName 了



3 @Resource

@Resource注解是jdk提供的，属于j2ee规范有两个重要的属性：name和type，而Spring 将@Resource注解的name属性解析为bean的名字，而type属性则解析为bean的类型。

Resource注解优先<mark style="background: #FF5582A6;">byname</mark>获取java bean，其次<mark style="background: #FF5582A6;">byType</mark>

Resource注解的属性名称作为java bean的名称进行查找，如果有name参数，则使用name参数查找java bean

Resource注解如果声明了name属性，则必须按照name查找对象，不会再使用类型查找

@Resource可以作用在变量、setter方法上, @Resource不能用于构造器注入


# AOP

## 什么是AOP

AOP:Aspect Oriented Programming 面向切面编程，通过预编译或运行期动态代理实现程序功能的统一维护的一种技术 

每个业务方法，除了自身的<mark style="background: #FF5582A6;">业务逻辑</mark>，还需要<mark style="background: #FF5582A6;">安全检查</mark>、<mark style="background: #FF5582A6;">日志记录</mark>和<mark style="background: #FF5582A6;">事务处理</mark>等，如果没有AOP，就会出现大量重复的代码


主要功能是：**日志记录**、**性能统计**、**安全控制**、**事务处理**、**异常处理**等

## AOP的实现方式 

在Java平台上，对于AOP的织入，有3种方式：

1. 编译期：在编译时，由编译器把切面调用编译进字节码，这种方式需要定义新的关键字并扩展编译器，AspectJ就扩展了Java编译器，使用关键字aspect来实现织入；
2. 类加载器：在目标类被装载到JVM时，通过一个特殊的类加载器，对目标类的字节码重新“增强”；
3. 运行期动态代理：目标对象和切面都是普通Java类，通过JVM的动态代理功能或者第三方库实现运行期动态织入。(JDK的动态代理、CGLib的动态代理）如SpringAOP、JbossAOP

最简单的方式是第三种，<mark style="background: #FF5582A6;">Spring的AOP实现就是基于JVM的动态代理</mark>。由于<mark style="background: #FF5582A6;">JVM的动态代理要求必须实现接口</mark>，如果一个<mark style="background: #FF5582A6;">普通类</mark>没有业务接口，就需要通过[CGLIB](https://github.com/cglib/cglib)或者[Javassist](https://www.javassist.org/)这些第三方库实现。

<mark style="background: #FF5582A6;">Spring Boot 2之后，默认使用CGLIB代理，不论被代理的类是否实现接口</mark>

AOP技术看上去比较神秘，但实际上，它本质就是一个动态代理，让我们把一些常用功能如权限检查、日志、事务等，从每个业务方法中剥离出来。


## 相关概念
在AOP编程中，我们经常会遇到下面的概念：
- Aspect：切面，即一个横跨多个核心逻辑的功能，或者称之为系统关注点；
- Joinpoint：连接点，即定义在应用程序流程的何处插入切面的执行；
- Pointcut：切入点，即一组连接点的集合；
- Advice：增强，指特定连接点上执行的动作；
- Introduction：引介，指为一个已有的Java对象动态地增加新的接口；
- Weaving：织入，指将切面整合到程序的执行流程中；
- Interceptor：拦截器，是一种实现增强的方式；
- Target Object：目标对象，即真正执行业务的核心逻辑对象；
- AOP Proxy：AOP代理，是客户端持有的增强后的对象引用。


