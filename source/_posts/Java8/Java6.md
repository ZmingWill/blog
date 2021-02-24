---
title: SpringCloud各层框架注解简述
date: 2020/7/24 20:33:43
layout: JavaSingletenPattern
permalink:  JavaSingletenPattern.html
cover:  http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
单例模式（SingletenPattern）是Java中最简单的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方法，本文我将通过资料以及自己的理解详细梳理对单例模式的运用和理解。
<!--more-->

---
## Springcloud各层框架注解
### 声明Bean的注解:

> - @Component : 组件,没有明确的角色
> - @Service : 在业务逻辑层(service层)使用
> - @Repository : 在数据访问层(dao层)使用.
> - @Controller : 在展现层(MVC--SpringMVC)使用


### 注入Bean的注解:

> - @Autowired : Spring提供的注解.
> - @Inject : JSR-330提供的注解
> - @Resource : JSR-250提供的注解


### 配置文件的注解:

> - @Configuration : 声明当前类是个配置类,相当于一个Spring配置的xml文件.
> - @ComponentScan (cn.test.demo): 自动扫描包名下所有使用
> - @Component @Service  @Repository @Controller 的类,并注册为Bean
> - @WiselyConfiguration : 组合注解 可以替代
> - @Configuration和@ComponentScan
> - @Bean : 注解在方法上,声明当前方法的返回值为一个Bean.
> - @Bean(initMethod="aa",destroyMethod="bb")--> 指定 aa和bb方法在构造之后.Bean销毁之前执行.


### AOP切面编程注解:

> - @Aspect : 声明这是一个切面
> - @After @Before. @Around 定义切面,可以直接将拦截规则(切入点 PointCut)作为参数
> - @PointCut : 专门定义拦截规则 然后在
> - @After @Before. @Around 中调用
> - @Transcational : 事务处理
> - @Cacheable : 数据缓存
> - @EnableAaspectJAutoProxy : 开启Spring 对 这个切面(Aspect )的支持
> - @Target (ElementType.TYPE):元注解,用来指定注解修饰类的那个成员 -->指定拦截规则
> - @Retention(RetentionPolicy.RUNTIME)
--->当定义的注解的@Retention为RUNTIME时，才能够通过运行时的反射机制来处理注解.-->指定拦截规则


### Spring 常用配置:

> - @import :导入配置类
> - @Scope : 新建Bean的实例 > - @Scope("prototype") 声明Scope 为 Prototype
> - @Value : 属性注入
> - @Value ("我爱你")  --> 普通字符串注入
> - @Value ("#{systemProperties['os.name']}") -->注入操作系统属性
> - @Value ("#{ T (java.lang.Math).random()  * 100.0 }") --> 注入表达式结果
> - @Value ("#{demoService.another}") --> 注入其他Bean属性
> - @Value ( "classpath:com/wisely/highlight_spring4/ch2/el/test.txt" ) --> 注入文件资源
> - @Value ("http://www.baidu.com")-->注入网址资源
> - @Value ("${book.name}" ) --> 注入配置文件  注意: 使用的是$ 而不是 #
> - @PostConstruct : 在构造函数执行完之后执行
> - @PreDestroy  : 在 Bean 销毁之前执行
> - ActiveProfiles : 用来声明活动的 profile
> - profile: 为不同环境下使用不同的配置提供了支持
> - @Profile("dev") .......对方法名为 dev-xxxx的方法提供实例化Bean
> - @EnableAsync : 开启异步任务的支持(多线程)
> - @Asyns : 声明这是一个异步任务,可以在类级别 和方法级别声明.
> - @EnableScheduling : 开启对计划任务的支持(定时器)
> - @Scheduled : 声明这是一个计划任务 支持多种计划任务,包含 cron. fixDelay fixRate
> - @Scheduled (dixedDelay = 5000) 通过注解 定时更新
> - @Conditional : 条件注解,根据满足某一特定条件创建一个特定的Bean
> - @ContextConfiguration : 加载配置文件
> - @ContextConfiguration(classes = {TestConfig.class})
> - @ContextConfiguration用来加载ApplicationContext
classes属性用来加载配置类
> - @WebAppCofiguration : 指定加载 ApplicationContext是一个WebApplicationContext
> - @Enable*注解:

> - @EnableAsync : 开启异步任务的支持(多线程)
> - @EnableScheduling : 开启对计划任务的支持(定时器)
> - @EnableWebMVC : 开启对Web MVC 的配置支持
> - @EnableAaspectJAutoProxy : 开启Spring 对 这个切面(Aspect )的支持
> - @EnableConfigurationProperties 开启对@ConfigurationProperties注解配置Bean的支持
> - @EnableJpaRepositories : 开启对Spring Data JAP Repository 的支持
> - @EnableTransactionManagement 开启对注解式事物的支持
> - @EnableCaching开启注解是缓存的支持.
> - @EnableDiscoveryClient 让服务发现服务器,使用服务器.Spring cloud 实现服务发现
> - @EnableEurekaServer 注册服务器 spring cloud 实现服务注册@
> - @EnableScheduling 让spring可以进行任务调度,功能类似于spring.xml文件中的命名空间<task:*>
> - @EnableCaching 开启Cache缓存支持;
SpringMVC 常用注解:

> - @Controller : 注解在类上 声明这个类是springmvc里的Controller,将其声明为一个spring的Bean.
> - @RequestMapping :可以注解在类上和方法上 映射WEB请求(访问路径和参数)
@RequestMapping(value= "/convert",produces+{"application/x-wisely"}) 设置访问URL 返回值类型
>- @ResponseBody : 支持将返回值放入response体内 而不是返回一个页面(返回的是一个组数据)
>- @RequestBody : 允许request的参数在request体中,而不是直接连接在地址后面 次注解放置在参数前
>- @Path Variable : 用来接收路径参数 如/test/001,001为参数,次注解放置在参数前
>- @RestController : @Controller + @ResponseBody 组合注解
>- @ControllerAdvice : 通过@ControllerAdvice可以将对已控制器的全局配置放置在同一个位置
>- @ExceptionHandler : 用于全局处理控制器的异常
>- @ExceptionHandier(value=Exception.class) -->通过value属性可过滤拦截器条件,拦截所有的异常
>- @InitBinder : 用来设置WebDataBinder , WebDataBinder用来自动绑定前台请求参数到Model中.
>- @ModelAttrbuute : 绑定键值对到Model中,
>- @RunWith : 运行器
>- @RunWith(JUnit4.class)就是指用JUnit4来运行
>- @RunWith(SpringJUnit4ClassRunner.class),让测试运行于Spring测试环境
>- @RunWith(Suite.class)的话就是一套测试集合，
>- @WebAppConfiguration("src/main/resources") : 注解在类上,用来声明加载的ApplicationContex 是一个WebApplicationContext ,它的属性指定的是Web资源的位置,默认为 src/main/webapp ,自定义修改为 resource

> - @Before : 在 xxx 前初始化



Spring Boot 注解:

>-  @SpringBootApplication : 是Spring Boot 项目的核心注解 主要目的是开启自动配置 @SpringBootApplication注解是一个组合注解,主要组合了@Configuration .+@EnableAutoConfiguration.+@ComponentScan
> @Value : 属性注入,读取properties或者 Yml 文件中的属性
>- @ConfigurationProperties : 将properties属性和一个Bean及其属性关联,从而实现类型安全的配置 @ConfigurationProperties(prefix = "author",locations = {"classpath:config/author.properties"}) 通过@ConfigurationProperties加载配置,通过prefix属性指定配置前缀,通过location指定配置文件位置
>- @EnableAutoConfiguration 注解:作用在于让 Spring Boot   根据应用所声明的依赖来对 Spring 框架进行自动配置        这个注解告诉Spring Boot根据添加的jar依赖猜测你想如何配置Spring。由于spring-boot-starter-web添加了Tomcat和Spring MVC，所以auto-configuration将假定你正在开发一个web应用并相应地对Spring进行设置。
>- @ Configuration @EnableAutoConfiguration (exclude={xxxx.class}) 禁用特定的自动配置
>- @SpringBootApplication   注解等价于以默认属性使用 @Configuration，@EnableAutoConfiguration和     @ComponentScan。




### @SuppressWarnings注解

> - @SuppressWarnings("unchecked")
告诉编译器忽略 unchecked 警告信息,如使用 list ArrayList等未进行参数化产生的警告信息
> - @SuppressWarnings("serial")
如果编译器出现这样的警告信息: The serializable class WmailCalendar does not declare a static final serialVersionUID field of type long     使用这个注释将警告信息去掉。
> - @SuppressWarnings("deprecation")
如果使用了使用@Deprecated注释的方法，编译器将出现警告信息。使用这个注释将警告信息去掉。
> - @SuppressWarnings("unchecked", "deprecation")
告诉编译器同时忽略unchecked和deprecation的警告信息。
> - @SuppressWarnings(value={"unchecked", "deprecation"})
等同于@SuppressWarnings("unchecked", "deprecation")
### @FeignClient
@FeignClient标签的常用属性如下：
> - name：指定FeignClient的名称，如果项目使用了Ribbon，name属性会作为微服务的名称，用于服务发现
>-  url: url一般用于调试，可以手动指定@FeignClient调用的地址
>- decode404:当发生http 404错误时，如果该字段位true，会调用decoder进行解码，否则抛出FeignException
>- configuration: Feign配置类，可以自定义Feign的Encoder、Decoder、LogLevel、Contract
>- fallback: 定义容错的处理类，当调用远程接口失败或超时时，会调用对应接口的容错逻辑，fallback指定的类必须实现@FeignClient标记的接口
>- fallbackFactory: 工厂类，用于生成fallback类示例，通过这个属性我们可以实现每个接口通用的容错逻辑，减少重复的代码
>- path: 定义当前FeignClient的统一前缀

### @component
把普通pojo实例化到spring容器中，相当于配置文件中的

泛指各种组件，就是说当我们的类不属于各种归类的时候（不属于@Controller、@Services等的时候），我们就可以使用@Component来标注这个类。
