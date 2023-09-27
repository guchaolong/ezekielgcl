

# 组件
## @Component

<mark style="background: #FF5582A6;">泛指组件</mark>，当组件不好归类的时候，我们可以使用这个注解进行标注。

## @Controller

用于标注<mark style="background: #FF5582A6;">控制层</mark>组件(如struts中的action)

## @Service

用于标注<mark style="background: #FF5582A6;">业务层</mark>组件

>@Service注解是标注在<mark style="background: #FF5582A6;">实现类</mark>上的 ,因为@Service是把spring容器中的bean进行<mark style="background: #FF5582A6;">实例化</mark>，也就是等同于<mark style="background: #FF5582A6;">new</mark>操作，只有实现类是可以进行new实例化的，而接口则不能，所以是加在实现类上的

## @Repository

用于标注<mark style="background: #FF5582A6;">数据访问</mark>组件，即DAO组件

> @Service，@Repository不能写在接口上，需要<mark style="background: #FF5582A6;">写在</mark>接口的<mark style="background: #FF5582A6;">实现类</mark>上


# 依赖注入

## @Autowired、@Qualifier

会根据对象的<mark style="background: #FF5582A6;">类型</mark>自动注入依赖对象，默认要求注入对象实例必须存在，可以配置`required=false`来注入不一定存在的对象

@Autowired 和 <mark style="background: #FF5582A6;">@Qualifier</mark> 结合使用时，自动注入的策略就从 byType 转变成 <mark style="background: #FF5582A6;">byName</mark> 了，按照`@Qualifier`指定的`name`进行匹配，如果没有，则按照<mark style="background: #FF5582A6;">变量名</mark>进行匹配，匹配不到，则报错。`@Autowired(required=false)`(默认为`true`)，如果设置`required`为`false`，则注入失败时不会抛出异常

## @Inject、@Named
与@Autowired、@Qualifier差不多，都是根据<mark style="background: #FF5582A6;">类型</mark>，然后<mark style="background: #FF5582A6;">名称</mark>匹配
区别：这两个是 j2EE 的，不是 Spring 的

## @Resource

默认会根据对象的<mark style="background: #FF5582A6;">名称</mark>自动注入依赖对象，如果想要根据<mark style="background: #FF5582A6;">类型</mark>进行注入，可以<mark style="background: #FF5582A6;">设置属性</mark>为`type = UmsAdminService.class`



# bean以及bean的生命周期

## @Bean

@Bean(name="bean的名字",initMethod="初始化时调用方法名字",destroyMethod="close")

定义在方法上，在容器内初始化一个bean实例类。

```java
@Bean(destroyMethod="close")
@ConditionalOnMissingBean
public PersonService registryService() {
		return new PersonService();
	}
```


## @Scope

声明 Spring Bean 的<mark style="background: #FF5582A6;">作用域</mark>，使用方法:
```java
@Bean
@Scope("singleton")
public Person personSingleton() {
    return new Person();
}
```
**四种常见的 Spring Bean 的作用域：**

- singleton : 唯一 bean 实例，Spring 中的 bean 默认都是<mark style="background: #FF5582A6;">单例</mark>的。
- prototype : 每次请求都会创建一个<mark style="background: #FF5582A6;">新的 bean 实例</mark>。
- request : <mark style="background: #FF5582A6;">每一次 HTTP 请求</mark>都会产生一个<mark style="background: #FF5582A6;">新的 bean</mark>，该 bean 仅在当前 HTTP request 内有效。
- session : 同一个<mark style="background: #FF5582A6;">HTTP Session</mark>共享一个Bean，不同Session使用不同的Bean，仅适用于 <mark style="background: #D2B3FFA6;">WebApplicationContext</mark> 环境

## @Primary

当同一个对象有<mark style="background: #FF5582A6;">多个实例</mark>时，<mark style="background: #FF5582A6;">优先选择</mark>该实例

```java
/**
 * @auther macrozheng
 * @description Jackson相关配置，配置json不返回null的字段
 * @date 2018/8/2
 * @github https://github.com/macrozheng
 */
@Configuration
public class JacksonConfig {
    @Bean
    @Primary
    @ConditionalOnMissingBean(ObjectMapper.class)
    public ObjectMapper jacksonObjectMapper(Jackson2ObjectMapperBuilder builder) {
        ObjectMapper objectMapper = builder.createXmlMapper(false).build();
        objectMapper.setSerializationInclusion(JsonInclude.Include.NON_NULL);
        return objectMapper;
    }
}

```

## @PostConstruct

用于<mark style="background: #FF5582A6;">修饰方法</mark>，当对象实例被创建并且依赖注入完成后执行，可用于对象实例的<mark style="background: #FF5582A6;">初始化操作</mark>

spring容器初始化时，要执行该方法

[[Spring知识梳理]] 中 bean 的生命周期部分，bean 初始化阶段会调用

```java
@PostConstruct  
public void init() {   
}   
```


## @PreDestroy

用于修饰方法，当对象实例将被 Spring 容器移除时执行，可用于对象实例持有<mark style="background: #FF5582A6;">资源的释放</mark>


