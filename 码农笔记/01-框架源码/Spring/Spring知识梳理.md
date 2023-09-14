#Spring 

# Spring概述 
## 什么是Spring框架


Spring 是<mark style="background: #FF5582A6;">开源</mark>的，最受欢迎的<mark style="background: #FF5582A6;">企业级 Java 应用</mark>程序<mark style="background: #FF5582A6;">开发框架</mark>，它的目标是简化企业级应用开发。

Spring 框架是一个<mark style="background: #FF5582A6;">轻量级</mark>的框架，它的核心容器非常小巧，只包含少量的类和接口，但它提供了很多<mark style="background: #FF5582A6;">可扩展</mark>的模块，可以根据需求灵活选择使用。Spring 框架采用<mark style="background: #FF5582A6;">松耦合</mark>的设计，可以和其他框架和库<mark style="background: #FF5582A6;">无缝集成</mark>，例如 Hibernate、MyBatis、Struts 等。

通过使用 Spring，开发者可以<mark style="background: #D2B3FFA6;">专注于业务逻辑</mark>的实现，而不需要关注一些<mark style="background: #D2B3FFA6;">底层的技术细节</mark>

>在Spring Framework基础上，又诞生了Spring Boot、Spring Cloud、Spring Data、Spring Security等一系列基于Spring Framework的项目


## Spring的主要特性和优势：

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


### Test

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

所谓基于 field 注入，就是在bean的变量上使用注解进行依赖注入。本质上是通过反射的方式直接注入到field。属性注入是我们最熟悉，也是日常开发中使用最多的一种注入方式，同时，也正是 Spring 团队所<mark style="background: #FF5582A6;">不推荐</mark>的方式。比如：

```java
@RestController
public class UserController {
    // 属性对象
    @Autowired
    private UserService userService;

    @RequestMapping("/add")
    public UserInfo add(String username, String password) {
        return userService.add(username, password);
    }
}
```

<mark style="background: #D2B3FFA6;">好处:</mark>
属性注入最大的优点就是实现<mark style="background: #FF5582A6;">简单</mark>、使用简单，只需要给变量上添加一个注解（@Autowired），就可以在不 new 对象的情况下，直接获得注入的对象了（这就是 DI 的功能和魅力所在），所以它的优点就是使用简单

<mark style="background: #D2B3FFA6;">坏处：</mark>
然而，基于 field 注入虽然简单，但是却会引发很多的问题。这些问题在我平常开发阅读项目代码的时候就经常遇见，甚至编译器 Idea 都会提醒你“不建议使用此注入方式”
属性注入的缺点主要包含以下 3 个：

* 功能性问题：一个<mark style="background: #FF5582A6;">不可变</mark>的对象（<mark style="background: #FF5582A6;">final</mark> 修饰的变量）；
  原因也很简单：在 Java 中 final 对象（不可变）要么直接赋值，要么在构造方法中赋值，所以当使用属性注入 final 对象时，它不符合 Java 中 final 的使用规范，所以就不能注入成功了

* 通用性问题：只能适应于 IoC 容器；
  使用属性注入的方式只适用于 IoC 框架（容器），<mark style="background: #FF5582A6;">与容器本身耦合</mark>，<mark style="background: #FF5582A6;">不能在容器外使用</mark>，必须通过<mark style="background: #FF5582A6;">容器才能实例化</mark>，如果将属性注入的代码移植到其他非 IoC 的框架中，那么代码就无效了，所以属性注入的通用性不是很好。

* 设计原则问题：更容易违背单一设计原则
  使用属性注入的方式，因为使用起来很<mark style="background: #FF5582A6;">简单</mark>，所以开发者很容易在一个类中同时<mark style="background: #FF5582A6;">注入多个对象</mark>，而这些对象的注入<mark style="background: #FF5582A6;">是否有必要</mark>？是否符合程序设计中的<mark style="background: #FF5582A6;">单一职责原则</mark>？就变成了一个问题。但可以肯定的是，注入实现越简单，那么<mark style="background: #FF5582A6;">滥用它的概率也越大</mark>，所以出现违背单一职责原则的概率也越大。注意：这里强调的是违背设计原则（单一职责）的可能性，而不是一定会违背设计原则，二者有着本质的区别

