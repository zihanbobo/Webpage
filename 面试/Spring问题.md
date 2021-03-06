###1、Spring中AOP的应用场景、Aop原理、好处?
Aop-Aspect Oriented Programming面向切片编程:用来封装**横切关注点**，具体可以在下面的场景中使用:
Authentication权限、Caching缓存、Context passing内容传递、Error handling错误处理、Lazy loading懒加载、Debugging调优、logging、tracing、profiling and monitoring记录跟踪优化校准、Performance optimization 性能优化、Persistence持久化、Resource pooling资源池、Synchronization同步、Transactions事务。
*权限、缓存、内容、错误、懒、调试、日志、跟踪、性能、持久、资源、同步、事务*
*日志内容里有很多错误，因为权限懒得调试，资源无法同步跟踪缓存，影响事务性能*
原理:Aop是面向切面编程，是通过动态代理的方式为程序添加统一功能，集中解决一些公共问题。
优点：1、各个步骤之间的**良好隔离性耦合性**大大降低
     2、源代码无关性，再扩展功能的同时不对源码进行修改操作
*解耦的同时不对源码进行修改*
#2、Spring中ioc的作用与原理？对象创建的过程。
IOC--Inversion of Control控制反转。**某个角色需要另外一个角色协助的时候，在传统的程序设计过程中，通常由调用者来创建被调用者的实例对象。但在Spring中创建被调用者的工作不再由调用者来完成，因此称为控制反转。创建被调用者的工作由Spring来完成，然后注入调用者直接使用**。
*我本来需要请人帮忙，Spring主动帮我找来*
#3、介绍Spring框架
它是一个一站式(full-stack)全栈式框架，提供了**从表现层-springMVC业务层-spring再到持久层-springdata**的一套完整的解决方案。我们在项目中可以只使用spring的一个框架，它就可以提供表现层的mvc框架，持久层的Dao框架。它的两大核心Ioc和AOP更是为我们*程序解耦和代码简洁易维护*提供了支持。
*表现业务很持久的样子*
#4、Spring常见创建对象的注解
@Cmponent@Controller@Service@Repository
*组件、控制器服务仓库*
#5、Spring中用到的设计模式
答：简单工厂、工厂方法、单例模式、适配器、包装器、代理、观察者、策略、模板方法
*骑着单车带包碱观摩工厂*
#6、Spring的优点
答：1、降低了组件之间的耦合性，实现了软件各层之间的**解耦**
2、可以使用容易提供的**众多服务**，如事务管理、消息服务
3、容器提供**单例模式**支持
4、容器提供了AOP技术，利用它很容易实现如**权限拦截，运行期监控**等功能
5、容器提供了**众多的辅助类，能加快应用的开发**
6、spring对于主流的**应用框架**提供了集成支持，如hibernate、JPA、Sruts等。
7、spring属于**低侵入式设计**，代码的污染极低
8、**独立于各种应用服务器**
9、spring的DI机制降低了**业务对象替换的复杂性**
10、spring的**高度开放性**，并不强制应用完全依赖于Spring，**开发者可以自由选择spring的部分或全部**
*单、独、开放、应用框架、辅助、低侵入、替换复杂性、解耦、服务、功能*
**应用单独开放服务，辅助功能替换复杂性解耦低侵入**
#7、SpringBean的作用域之间有什么区别
Spring容器中的bean可以分为5 个范围。所有范围的名称都是自说明的，但是为了避免混淆，不是让我们解释一下：
singleton:这种bean范围是默认的，这种范围确保不管接受到多少个请求，每个容器只有一个bean实例，单例的模式由bean factory自身来维护。
prototype:原形范围与单例范围相反，为每一个bean请求提供一个实例。
request:在请求bean范围内会每一个来自客户端的网络请求创建一个实例，在请求完成以后，bean会失效并被垃圾回收器回收。
Session:与请求范围类似，确保每个sesion中有一个bean的实例，在session过期后，bean会随之失效。
global-session:global-session和portlet应用相关。当你的应用部署在portlet容器中工作时，它包含很多portlet。如果你想要声明让所有的Portlet共用全局的存储变量的话，那么这全局变量需要存储在global-session中。
全局作用域与Sevlet中的session作用域效果相同