# 配置

## @SpringBootApplication

这个注解是 Spring Boot 项目的<mark style="background: #FF5582A6;">基石</mark>，创建 SpringBoot 项目之后会默认在主类加上,是 <mark style="background: #FF5582A6;">@Configuration、@EnableAutoConfiguration、@ComponentScan</mark> 注解的集合
- `@EnableAutoConfiguration`：启用 SpringBoot 的<mark style="background: #FF5582A6;">自动配置</mark>机制
- `@ComponentScan`： <mark style="background: #FF5582A6;">扫描</mark>指定的包来初始化Spring。
- `@Configuration`：允许在 Spring 上下文中注册额外的 bean 或导入其他<mark style="background: #FF5582A6;">配置类</mark>



@EnableAutoConfiguration,让spring boot根据类路径中的jar包依赖当前项目进行<mark style="background: #FF5582A6;">自动配置</mark>

在src/main/resources的META-INF/spring.factories

```java
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
org.springframework.boot.autoconfigure.admin.SpringApplicationAdminJmxAutoConfiguration,\
org.springframework.boot.autoconfigure.aop.AopAutoConfiguration

若有多个自动配置，用“，”隔开
```


@ComponentScan注解会告知Spring<mark style="background: #FF5582A6;">扫描指定的包</mark>来初始化Spring

```java
@ComponentScan(basePackages = "com.bbs.xx")
```



## @Configuration

一般用来声明<mark style="background: #FF5582A6;">配置类</mark>，可以使用 `@Component`注解替代，不过使用`Configuration`注解声明配置类更加<mark style="background: #FF5582A6;">语义化</mark>

```java
@Configuration("name")//表示这是一个配置信息类,可以给这个配置类也起一个名称
@ComponentScan("spring4")//类似于xml中的<context:component-scan base-package="spring4"/>
public class Config {

    @Autowired//自动注入，如果容器中有多个符合的bean时，需要进一步明确
    @Qualifier("compent")//进一步指明注入bean名称为compent的bean
    private Compent compent;

    @Bean//类似于xml中的<bean id="newbean" class="spring4.Compent"/>
    public Compent newbean(){
        return new Compent();
    }   
}

```


## @Conditional

这个是一个综合的注解，包含了很多子注解。用于表示当某个<mark style="background: #FF5582A6;">条件</mark>满足时，该组件或Bean将被Spring容器创建

**@ConditionalOnBean**：当某个Bean存在时，配置生效
**@ConditionalOnMissingBean**：当某个Bean不存在时，配置生效
**@ConditionalOnClass**：当某个类在Classpath存在时，配置生效
**@ConditionalOnMissingClass**：当某个类在Classpath不存在时，配置生效
**@ConditionalOnExpression**：标注给定的 SpELl 表达式计算结果为 true
**@ConditionalOnJava**：标注 Java 的版本匹配特定值或者一个范围值
**@ConditionalOnJndi**：标注参数中给定的 JNDI 位置必须存在一个，如果没有给参数，则要有 JNDI InitialContext
**@ConditionalOnOnProperty**：标注指定的配置属性要有一个明确的值
**@ConditionalOnResource**：标注 Classpath 里没有指定的资源
**@ConditionalOnWebApplication**：标注这是一个 Web 应用程序
**@ConditionalOnNotWebApplication**：标注这不是一个 Web 应用程序



@ConditionalOnExpression：开关为true的时候才实例化bean

```java
@Configuration
@ConditionalOnExpression("${enabled:false}")
public class BigpipeConfiguration {
    @Bean
    public OrderMessageMonitor orderMessageMonitor(ConfigContext configContext) {
        return new OrderMessageMonitor(configContext);
    }
}
```


@ConditionalOnProperty

这个注解能够控制某个 @Configuration 是否生效。具体操作是通过其两个属性name以及havingValue来实现的，其中name用来从application.properties中读取某个属性值，如果该值为空，则返回false;如果值不为空，则将该值与havingValue指定的值进行比较，如果一样则返回true;否则返回false。如果返回值为false，则该configuration不生效；为true则生效。

```java
@Configuration
//如果synchronize在配置文件中并且值为true
@ConditionalOnProperty(name = "synchronize", havingValue = "true")
public class SecondDatasourceConfig {

    @Bean(name = "SecondDataSource")
    @Qualifier("SecondDataSource")
    @ConfigurationProperties(prefix = "spring.second.datasource")
    public DataSource jwcDataSource() {
        return DataSourceBuilder.create().build();
    }
}
```

@ConditionalOnClass：该注解的参数对应的类必须存在，否则不解析该注解修饰的配置类

```java
@Configuration
@ConditionalOnClass({Gson.class})
public class GsonAutoConfiguration {
    public GsonAutoConfiguration() {
    }

    @Bean
    @ConditionalOnMissingBean
    public Gson gson() {
        return new Gson();
    }
}

```

@ConditionalOnMisssingClass({ApplicationManager.class})：如果存在它修饰的类的bean，则不需要再创建这个bean；