* **循环依赖的问题**：
  使用<mark style="background: #FF5582A6;">field注入</mark>可能会导致<mark style="background: #FF5582A6;">循环依赖</mark>，即A里面注入B，B里面又注入A：如果使用<mark style="background: #FF5582A6;">构造器注入</mark>，在spring项目<mark style="background: #FF5582A6;">启动的时候</mark>，就会<mark style="background: #FF5582A6;">抛出异常</mark>：BeanCurrentlyInCreationException：Requested bean is currently in creation: Is there an unresolvable circular reference？从而提醒你避免循环依赖，如果是<mark style="background: #FF5582A6;">field注入</mark>的话，<mark style="background: #FF5582A6;">启动的时候不会报错</mark>，在<mark style="background: #FF5582A6;">使用</mark>那个bean的时候才会<mark style="background: #FF5582A6;">报错</mark>



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
@RestController
public class UserController {
    // Setter 注入
    private UserService userService;

    @Autowired
    public void setUserService(UserService userService) {
        this.userService = userService;
    }

    @RequestMapping("/add")
    public UserInfo add(String username, String password) {
        return userService.add(username, password);
    }
}
```

优点：
* 它<mark style="background: #FF5582A6;">完全符合单一职责的设计原则</mark>，因为每一个 Setter 只针对一个对象。
* 这个依赖可以很方便的被<mark style="background: #FF5582A6;">改变</mark>或者<mark style="background: #FF5582A6;">重新注入</mark>

缺点：
但它的缺点也很明显，它的缺点主要体现在以下 2 点：
* <mark style="background: #FF5582A6;">1.不能注入不可变对象</mark>（final 修饰的对象）；
  ![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230914000048.png)

* 2.注入的对象<mark style="background: #FF5582A6;">可被修改</mark>
  因为提供了 setXXX 的方法，意味着你可以在任何时候、在任何地方，通过调用 setXXX 的方法来改变注入对象，所以 Setter 注入的问题是，被注入的对象可能随时被修改

> 注：
> 1. 在Spring3.x刚推出的时候，推荐使用注入的就是这种, 但是这种方式比较麻烦，所以在Spring4.x版本中推荐构造函数注入。
> 2. 在 Spring 4.3及以后的版本中，setter 上面的 @Autowired 注解是<mark style="background: #FF5582A6;">可以不写</mark>的。



### 3. 基于 constructor 注入
**在XML配置方式中**，`<constructor-arg>`是通过构造函数参数注入，比如下面的xml:
```xml
    <bean id="userService" class="tech.pdai.springframework.service.UserServiceImpl">
        <constructor-arg name="userDao" ref="userDao"/>
    </bean>
```
> xml中用constructor-arg，`UserServiceImpl`中要申明<mark style="background: #FF5582A6;">构造函数</mark>


- **在注解和Java配置方式下**
将各个必需的依赖全部放在带有注解构造方法的参数中，并在构造方法中完成对应变量的初始化，这种方式，就是基于构造方法的注入。比如：
```java
@RestController
public class UserController {
    // 构造方法注入
    private UserService userService;

    @Autowired
    public UserController(UserService userService) {
        this.userService = userService;
    }

