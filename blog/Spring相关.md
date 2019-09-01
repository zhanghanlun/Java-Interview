# 1、Spring中的过滤器和拦截器

过滤器：Filter，用来过滤请求传入的内容，对web网站进行压缩，对请求加密和解密。基于函数回调。一个过滤器实例只能在容器初始化中调用一次，修改字符编码，过滤垃圾信息。
拦截器：Interceptor，用来拦截接口请求，对其进行相应的处理，比如登陆验证等等。基于Java反射技术。对COntroller的请求进行拦截。

# 2、Spring AOP

- 横向编程，面向切面编程
- 对一些公共行为进行统一处理，例如日志打印和安全监测。
- 可以作用于方法，提供before、after、after return、around等切入

# 3、Spring IOC

依赖注入，将java对象交给容器管理，在Spring的配置文件中配置Java Bean以及其相关属性，让Spring容器来生成类的实例对象以及管理对象。

# 4、Spring MVC

<img src="https://img-blog.csdnimg.cn/20190901153443835.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3poYW5naGFubHVu,size_16,color_FFFFFF,t_70" width="80%" height="80%">

**实现原理**

1.浏览器发送HTTP请求到DispatcherServlet.
2.DispatcherServlet通过HandlerMapping寻找处理器Controller
3.调用对应的处理器Controller，进行业务请求逻辑处理
4.返回ModelAndView处理结果
5.通过ViewResolver来处理视图
6.返回给浏览器进行渲染视图

# 5、Spring Bean

Spring中的对象实例。
作用域：
- singleton：在Spring IOC容器中仅存一个Bean实例，Bean以单例模式存在
- prototype：每次从容器中调用Bean的时候，返回一个新的实例，即每次调用getBean时，相当于执行 new Bean()
- request：每次HTTP请求都会创建一个新的Bean，该作用域仅适用于WebApplicationContext环境
- session：同一个HTTP Session共享一个Bean，不同Session使用不同Bean，仅适用于WebApplicationContext环境。