@ConditionOnMissingBean(name = "example")：表示如果name为“example”的bean存在，该注解修饰的代码块不执行。

## @Import(Config1.class)

@Import 注解是用来导入<mark style="background: #FF5582A6;">配置类</mark>或者一些需要<mark style="background: #FF5582A6;">前置加载的类</mark>

```java
@Configuration
public class CDConfig {

    @Bean   // 将SgtPeppers注册为 SpringContext中的bean
    public CompactDisc compactDisc() {
        return new CompactDisc();  // CompactDisc类型的
    }
}

@Configuration
@Import(CDConfig.class)  //导入CDConfig的配置
public class CDPlayerConfig {

    @Bean(name = "cDPlayer")
    public CDPlayer cdPlayer(CompactDisc compactDisc) {  
         // 这里会注入CompactDisc类型的bean
         // 这里注入的这个bean是CDConfig.class中的CompactDisc类型的那个bean
        return new CDPlayer(compactDisc);
    }
}
```


# 读取配置信息

## @Value

application.properties定义属性，直接使用@Value注入即可

```java
public class A{
	 @Value("${push.start:0}")    如果缺失，默认值为0
     private Long  id;
}
```


## @ConfigurationProperties(prefix="xxxxx")

通过`@ConfigurationProperties`读取配置信息并与 bean 绑定。

Spring源码中大量使用了`ConfigurationProperties`注解，比如`server.port`就是由该注解获取到的，通过与其他注解配合使用，能够实现Bean的按需配置。

该注解有一个`prefix`属性，通过指定的<mark style="background: #FF5582A6;">前缀</mark>，<mark style="background: #FF5582A6;">绑定配置文件中的配置</mark>，该注解可以放在<mark style="background: #FF5582A6;">类</mark>上，也可以放在<mark style="background: #FF5582A6;">方法</mark>上,当作用于方法上时，该方法需要有`@Bean`注解且所属Class需要有`@Configuration`注解。

1. 作用于方法上

配置文件：
```
#数据源  
spring.datasource.druid.write.url=jdbc:mysql://localhost:3306/jpa  
spring.datasource.druid.write.username=root  
spring.datasource.druid.write.password=1  
spring.datasource.druid.write.driver-class-name=com.mysql.jdbc.Driver  
  
spring.datasource.druid.read.url=jdbc:mysql://localhost:3306/jpa  
spring.datasource.druid.read.username=root  
spring.datasource.druid.read.password=1  
spring.datasource.druid.read.driver-class-name=com.mysql.jdbc.Driver
```

java代码：需要@Configuration和@Bean
```java
@Configuration
public class DruidDataSourceConfig {
    /**
     * DataSource 配置
     * @return
     */
    @ConfigurationProperties(prefix = "spring.datasource.druid.read")
    @Bean(name = "readDruidDataSource")
    public DataSource readDruidDataSource() {
        return new DruidDataSource();
    }


    /**
     * DataSource 配置
     * @return
     */
    @ConfigurationProperties(prefix = "spring.datasource.druid.write")
    @Bean(name = "writeDruidDataSource")
    @Primary
    public DataSource writeDruidDataSource() {
        return new DruidDataSource();
    }
}
```
`@Value`注解可以通过全限定名进行配置的绑定，这里的`ConfigurationProperties`其实就类似于使用多个`@Value`同时绑定，绑定的对象就是DataSource类型的对象，而且是隐式绑定的，意味着在配置文件编写的时候需要与对应类的字段名称相同，比如上述`spring.datasource.druid.write.url=jdbc:mysql://localhost:3306/jpa`，当然了，你也可以随便写个配置，比如`spring.datasource.druid.write.uuu=www.baidu.com`，此时你只需要在注解中加上以下参数即可
```java
boolean ignoreInvalidFields() default false;
```


2. 作用于类上
配置文件：
```
spring.datasource.url=jdbc:mysql://127.0.0.1:8888/test?useUnicode=false&autoReconnect=true&characterEncoding=utf-8 
spring.datasource.username=root spring.datasource.password=root spring.datasource.driver-class-name=com.mysql.jdbc.Driver spring.datasource.type=com.alibaba.druid.pool.DruidDataSource
```

java代码
```java
@ConfigurationProperties(prefix = "spring.datasource")
@Component
@Getter
@Setter
public class DatasourcePro {

    private String url;

    private String username;

    private String password;

    // 配置文件中是driver-class-name, 转驼峰命名便可以绑定成
    private String driverClassName;

    private String type;
}
```

用法：
```java
@Controller
@RequestMapping(value = "/config")
public class ConfigurationPropertiesController {

    @Autowired
    private DatasourcePro datasourcePro;

    @RequestMapping("/test")
    @ResponseBody
    public Map<String, Object> test(){

        Map<String, Object> map = new HashMap<>();
        map.put("url", datasourcePro.getUrl());
        map.put("userName", datasourcePro.getUsername());
        map.put("password", datasourcePro.getPassword());
        map.put("className", datasourcePro.getDriverClassName());
        map.put("type", datasourcePro.getType());

        return map;
    }
}
```