    @RequestMapping("/add")
    public UserInfo add(String username, String password) {
        return userService.add(username, password);
    }
}
```

> 在Spring4.x版本中推荐的注入方式就是这种
> 
> 在 `Spring 4.3` 及以后的版本中，如果这个类<mark style="background: #FF5582A6;">只有一个构造方法</mark>，那么这个构造方法上面也<mark style="background: #FF5582A6;">可以不写</mark> `@Autowired` 注解

优点：
构造方法注入相比于前两种注入方法，它<mark style="background: #FF5582A6;">可以注入不可变对象</mark>，并且<mark style="background: #FF5582A6;">它只会执行一次</mark>，也<mark style="background: #FF5582A6;">不存在像 Setter 注入那样，被注入的对象随时被修改的情况</mark>，它的优点有：

- <mark style="background: #FF5582A6;">可注入不可变对象</mark>（<mark style="background: #FF5582A6;">final</mark> 修饰的变量）；

- <mark style="background: #FF5582A6;">注入对象不会被修改；</mark>
  构造方法注入不会像 Setter 注入那样，构造方法在对象创建时只会执行一次，因此它不存在注入对象被随时（调用）修改的情况
  
* <mark style="background: #FF5582A6;">依赖不为空</mark>（省去了我们对其检查）
  当要实例化UserController的时候，由于自己实现了有参数的构造函数，所以不会调用默认构造函数，那么就需要Spring容器传入所需要的参数，所以就两种情况：1、有该类型的参数->传入，OK 。2：无该类型的参数->报错。
  
- <mark style="background: #FF5582A6;">注入对象会被完全初始化</mark>；
  因为依赖对象是在构造方法中执行的，而构造方法是在对象创建之初执行的，因此被注入的对象在使用之前，会被完全初始化，这也是构造方法注入的优点之一
 
  这个可以跟上面的依赖不为空结合起来，向构造器传参之前，要确保注入的内容不为空，那么肯定要调用依赖组件的构造方法完成实例化。而在Java类加载实例化的过程中，构造方法是最后一步（之前如果有父类先初始化父类，然后自己的成员变量，最后才是构造方法），所以返回来的都是初始化之后的状态
  
- <mark style="background: #FF5582A6;">通用性更好；不依赖IOC容器</mark>
  构造方法和属性注入不同，构造方法注入可适用于任何环境，无论是 IoC 框架还是非 IoC 框架，构造方法注入的代码都是通用的，所以它的通用性更好
  
* <mark style="background: #FF5582A6;">循环依赖的问题</mark>：使用<mark style="background: #FF5582A6;">field注入</mark>可能会导致<mark style="background: #FF5582A6;">循环依赖</mark>，即A里面注入B，B里面又注入A：如果使用<mark style="background: #FF5582A6;">构造器注入</mark>，在spring项目<mark style="background: #FF5582A6;">启动的时候</mark>，就会<mark style="background: #FF5582A6;">抛出异常</mark>：BeanCurrentlyInCreationException：Requested bean is currently in creation: Is there an unresolvable circular reference？从而提醒你避免循环依赖，如果是<mark style="background: #FF5582A6;">field注入</mark>的话，<mark style="background: #FF5582A6;">启动的时候不会报错</mark>，在<mark style="background: #FF5582A6;">使用</mark>那个bean的时候才会<mark style="background: #FF5582A6;">报错</mark>

Spring 开发团队的建议
- <mark style="background: #FF5582A6;">强制依赖</mark>就用<mark style="background: #FF5582A6;">构造器</mark>方式
- <mark style="background: #FF5582A6;">可选、可变的依赖</mark>就用<mark style="background: #FF5582A6;">setter</mark> 注入


## @Autowired, @Inject, @Resource  三个注解的区别
Spring 支持使用`@Autowired`, `@Resource`, `@Inject` 三个注解进行依赖注入

1 @Autowired

`@Autowired`为Spring 框架提供的注解

<mark style="background: #FF5582A6;">装配顺序</mark>：
1. 优先<mark style="background: #FF5582A6;">byType</mark>(默认），其次<mark style="background: #FF5582A6;">byName</mark>
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


4 总结：
* @<mark style="background: #FF5582A6;">Autowired</mark>是<mark style="background: #FF5582A6;">Spring自带</mark>的，@<mark style="background: #FF5582A6;">Resource</mark>是<mark style="background: #FF5582A6;">JSR250</mark>规范实现的，@<mark style="background: #FF5582A6;">Inject</mark>是<mark style="background: #FF5582A6;">JSR330</mark>规范实现的

* <mark style="background: #FF5582A6;">@Autowired、@Inject用法基本一样</mark>，不同的是<mark style="background: #FF5582A6;">@Inject没有required属性</mark>

* <mark style="background: #FF5582A6;">@Autowired、@Inject</mark>是默认按照<mark style="background: #FF5582A6;">类型</mark>匹配的，<mark style="background: #FF5582A6;">@Resource</mark>是按照<mark style="background: #FF5582A6;">名称</mark>匹配的

* <mark style="background: #FF5582A6;">@Autowired</mark>如果需要按照名称匹配需要和<mark style="background: #FF5582A6;">@Qualifier</mark>一起使用，<mark style="background: #FF5582A6;">@Inject</mark>和<mark style="background: #FF5582A6;">@Named</mark>一起使用，<mark style="background: #FF5582A6;">@Resource</mark>则通过<mark style="background: #FF5582A6;">name</mark>进行指定


# AOP

## 什么是AOP

AOP:Aspect Oriented Programming 面向切面编程，通过<mark style="background: #FF5582A6;">预编译</mark>或<mark style="background: #FF5582A6;">运行期动态代理</mark>实现程序功能的统一维护的一种技术 

每个业务方法，除了自身的<mark style="background: #FF5582A6;">业务逻辑</mark>，还需要<mark style="background: #FF5582A6;">安全检查</mark>、<mark style="background: #FF5582A6;">日志记录</mark>和<mark style="background: #FF5582A6;">事务处理</mark>等，如果没有AOP，就会出现大量重复的代码

AOP又叫`面向切面编程`，旨在通过允许横切关注点的分离，提高`模块化`。通俗理解就是，将那些与业务无关，却为业务模块所共同调用的逻辑代码封装起来，形成一个切面，使原来的业务功能更加强大，即`增强`，并`减少重复代码`，`降低`模块间的`耦合度`，方便后期操作和维护

AOP的理念：就是将分散在各个业务逻辑代码中相同的代码通过**横向切割**的方式抽取到一个独立的模块中！
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230914005556.png)


主要功能是：**日志记录**、**性能统计**、**安全控制**、**事务处理**、**异常处理**等

## 静态代理和动态代理区别

AOP实现的关键就在于AOP框架自动创建的AOP代理，AOP代理则可分为静态代理和动态代理两大类

`静态代理`是指使用<mark style="background: #FF5582A6;">AOP框架</mark>提供的命令进行编译，从而在编译阶段就可生成 AOP 代理类，因此也称为`编译时增强`

`动态代理`则在运行时借助于<mark style="background: #FF5582A6;">JDK动态代理</mark>、<mark style="background: #FF5582A6;">CGLIB</mark>等在内存中“临时”生成AOP动态代理类，因此也被称为`运行时增强`

## cglib和jdk动态代理的区别？ 

- cglib动态代理：利用`ASM框架`，对代理对象类生成的class文件加载进来，通过<mark style="background: #FF5582A6;">修改其字节码</mark>生成`子类`来处理，对指定的类生成一个<mark style="background: #FF5582A6;">子类</mark>，覆盖其中的方法，并覆盖其中方法的增强，但是因为采用的是<mark style="background: #FF5582A6;">继承</mark>，所以该类或方法最好不要生成final，对于<mark style="background: #FF5582A6;">final类或方法</mark>，是<mark style="background: #FF5582A6;">无法继承</mark>的

- JDK动态代理：利用拦截器（必须实现InvocationHandler）加上<mark style="background: #FF5582A6;">反射</mark>机制生成一个`代理接口`的匿名类，在调用具体方法前调用InvokeHandler来处理，jdk动态代理只能对实现了<mark style="background: #FF5582A6;">接口</mark>的类生成代理，而不能针对类

## cglib和jdk动态代理使用场景

- 目标对象生成了<mark style="background: #FF5582A6;">接口</mark> 默认用<mark style="background: #FF5582A6;">JDK动态代理</mark>
- 如果目标对象使用了接口，也可以强制使用cglib
- 如果目标对象<mark style="background: #FF5582A6;">没有实现接口</mark>，必须采用<mark style="background: #FF5582A6;">cglib</mark>库，Spring会<mark style="background: #FF5582A6;">自动在JDK动态代理和cglib之间转换</mark>

## cglib比jdk快

- cglib底层是ASM字节码生成框架，但是<mark style="background: #FF5582A6;">字节码技术</mark>生成<mark style="background: #FF5582A6;">代理类</mark>，在JDL1.6之前比使用java反射的效率要高
- 在jdk6之后逐步对JDK动态代理进行了优化，在<mark style="background: #FF5582A6;">调用次数</mark>比较<mark style="background: #FF5582A6;">少</mark>时效率<mark style="background: #FF5582A6;">高于cglib代理效率</mark>
- 只有在<mark style="background: #FF5582A6;">大量调用</mark>的时候<mark style="background: #FF5582A6;">cglib的效率高</mark>，但是在<mark style="background: #FF5582A6;">1.8的时候JDK的效率已高于cglib</mark>
- Cglib不能对声明final的方法进行代理，因为cglib是动态生成代理对象，final关键字修饰的类不可变只能被引用不能被修改

|区别|CGLIB|JDK动态代理|
|---|---|---|
|原理|`动态`生成一个要代理的`子类`，`子类重写`要代理的类的所有不是final的方法。在子类中采用方法拦截技术拦截所有的父类方法的调用，顺势织入横切逻辑，它比Java反射的jdk动态代理要`快`|JDK中的动态代理是通过反射类Proxy以及InvocationHandler回调接口实现的，但是JDK中所有要进行动态代理的类`必须`要实现一个`接口`，也就是说只能对该类所实现接口中定义的方法进行代理，这在实际编程中有一定的局限性，而且使用反射的效率`较慢`|
|是否提供子类代理|是|否|
|是否提供接口代理|是（可不用接口）|是（必须）|


## cglib和jdk动态代理的依赖：
spring-core带有cglib依赖
jdk环境就自带jdk动态代理需要的jar包
所以，使用springboot或spring的时候，不需要引入其他依赖，使用@Aspect等注解的时候，底层还是使用cglib或者jdk动态代理（自动转换）


## Spring AOP和AspectJ

- Spring AOP
    - `Spring AOP是在运行期间通过代理生成目标类，属于动态代理。默认如果使用接口的，用JDK动态代理实现，如果没有接口则使用CGLIB实现`
    - Spring AOP致力于解决企业级开发中最普遍的AOP（方法织入），仅仅是`方法织入`
    - Spring AOP需要`依赖IOC容器`来管理，并且只能作用于Spring容器，使用纯Java代码实现
    - 在性能上，由于Spring AOP是基于动态代理来实现的，在容器启动时需要生成代理实例，在方法调用上也会增加栈的深度，使得Spring AOP的`性能较`AspectJ的`差`
    - Spring AOP`支持注解`，在使用@Aspect注解创建和配置切面时将更加方便。


- AspectJ是什么

AspectJ是一个<mark style="background: #FF5582A6;">java实现</mark>的<mark style="background: #FF5582A6;">AOP框架</mark>，它能够对java代码进行AOP编译（一般在<mark style="background: #FF5582A6;">编译期</mark>进行），让java代码具有AspectJ的AOP功能（当然需要特殊的<mark style="background: #FF5582A6;">编译器</mark>）

可以这样说AspectJ是目前实现AOP框架中<mark style="background: #FF5582A6;">最成熟</mark>，<mark style="background: #FF5582A6;">功能最丰富</mark>的语言，更幸运的是，AspectJ与java程序完全兼容，几乎是无缝关联，因此对于有java编程基础的工程师，上手和使用都非常容易。

AspectJ是在编译期间将切面代码编译到目标代码的，属于静态代理，通过修改代码来实现

AspectJ可以做Spring AOP干不了的事情，它是AOP编程的完全解决方案，AspectJ支持`所有切入点`，不仅仅是方法织入

因为AspectJ在实际运行之前就完成了织入，所以说它生成的类是<mark style="background: #FF5582A6;">没有额外运行时开销</mark>的

需要通过.aj文件来创建切面，并且需要使用ajc（<mark style="background: #FF5582A6;">Aspect编译器</mark>）来编译代码


|Spring AOP|AspectJ|
|---|---|
|在纯 Java 中实现|使用 Java 编程语言的扩展实现|
|不需要单独的编译过程|除非设置 LTW，否则需要 AspectJ 编译器 (ajc)|
|只能使用`运行时`织入|运行时织入不可用。支持`编译时、编译后和加载时`织入|
|功能不强-仅支持`方法级`编织|`更强大` - 可以编织字段、方法、构造函数、静态初始值设定项、最终类/方法等。|
|只能在由 Spring 容器管理的 bean 上实现|可以在所有域对象上实现|
|仅支持`方法`执行切入点|支持`所有切入点`|
|代理是由目标对象创建的, 并且切面应用在这些代理上|在执行应用程序之前 (在运行时) 前, 各方面直接在代码中进行织入|
|比 AspectJ `慢`多了|`更好`的性能|
|易于学习和应用|相对于 Spring AOP 来说更复杂|



- **Spring AOP和AspectJ是什么关系**？

> @Aspect以及增强的几个注解来源于aspectJ，而不是Spring包

1. AspectJ是<mark style="background: #FF5582A6;">更强的AOP框架</mark>，是实际意义的<mark style="background: #FF5582A6;">AOP标准</mark>；
2. Spring为何不写类似AspectJ的框架？ Spring AOP使用纯Java实现, 它不需要专门的编译过程, 它一个**重要的原则就是无侵入性（non-invasiveness）**; Spring 小组完全有能力写类似的框架，只是Spring AOP从来没有打算通过提供一种全面的AOP解决方案来与AspectJ竞争。Spring的开发小组相信无论是基于代理（proxy-based）的框架如Spring AOP或者是成熟的框架如AspectJ都是很有价值的，他们之间应该是**互补而不是竞争的关系**。
3. Spring小组喜欢@AspectJ注解风格更胜于Spring XML配置； 所以**在Spring 2.0使用了和AspectJ 5一样的注解，并使用AspectJ来做切入点解析和匹配**。**但是，AOP在运行时仍旧是纯的Spring AOP，并不依赖于AspectJ的编译器或者织入器（weaver）**。
4. Spring 2.5对AspectJ的支持：在一些环境下，增加了对AspectJ的装载时编织支持，同时提供了一个新的bean切入点。


AspectJ应用到java代码的过程（这个过程称为织入），对于<mark style="background: #FF5582A6;">织入</mark>这个概念，可以简单理解为aspect(切面)应用到目标函数(类)的过程

对于这个过程，一般分为**动态织入**和**静态织入**：
- <mark style="background: #FF5582A6;">动态织入</mark>的方式是在运行时动态将要增强的代码织入到目标类中，这样往往是通过动态代理技术完成的，如Java <mark style="background: #FF5582A6;">JDK的动态代理</mark>(Proxy，底层通过反射实现)或者<mark style="background: #FF5582A6;">CGLIB</mark>的动态代理(底层通过继承实现)，<mark style="background: #FF5582A6;">Spring AOP采用的就是基于运行时增强的代理技术</mark>
- <mark style="background: #FF5582A6;">ApectJ</mark>采用的就是<mark style="background: #FF5582A6;">静态织入</mark>的方式。ApectJ主要采用的是<mark style="background: #FF5582A6;">编译期</mark>织入，在这个期间使用AspectJ的<mark style="background: #FF5582A6;">acj编译器</mark>(类似javac)把aspect类编译成class字节码后，在java目标类编译时织入，即先编译aspect类再编译目标类。
  ![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230914012828.png)

## jdk动态代理，cglib，Spring AOP和Aspectj关系
- Spring AOP和Aspectj是两种实现aop的框架
- Spring AOP采用的是动态代理
    - 动态代理有两种底层技术实现：
        - jdk动态代理（默认有接口的目标类使用jdk动态代理）
        - cglib（没有接口或有接口的目标类使用）
    - Spring AOP采用了Aspectj包提供的注解，但是底层编译器和织入器并不是Aspectj
- Aspectj采用的是静态代理


## 误区

- 曾经以为AspectJ是Spring AOP一部分，是因为Spring AOP使用了AspectJ的注解Aspect来定义切面,使用Pointcut来定义切入点，使用Advice来定义增强处理。
	
- Spring AOP虽然使用了Aspect的Annotation（@Aspect，@Pointcut，@Before等），但是并没有使用它的<mark style="background: #FF5582A6;">编译器</mark>和<mark style="background: #FF5582A6;">织入器</mark>。其实现原理是<mark style="background: #FF5582A6;">JDK动态代理</mark>和<mark style="background: #FF5582A6;">CGLIB</mark>(会自动转换），在运行时生成代理类。



## AOP的实现方式 

在Java平台上，对于AOP的织入，有3种方式：

1. 编译期：在编译时，由编译器把切面调用编译进字节码，这种方式需要定义新的关键字并扩展编译器，AspectJ就扩展了Java编译器，使用关键字aspect来实现织入；
2. 类加载器：在目标类被装载到JVM时，通过一个特殊的类加载器，对目标类的字节码重新“增强”；
3. 运行期动态代理：目标对象和切面都是普通Java类，通过JVM的动态代理功能或者第三方库实现运行期动态织入。(JDK的动态代理、CGLib的动态代理）如SpringAOP、JbossAOP

最简单的方式是第三种，<mark style="background: #FF5582A6;">Spring的AOP实现就是基于JVM的动态代理</mark>。由于<mark style="background: #FF5582A6;">JVM的动态代理要求必须实现接口</mark>，如果一个<mark style="background: #FF5582A6;">普通类</mark>没有业务接口，就需要通过[CGLIB](https://github.com/cglib/cglib)或者[Javassist](https://www.javassist.org/)这些第三方库实现。

<mark style="background: #FF5582A6;">Spring Boot 2之后，默认使用CGLIB代理，不论被代理的类是否实现接口</mark>

AOP技术看上去比较神秘，但实际上，它本质就是一个动态代理，让我们把一些常用功能如权限检查、日志、事务等，从每个业务方法中剥离出来。


## AOP的配置方式
[Spring基础 - Spring核心之面向切面编程(AOP) | Java 全栈知识体系](https://pdai.tech/md/spring/spring-x-framework-aop.html)

Spring AOP 支持对<mark style="background: #FF5582A6;">XML模式</mark>和基于<mark style="background: #FF5582A6;">@AspectJ注解</mark>的两种配置方式

基于XML的声明式AspectJ存在一些不足，需要在Spring配置文件配置大量的代码信息，为了解决这个问题，Spring 使用了@AspectJ框架为AOP的实现提供了一套注解。

|注解名称|解释|
|---|---|
|@Aspect|用来定义一个切面。|
|@pointcut|用于定义切入点表达式。在使用时还需要定义一个包含名字和任意参数的方法签名来表示切入点名称，这个方法签名就是一个返回值为void，且方法体为空的普通方法。|
|@Before|用于定义前置通知，相当于BeforeAdvice。在使用时，通常需要指定一个value属性值，该属性值用于指定一个切入点表达式(可以是已有的切入点，也可以直接定义切入点表达式)。|
|@AfterReturning|用于定义后置通知，相当于AfterReturningAdvice。在使用时可以指定pointcut / value和returning属性，其中pointcut / value这两个属性的作用一样，都用于指定切入点表达式。|
|@Around|用于定义环绕通知，相当于MethodInterceptor。在使用时需要指定一个value属性，该属性用于指定该通知被植入的切入点。|
|@After-Throwing|用于定义异常通知来处理程序中未处理的异常，相当于ThrowAdvice。在使用时可指定pointcut / value和throwing属性。其中pointcut/value用于指定切入点表达式，而throwing属性值用于指定-一个形参名来表示Advice方法中可定义与此同名的形参，该形参可用于访问目标方法抛出的异常。|
|@After|用于定义最终final 通知，不管是否异常，该通知都会执行。使用时需要指定一个value属性，该属性用于指定该通知被植入的切入点。|
|@DeclareParents|用于定义引介通知，相当于IntroductionInterceptor (不要求掌握)。|


Spring AOP的实现方式是动态织入，动态织入的方式是在运行时动态将要增强的代码织入到目标类中，这样往往是通过动态代理技术完成的；**如Java JDK的动态代理(Proxy，底层通过反射实现)或者CGLIB的动态代理(底层通过继承实现)**，Spring AOP采用的就是基于运行时增强的代理技术


## 相关概念
在AOP编程中，我们经常会遇到下面的概念：
- **连接点（Jointpoint）**：表示需要在程序中插入横切关注点的扩展点，**连接点可能是类初始化、方法执行、方法调用、字段调用或处理异常等等**，Spring只支持方法执行连接点，在AOP中表示为**在哪里干**；

- **切入点（Pointcut）**： 选择一组相关连接点的模式，即可以认为连接点的集合，Spring支持perl5正则表达式和AspectJ切入点模式，Spring默认使用AspectJ语法，在AOP中表示为**在哪里干的集合**；

- **通知（Advice）**：在连接点上执行的行为，通知提供了在AOP中需要在切入点所选择的连接点处进行扩展现有行为的手段；包括前置通知（before advice）、后置通知(after advice)、环绕通知（around advice），在Spring中通过代理模式实现AOP，并通过拦截器模式以环绕连接点的拦截器链织入通知；在AOP中表示为**干什么**；

- **方面/切面（Aspect）**：横切关注点的模块化，比如上边提到的日志组件。可以认为是通知、引入和切入点的组合；在Spring中可以使用Schema和<mark style="background: #FF5582A6;">@AspectJ</mark>方式进行组织实现；在AOP中表示为**在哪干和干什么集合**；

- **引入（inter-type declaration）**：也称为内部类型声明，为已有的类添加额外新的字段或方法，Spring允许引入新的接口（必须对应一个实现）到所有被代理对象（目标对象）, 在AOP中表示为**干什么（引入什么）**；

- **目标对象（Target Object）**：需要被织入横切关注点的对象，即该对象是切入点选择的对象，需要被通知的对象，从而也可称为被通知对象；由于Spring AOP 通过代理模式实现，从而这个对象永远是被代理对象，在AOP中表示为**对谁干**；

- **织入（Weaving）**：把切面连接到其它的应用程序类型或者对象上，并创建一个被通知的对象。这些可以在编译时（例如使用AspectJ编译器），类加载时和运行时完成。Spring和其他纯Java AOP框架一样，在运行时完成织入。在AOP中表示为**怎么实现的**；

- **AOP代理（AOP Proxy）**：AOP框架使用代理模式创建的对象，从而实现在连接点处插入通知（即应用切面），就是通过代理来对目标对象应用切面。在Spring中，AOP代理可以用JDK动态代理或CGLIB代理实现，而通过拦截器模型应用切面。在AOP中表示为**怎么实现的一种典型方式**


通知类型：
- **前置通知（Before advice）**：在某连接点之前执行的通知，但这个通知不能阻止连接点之前的执行流程（除非它抛出一个异常）。
- **后置通知（After returning advice）**：在某连接点正常完成后执行的通知：例如，一个方法没有抛出任何异常，正常返回。 
- **异常通知（After throwing advice）**：在方法抛出异常退出时执行的通知。
- **最终通知（After (finally) advice）**：当某连接点退出的时候执行的通知（不论是正常返回还是异常退出）。
- **环绕通知（Around Advice）**：包围一个连接点的通知，如方法调用。这是最强大的一种通知类型。环绕通知可以在方法调用前后完成自定义的行为。它也会选择是否继续执行连接点或直接返回它自己的返回值或抛出异常来结束执行

把这些术语串联到一起，方便理解：

![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230914011002.png)