#8、Spring管理事务有几种方式?
答:有两种方式
1、**编程式**事务，在代码中硬编码（不推荐使用）
2、**声明式**事务，在配置文件中配置(推荐使用）
声明式事务又分为两种:
a、基于**XML的声明式事务**
b、基于**注解的声明式事务**
**编程、声明、XML、注解**
#9、spring中自动装配的方式有哪些？
1、**No**:即不启用自动装配
2、**byName**:通过属性的名字的方式查找的JavaBean的依赖的对象并为其注入。比如说类Computer有个属性printer，指定其autowire属性为byName后，SpringIoc容器会在配置文件中查找id/name属性为printer的bean，然后使用Setter方法为其注入。
3、**byType**:通过属性的类型查找JavaBean依赖的对象并为其注入。比如类Computer有个属性printer，类型为Printer，那么，指定其autowire属性为byType后，SpringIOC容器会查找Class属性为Printer的bean，使用Setter方法为其注入。
4、**constructor**:通过byType一样，也是通过类型查找依赖对象。与byType的区别在于 它不是使用Setter方法注入，而是使用构造子注入。
5、**autodetect**:在byType和constructor之间自动的选择注入方式。
6、**default**:由上级标签<beans>的default-autowire属性确定。
**N,b,b,c,a,d**
#10、spring中的核心类有哪些，各有什么作用。
答:BeanFactory:产生一个新的实例，可以实现单例模式
BeanWrapper:提供统一的get及set方法
ApplicationContext:提供框架实现，包括BeanFactory的所有功能
**BBAC**
#11、Bean的调用方式有哪些
答:有三种方式可以得到Bean并进行调用:
1、使用BeanWrapper
2、使用BeanFactory
3、使用ApplicationContext
  
#12、什么是IOC，什么又是DI，他们有什么区别?
依赖注入是一个**程序设计模式和架构模型，一些时候也称作控制反转，尽管在技术上来讲，依赖注入是一个IOC的特殊实现，依赖注入是指一个对象应用另外一个对象来提供一个特殊的能力，例如：把一个数据库连接以参数的形式传到一个对象的结构方法里面而不是在那个对象内部自行创建一个连接。控制舞者 依赖注入的基本思想就是把类的依赖从类内部转化到外部以减少依赖**
应用控制反转，对象在被创建的时候，由一个调控系统内所有对象的外界实体，将其所依赖的对象的引用，传递给它，依赖被注入到对象中，所以，控制反转是，关于一个对象如何获取他所依赖的对象的引用，这个责任的反转。

#13、Spring有两种代理方式：
若目标对象实现了若干个接口，Spring使用JDK的java.lang.reflect.Proxy类代理。
优点：因为有接口，所以使系统更加松耦合。
缺点：为每一个目标类创建接口
若目标对象没有实现任何接口，spring使用的CGLIB库生成目标对象的子类。
优点：因为代理类与目标类是继承关系，所以不需要有接口的存在 。
缺点：因为没有使用接口，所以系统的耦合性没有JDK的动态代理好。
**接口,CGLIB**
#14、SpringMVC的流程
1、用户发送请求至**前端控制器DispatcherServlet**
2、DispatcherServlet收到请求调用**HandlerMapping处理器映射器**
3、**处理器映射器根据请求url找到具体的处理器，生成处理器对象及处理器拦截器**（如果有则生成）一并返回给DispatcherServerlet。
4、Dispatcher**Servlet通过**HandlerAdapter处理器适配器**调用处理器
5、**执行处理器(controller，也叫后端控制器）**
6、Controller执行完成返回**ModelAndView****
7、HandlerAdapter将controller**执行结果ModelAndView返回给DispatcherServlet**
8、DispatcherSe**rver将ModelAndView传给ViewReslover视图解析器**
9、ViewResolve**解析后返回具体View**
10、DispatcherServlet对view进行**渲染视图**（即将模型数据填充至视图中）
11、**DispatcherServlet响应用户**

#15、SpringMVC优点


Dubbo支持哪些协议，每种协议的应用场景，优缺点?
dubbo：单一长连接和NIO异步讯，适合大并发小数据量的服务调用，以及消费者远大于提供者，传输协议TCP、异步，Hessian序列化。
rmi:采用JDK标准的rmi协议实现，传输参数和返回参数对象需要实现Serializable接口，使用java标准序列化机制，使用阻塞式短连接，传输数据包大小混合，消费者和提供者个数差不多，可传文件，传输协议TCP。多个短连接，TCP协议传输，同步传输，适用常规的远程服务调用和rmi互操作。在依赖低版本的Common-Collections包，java序列化存在安全漏洞。
webService:基于WebService的远程调用协议，集成CXF实现，提供和原WebService的互操作。多个短连接，基于HTTP传输，同步传输，适用系统集成和跨语言调用：
http:基于Http表彰提供的远程调用协议，使用Spring的HttpInvoke实现，多个短连接，传输协议HTTP，传入参数大小混合，提供者个数大于消费者，需要给应用程序和浏览器JS调用；
hessian:集成Hessian服务，基于HTTP通讯，采用Servlet显露服务，Dubbo内嵌Jetty作为服务器时默认实现，提供与Hession服务互操作。多个短连接，同步Http传输，Hession序列化，传入参数较大，提供者大于消费者，提供者压力较大，可传文件
memcache:基于meecached实现的RPC协议
redis:基于redis实现的rpc协议

#2、Dubbo超时时间怎样设置？
Dubbo超时时间设置有两种方式：
服务提供者端设置超时时间，在Dubbo的用户文档中，推荐如果能在服务端多配置就尽量多配置，因为服务提供者比消费者更清楚自己提供的服务特性。服务消费者设置超时时间，如果在消费者端设置了超时时间，以消费者端为主，即优先级更高。因为服务调用方设置超时时间控制性更灵活。如果消费方超时，服务端线程不会定制，会产生警告。

#3、Dubbo有哪些注册中心?
Multicast注册中心:Multicast注册中心不需要任何中心节点，只要广播地址，就能进行服务注册和发现。基于网络中组播传输实现：
Zookeeper注册中心:基于分布式协调系统Zookeeper实现，采用Zookepper的watch机制实现数据变更；
redis注册中心：基于redis实现，采用key/Map存储，在key存储服务名和类型，Map中key存储服务URL，value服务过期时间。基于redis的发布/订阅模式通知数据变更：
Simple注册中心

#4、Dubbo集群的负载均衡有哪些策略
Dubbo提供了常见的集群策略的实现，并预扩展点予以自行实现。
1、它基于组件技术的，全部的应用对象，无论控制器和视图，还是业务对象之类的都是java组件，并且和Spring提供的其他基础结构紧密集成。
2、不依赖于ServletAPI
3、可以任意使用各种视图技术，而不仅仅局限于JSP
4、支持各种请求资源的映射策略
5、它应是易于扩展的。

#注解
SpringMVC中有一个Servlet，是通过它来将前端原请求分控制器的，这个Servlet的名字DispatcherServlet
声明控制器的注解是@Controller
**控制器类中有一个成员变量，已经在spring配置文件中声明，要将这个成员变量注很高的注解是@autowire**
**将一个请求url指向一个类的方法的注解是@RequestMapping**
**将前台的form中input控件的name属性绑定到控制器类中的方法参数的注解是@RequestParam**
**通常用来将登录用户设置为session对象的注解是@SesssionAttribute**
**ModelAndView类中的addObject方法和Model类中的addAttribute()方法相当于执行了(request)对象中的setAttribute方法**