3. 总结

	1. `@ConfigurationProperties`和`@value` 有着相同的功能，但是`@ConfigurationProperties`的写法更为方便。
	2. `@ConfigurationProperties`的`POJO`类的命名比较严格，因为它必须和`prefix`的后缀名要一致, 不然值会绑定不上, 特殊的后缀名是`“driver-class-name”`这种带横杠的情况，在`POJO`里面的命名规则是下划线转驼峰就可以绑定成功，所以就是 `“driverClassName”`


## @EnableConfigurationProperties

用 @EnableConfigurationProperties注解使 @ConfigurationProperties生效，并从IOC容器中获取bean。


## @ImportResource

用于导入Spring 的<mark style="background: #FF5582A6;">配置文件</mark>。

以前写的 springmvc.xml、applicationContext.xml 在 SpringBoot 里面并没有，我们自己编写的配置文件也不能自动识别，这里就可以使用 @ImportResource 标注在一个配置类上让 Spring 的配置文件生效。

`注意！不使用 @ImportResource 注解，程序根本不能对我们 Spring 的配置文件进行加载`


```java
@ImportResource("classpath*:/spring/*.xml")  单个

@ImportResource({"classpath*:/spring/1.xml","classpath*:/spring/2.xml"})   多个

```


## @PropertySource

<mark style="background: #FF5582A6;">不常用</mark>,`@PropertySource`读取指定 properties 文件

```java
@Component
@PropertySource("classpath:website.properties")

class WebSite {
    @Value("${url}")
    private String url;

  省略getter/setter
  ......
}
```



# HTTP请求

* GET ：请求从服务器<mark style="background: #FF5582A6;">获取</mark>特定资源。举个例子：GET /users（获取所有学生）
* POST ：在服务器上<mark style="background: #FF5582A6;">创建</mark>一个新的资源。举个例子：POST /users（创建学生）
* PUT ：<mark style="background: #FF5582A6;">更新</mark>服务器上的资源（客户端提供更新后的整个资源）。举个例子：PUT /users/12（更新编号为 12 的学生）
* DELETE ：从服务器<mark style="background: #FF5582A6;">删除</mark>特定的资源。举个例子：DELETE /users/12（删除编号为 12 的学生）
* PATCH ：<mark style="background: #FF5582A6;">更新</mark>服务器上的资源（客户端提供更改的属性，可以看做作是部分更新），使用的比较少


## @RestController

`@RestController`注解是`@Controller和`@`ResponseBody`的合集,表示这是个控制器 bean,并且是将函数的返回值<mark style="background: #FF5582A6;">直接填入 HTTP 响应体</mark>中,是 REST 风格的控制器
现在都是前后端分离，说实话我已经很久没有用过`@Controller`

## @RequestMapping("/api2/copper")

用来映射web请求(访问路径和参数)、处理类和方法，可以注解在类或方法上。注解在方法上的路径会继承注解在类上的路径。

produces属性: 定制返回的response的媒体类型和字符集，或需返回值是json对象

```java
@RequestMapping(value="/api2/copper",produces="application/json;charset=UTF-8",method = RequestMethod.POST)
```


## @GetMapping("users") 
等价于@RequestMapping(value="/users",method=RequestMethod.GET)

## @PostMapping("users")
等价于@RequestMapping(value="/users",method=RequestMethod.POST)

## @PutMapping("/users/{userId}") 
等价于@RequestMapping(value="/users/{userId}",method=RequestMethod.PUT)

## @DeleteMapping("/users/{userId}")
等价于@RequestMapping(value="/users/{userId}",method=RequestMethod.DELETE)


# 前后端传值

## @RequestParam和@PathVariable

获取request请求的参数值
@RequestParam注解是Spring MVC框架中的一个注解，用于将<mark style="background: #FF5582A6;">HTTP请求中的参数</mark>绑定到Controller方法的参数上。

```java
 public List<CopperVO> getOpList(HttpServletRequest request,
                                    @RequestParam(value = "pageIndex", required = false) Integer pageIndex,
                                    @RequestParam(value = "pageSize", required = false) Integer pageSize) {
 
  }
```

@PathVariable用来获得请求<mark style="background: #FF5582A6;">url中的动态参数</mark>

```java
@Controller  
public class TestController {  

     @RequestMapping(value="/user/{userId}/roles/{roleId}",method = RequestMethod.GET)  
     public String getLogin(@PathVariable("userId") String userId,  
         @PathVariable("roleId") String roleId){
           
         System.out.println("User Id : " + userId);  
         System.out.println("Role Id : " + roleId);  
         return "hello";  
     
     }  
}
```

同时使用：
```java
@GetMapping("/klasses/{klassId}/teachers")
public List<Teacher> getKlassRelatedTeachers(
         @PathVariable("klassId") Long klassId,
         @RequestParam(value = "type", required = false) String type ) {
...
}
```
如果我们请求的 url 是：`/klasses/{123456}/teachers?type=web`
那么我们服务获取到的数据就是：`klassId=123456,type=web`


## @RequestBody

用于读取 Request 请求（可能是 POST,PUT,DELETE,GET 请求）的 body 部分并且**Content-Type 为 application/json** 格式的数据，接收到数据之后会自动将数据绑定到 Java 对象上去。系统会使用`HttpMessageConverter`或者自定义的`HttpMessageConverter`将请求的 body 中的 json 字符串转换为 java 对象，此外，还可以通过@Valid注解对请求主体中的参数进行校验。

```java
@PostMapping("/sign-up")
public ResponseEntity signUp(@RequestBody @Valid UserRegisterRequest userRegisterRequest) {
  userService.save(userRegisterRequest);
  return ResponseEntity.ok().build();
}
```

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class UserRegisterRequest {
    @NotBlank
    private String userName;
    @NotBlank
    private String password;
    @FullName
    @NotBlank
    private String fullName;
}
```

我们发送 post 请求到这个接口，并且 body 携带 JSON 数据：
```
{"userName":"coder","fullName":"shuangkou","password":"123456"}
```
后端就可以直接把 json 格式的数据映射到我们的 `UserRegisterRequest` 类上

需要注意的是：<mark style="background: #FF5582A6;">一个请求方法只可以有一个@RequestBody，但是可以有多个@RequestParam和@PathVariable</mark>。 如果你的方法必须要用两个 `@RequestBody`来接受数据的话，大概率是你的数据库设计或者系统设计出问题了！


## @ResponseBody

支持将返回值放在<mark style="background: #FF5582A6;">response</mark>体内，而不是返回一个页面。比如Ajax接口，可以用此注解返回数据而<mark style="background: #FF5582A6;">不是页面</mark>。此注解可以放置在返回值前或方法前。

@ResponseBody注解的作用是将controller的方法返回的对象 通过适当的转换器 转换为指定的格式之后，写入到response对象的body区（响应体中），通常用来返回JSON数据或者是XML数据，需要注意的呢，在使用此注解之后<mark style="background: #FF5582A6;">不会再走视图处理器</mark>，而是直接将数据写入到输入流中，它的效果等同于通过response对象输出指定格式的数据。

**这里还要着重强调一下**，要通过@ResponseBody 注解 将返回的json字符串放入响应体中，然后在前台js才能拿到json字符串进行解析，如果不加，响应体中就没有放入json字符串，前台自然是拿不到数据的


# 参数校验
**数据的校验的重要性就不用说了，即使在前端对数据进行校验的情况下，我们还是要对传入后端的数据再进行一遍校验，避免用户绕过浏览器直接通过一些 HTTP 工具直接向后端请求一些违法数据。**

一些常用的字段验证的注解:

- `@NotEmpty` 被注释的字符串的不能为 null 也不能为空
- `@NotBlank` 被注释的字符串非 null，并且必须包含一个非空白字符
- `@Null` 被注释的元素必须为 null
- `@NotNull` 被注释的元素必须不为 null
- `@AssertTrue` 被注释的元素必须为 true
- `@AssertFalse` 被注释的元素必须为 false
- `@Pattern(regex=,flag=)`被注释的元素必须符合指定的正则表达式
- `@Email` 被注释的元素必须是 Email 格式。
- `@Min(value)`被注释的元素必须是一个数字，其值必须大于等于指定的最小值
- `@Max(value)`被注释的元素必须是一个数字，其值必须小于等于指定的最大值
- `@DecimalMin(value)`被注释的元素必须是一个数字，其值必须大于等于指定的最小值
- `@DecimalMax(value)` 被注释的元素必须是一个数字，其值必须小于等于指定的最大值
- `@Size(max=, min=)`被注释的元素的大小必须在指定的范围内
- `@Digits (integer, fraction)`被注释的元素必须是一个数字，其值必须在可接受的范围内
- `@Past`被注释的元素必须是一个过去的日期
- `@Future` 被注释的元素必须是一个将来的日期
- ......

## @Valid 和 @Validated
//todo

# 全局处理 Controller 层异常

1. `@ControllerAdvice` :注解定义全局<mark style="background: #FF5582A6;">异常处理类</mark>
2. `@ExceptionHandler` :注解声明<mark style="background: #FF5582A6;">异常处理方法</mark>

## @ControllerAdvice和@ExceptionHandler


​`​@ControllerAdvice​`​是@Component注解的一个延伸注解，Spring会自动扫描并检测被@ControllerAdvice所标注的类。​`​@ControllerAdvice​`​需要和​`​@ExceptionHandler​`​、​`​@InitBinder​`​以及​`​@ModelAttribute​`​注解搭配使用，主要是用来处理控制器所抛出的异常信息。首先，我们需要定义一个被​`​@ControllerAdvice​`​所标注的类，在该类中，定义一个用于处理具体异常的方法，并使用@ExceptionHandler注解进行标记。此外，在有必要的时候，可以使用​`​@InitBinder​`​在类中进行全局的配置，还可以使用@ModelAttribute配置与视图相关的参数。使用​`​@ControllerAdvice​`​注解，就可以快速的创建统一的，自定义的异常处理类。下面是一个使用​`​@ControllerAdvice​`​的示例代码：
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230918043203.png)


```java
@ControllerAdvice
public class GlobalExceptionHandler {

    @ResponseBody
    @ExceptionHandler(value = ApiException.class)
    public CommonResult handle(ApiException e) {
        if (e.getErrorCode() != null) {
            return CommonResult.failed(e.getErrorCode());
        }
        return CommonResult.failed(e.getMessage());
    }
}
```


# JPA

## @Entity和@Table

@Entity 声明一个类对应一个数据库<mark style="background: #FF5582A6;">实体</mark>。
@Table 设置<mark style="background: #FF5582A6;">表名</mark>
```java
@Entity
@Table(name = "role")
public class Role {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String description;
    省略getter/setter......
}
```


## @Id、@GeneratedValue、@GenericGenerator

`@Id` ：声明一个字段为<mark style="background: #FF5582A6;">主键</mark>。

使用`@Id`声明之后，我们还需要定义<mark style="background: #FF5582A6;">主键的生成策略</mark>。我们可以使用 `@GeneratedValue` 指定主键生成策略。

**1.通过 `@GeneratedValue`直接使用 JPA 内置提供的四种主键生成策略来指定主键生成策略**
```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```

JPA 使用枚举定义了 4 中常见的主键生成策略，如下：
```java
public enum GenerationType {

    /**
     * 使用一个特定的数据库表格来保存主键
     * 持久化引擎通过关系数据库的一张特定的表格来生成主键,
     */
    TABLE,

    /**
     *在某些数据库中,不支持主键自增长,比如Oracle、PostgreSQL其提供了一种叫做"序列(sequence)"的机制生成主键
     */
    SEQUENCE,

    /**
     * 主键自增长
     */
    IDENTITY,

    /**
     *把主键生成策略交给持久化引擎(persistence engine),
     *持久化引擎会根据数据库在以上三种主键生成 策略中选择其中一种
     */
    AUTO
}

```

`@GeneratedValue`注解默认使用的策略是`GenerationType.AUTO`


**2.通过 `@GenericGenerator`声明一个主键策略，然后 `@GeneratedValue`使用这个策略**
```java
@Id
@GeneratedValue(generator = "IdentityIdGenerator")
@GenericGenerator(name = "IdentityIdGenerator", strategy = "identity")
private Long id;
```
等价于
```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```
jpa 提供的主键生成策略有如下几种
```java
public class DefaultIdentifierGeneratorFactory
        implements MutableIdentifierGeneratorFactory, Serializable, ServiceRegistryAwareService {

    @SuppressWarnings("deprecation")
    public DefaultIdentifierGeneratorFactory() {
        register( "uuid2", UUIDGenerator.class );
        register( "guid", GUIDGenerator.class );            // can be done with UUIDGenerator + strategy
        register( "uuid", UUIDHexGenerator.class );            // "deprecated" for new use
        register( "uuid.hex", UUIDHexGenerator.class );     // uuid.hex is deprecated
        register( "assigned", Assigned.class );
        register( "identity", IdentityGenerator.class );
        register( "select", SelectGenerator.class );
        register( "sequence", SequenceStyleGenerator.class );
        register( "seqhilo", SequenceHiLoGenerator.class );
        register( "increment", IncrementGenerator.class );
        register( "foreign", ForeignGenerator.class );
        register( "sequence-identity", SequenceIdentityGenerator.class );
        register( "enhanced-sequence", SequenceStyleGenerator.class );
        register( "enhanced-table", TableGenerator.class );
    }

    public void register(String strategy, Class generatorClass) {
        LOG.debugf( "Registering IdentifierGenerator strategy [%s] -> [%s]", strategy, generatorClass.getName() );
        final Class previous = generatorStrategyToClassNameMap.put( strategy, generatorClass );
        if ( previous != null ) {
            LOG.debugf( "    - overriding [%s]", previous.getName() );
        }
    }

}
```

## @Column

`@Column` <mark style="background: #FF5582A6;">声明字段</mark>

设置属性 userName 对应的<mark style="background: #FF5582A6;">数据库字段名</mark>为 user_name，长度为 32，非空
```java
@Column(name = "user_name", nullable = false, length=32)
private String userName;
```

设置<mark style="background: #FF5582A6;">字段类型</mark>并且加<mark style="background: #FF5582A6;">默认值</mark>，这个还是挺常用的。
```java
@Column(columnDefinition = "tinyint(1) default 1")
private Boolean enabled;
```

## @Transient

`@Transient` ：声明不需要与数据库映射的字段，在保存的时候<mark style="background: #FF5582A6;">不需要保存进数据库</mark> 。

如果我们想让`secrect` 这个字段<mark style="background: #FF5582A6;">不被持久化</mark>，可以使用 `@Transient`关键字声明。

```java
@Entity(name="USER")
public class User {

    ......
    @Transient
    private String secrect; // not persistent because of @Transient

}
```

除了 `@Transient`关键字声明， 还可以采用下面几种方法：

```java
static String secrect; // not persistent because of static
final String secrect = “Satish”; // not persistent because of final
transient String secrect; // not persistent because of transient
```

一般使用注解的方式比较多。


## @Lob

`@Lob`:声明某个字段为<mark style="background: #FF5582A6;">大字段</mark>。

```java
@Lob
//指定 Lob 类型数据的获取策略， FetchType.EAGER 表示非延迟 加载，而 FetchType. LAZY 表示延迟加载 ；
@Basic(fetch = FetchType.EAGER)
//columnDefinition 属性指定数据表对应的 Lob 字段类型
@Column(name = "content", columnDefinition = "LONGTEXT NOT NULL")
private String content;
```

## @Enumerated

可以使用<mark style="background: #FF5582A6;">枚举类型</mark>的<mark style="background: #FF5582A6;">字段</mark>，不过枚举字段要用`@Enumerated`注解修饰。 

```java
public enum Gender {
    MALE("男性"),
    FEMALE("女性");

    private String value;
    Gender(String str){
        value=str;
    }
}
```

```java
@Entity
@Table(name = "role")
public class Role {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String description;
    @Enumerated(EnumType.STRING)
    private Gender gender;
    省略getter/setter......
}
```

数据库里面对应存储的是 MAIL/FEMAIL

## @CreatedDate、@LastModifiedDate、@CreatedBy、@LastModifiedBy、@EnableJpaAuditing

只要继承了 `AbstractAuditBase`的类都会默认加上下面四个字段。

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
@MappedSuperclass
@EntityListeners(value = AuditingEntityListener.class)
public abstract class AbstractAuditBase {

    @CreatedDate
    @Column(updatable = false)
    @JsonIgnore
    private Instant createdAt;

    @LastModifiedDate
    @JsonIgnore
    private Instant updatedAt;

    @CreatedBy
    @Column(updatable = false)
    @JsonIgnore
    private String createdBy;

    @LastModifiedBy
    @JsonIgnore
    private String updatedBy;
}

```

`@CreatedDate`: 表示该字段为创建时间时间字段，在这个实体被 insert 的时候，会设置值
`@CreatedBy` :表示该字段为创建人，在这个实体被 insert 的时候，会设置值
`@LastModifiedDate`、`@LastModifiedBy`同理。

`@EnableJpaAuditing`：开启 JPA 审计功能

## @Modifying

提示 JPA 该操作是修改操作,注意还要配合`@Transactional`注解使用
```java
@Repository
public interface UserRepository extends JpaRepository<User, Integer> {

    @Modifying
    @Transactional(rollbackFor = Exception.class)
    void deleteByUserName(String userName);
}
```

## @OneToOne、@OneToMany、@ManyToOne、@MangToMang
- `@OneToOne` 声明一对一关系
- `@OneToMany` 声明一对多关系
- `@ManyToOne`声明多对一关系
- `@MangToMang`声明多对多关系

# 数据库事务处理 
## @EnableTransactionManagement

启用Spring基于注解的事务管理功能，需要和`@Configuration`注解一起使用

```java
@Configuration
@EnableTransactionManagement
@MapperScan({"com.macro.mall.mapper","com.macro.mall.dao"})
public class MyBatisConfig {
}
```

## @Transactional

在要开启事务的方法上使用`@Transactional`注解即可!

```java
@Transactional(rollbackFor = Exception.class)
public void save() {
  ......
}
```

我们知道 Exception 分为运行时异常 RuntimeException 和非运行时异常。在`@Transactional`注解中如果不配置`rollbackFor`属性,那么事物只会在遇到`RuntimeException`的时候才会回滚,加上`rollbackFor=Exception.class`,可以让事物在遇到非运行时异常时也回滚。

`@Transactional` 注解一般用在可以作用在`类`或者`方法`上。

- **作用于类**：当把`@Transactional 注解放在类上时，表示所有该类的`public 方法都配置相同的事务属性信息。
- **作用于方法**：当类配置了`@Transactional`，方法也配置了`@Transactional`，方法的事务会覆盖类的事务配置信息。

# AOP相关
### @Aspect

用于定义<mark style="background: #FF5582A6;">切面</mark>，切面是<mark style="background: #FF5582A6;">通知</mark>和<mark style="background: #FF5582A6;">切点</mark>的结合，定义了何时、何地应用通知功能。

### @Before

表示<mark style="background: #FF5582A6;">前置通知</mark>（Before），通知方法会在<mark style="background: #FF5582A6;">目标方法调用之前</mark>执行，通知描述了切面要完成的工作以及何时执行。

### @After

表示<mark style="background: #FF5582A6;">后置通知</mark>（After），通知方法会在<mark style="background: #FF5582A6;">目标方法返回</mark>或<mark style="background: #FF5582A6;">抛出异常</mark>后执行。

### @AfterReturning

表示<mark style="background: #FF5582A6;">返回通知</mark>（AfterReturning），通知方法会在<mark style="background: #FF5582A6;">目标方法返回</mark>后执行。

### @AfterThrowing

表示<mark style="background: #FF5582A6;">异常通知</mark>（AfterThrowing），通知方法会在<mark style="background: #FF5582A6;">目标方法返回</mark>后执行。

### @Around

表示<mark style="background: #FF5582A6;">环绕通知</mark>（Around），通知方法会<mark style="background: #FF5582A6;">将目标方法封装起来</mark>，在目标方法<mark style="background: #FF5582A6;">调用之前和之后执行自定义</mark>的行为。

### @Pointcut

定义<mark style="background: #FF5582A6;">切点</mark>表达式，定义了通知功能被应用的<mark style="background: #FF5582A6;">范围</mark>。

### @Order

用于定义组件的执行<mark style="background: #FF5582A6;">顺序</mark>，在AOP中指的是<mark style="background: #FF5582A6;">切面的执行顺序</mark>，value属性越低优先级越高

```java
/**
 * @description 统一日志处理切面
 */
@Aspect
@Component
@Order(1)
public class WebLogAspect {
    private static final Logger LOGGER = LoggerFactory.getLogger(WebLogAspect.class);

    @Pointcut("execution(public * com.macro.mall.tiny.controller.*.*(..))")
    public void webLog() {
    }

    @Before("webLog()")
    public void doBefore(JoinPoint joinPoint) throws Throwable {
    }

    @AfterReturning(value = "webLog()", returning = "ret")
    public void doAfterReturning(Object ret) throws Throwable {
    }

    @Around("webLog()")
    public Object doAround(ProceedingJoinPoint joinPoint) throws Throwable {
        WebLog webLog = new WebLog();
        //省略日志处理操作...
        Object result = joinPoint.proceed();
        LOGGER.info("{}", JSONUtil.parse(webLog));
        return result;
    }
    
}
```

# json 数据处理

## @JsonIgnoreProperties、@JsonIgnore

**`@JsonIgnoreProperties` 作用在类上用于过滤掉特定字段不返回或者不解析。**
```java
//生成json时将userRoles属性过滤
@JsonIgnoreProperties({"userRoles"})
public class User {

    private String userName;
    private String fullName;
    private String password;
    @JsonIgnore
    private List<UserRole> userRoles = new ArrayList<>();
}
```

**`@JsonIgnore`一般用于类的属性上，作用和上面的`@JsonIgnoreProperties` 一样。**
```java
public class User {

    private String userName;
    private String fullName;
    private String password;
   //生成json时将userRoles属性过滤
    @JsonIgnore
    private List<UserRole> userRoles = new ArrayList<>();
}
```


## @JsonFormat

格式化 json 数据

```java
@JsonFormat(shape=JsonFormat.Shape.STRING, pattern="yyyy-MM-dd'T'HH:mm:ss.SSS'Z'", timezone="GMT")
private Date date;
```

## @JsonUnwrapped

扁平化对象

```java
@Getter
@Setter
@ToString
public class Account {
    private Location location;
    private PersonInfo personInfo;

  @Getter
  @Setter
  @ToString
  public static class Location {
     private String provinceName;
     private String countyName;
  }
  @Getter
  @Setter
  @ToString
  public static class PersonInfo {
    private String userName;
    private String fullName;
  }
}

```

未扁平化之前：

```json
{
    "location": {
        "provinceName":"湖北",
        "countyName":"武汉"
    },
    "personInfo": {
        "userName": "coder1234",
        "fullName": "shaungkou"
    }
}
```

使用`@JsonUnwrapped` 扁平对象之后：

```java
@Getter
@Setter
@ToString
public class Account {
    @JsonUnwrapped
    private Location location;
    @JsonUnwrapped
    private PersonInfo personInfo;
    ......
}
```

```json
{
  "provinceName":"湖北",
  "countyName":"武汉",
  "userName": "coder1234",
  "fullName": "shaungkou"
}
```

# 测试

## @ActiveProfiles

**`@ActiveProfiles`一般作用于测试类上， 用于声明生效的 Spring 配置文件。**
```java
@SpringBootTest(webEnvironment = RANDOM_PORT)
@ActiveProfiles("test")
@Slf4j
public abstract class TestBase {
  ......
}
```

## @Test
声明一个方法为测试方法

## @Transactional
被声明的测试方法的数据会回滚，避免污染测试数据

## @WithMockUser
**Spring Security 提供的，用来模拟一个真实用户，并且可以赋予权限**

```java
    @Test
    @Transactional
    @WithMockUser(username = "user-id-18163138155", authorities = "ROLE_TEACHER")
    void should_import_student_success() throws Exception {
        ......
    }
```


# 其他

## @EnableZuulProxy

路由网关的主要目的是为了让所有的微服务对外只有一个接口，我们只需访问一个网关地址，即可由网关将所有的请求代理到不同的服务中。Spring Cloud是通过Zuul来实现的，支持自动路由映射到在Eureka Server上注册的服务。Spring Cloud提供了注解@EnableZuulProxy来启用路由代理。





