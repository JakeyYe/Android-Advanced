
# Retrofit2.0
 `A type-safe HTTP client for Android and Java`
  Android和Java的类型安全HTTP客户端

 	Retrofit 是 Square 公司出品的默认基于 OkHttp 封装的一套 RESTful url格式的网络请求框架,Retrofit 的封装可以说是很强
	大，里面涉及到一堆的设计模式，你可以通过注解直接配置请求，你可以使用不同的 http 客户端，虽然默认是用 http ，可以使用不
	同 Json Converter 来序列化数据，同时提供对 RxJava 的支持，使用 Retrofit + OkHttp + RxJava + Dagger2 可以说是目前比
	较潮的一套框架，但是需要有比较高的门槛。 

  
	Retrofit就是对OkHttp做了一层封装， 把网络请求都交给了OkHttp ，我们只需要通过简单配置就能使用Retrofit来进行网络请
	求。所以使用Retrofit时不仅要导入Retrofit的库，也要导入OKHttp3和Okio的库，也就是要同时导入三个库。

   	Retrofit提供的请求方式注解有@GET和@POST,参数注解有@PATH和@Query等。

	
###Retrofit使用的最核心的两个技术：动态代理和反射。其实Retrofit无非就是让用户创建接口，然后使用自己指定的规则进行网络访问，把接口传入Retrofit，接口上附着的规则由Retrofit进行层层解析后，再进行实际的网络调用。


###向服务器请求数据分为三步：
- 构建请求
- 执行请求
- 解析请求响应并返回到指定位置

###而Retrofit实现网络请求也是三步：
- 通过注解配置API参数
- `CallAdapter` (执行请求并管理)
- `Converter` (解析数据并转换为 `T` )

###Retrofit的使用三步：
	1，创建Retrofit实例
	2，接口定义
	3，接口调用


Retrofit通过`.client()`可以设置不同的底层网络库,默认是使用OkHttp网络库的。
Retrofit+RxJava使用方式
`compile 'com.squareup.retrofit2:adapter-rxjava:2.0.2'`该库是为了让`Retrofit`对`RxJava`的支持。

Retrofit+OkHttp3进行网络请求

  参考

[官方文档](http://square.github.io/retrofit/)

[Retrofit详细介绍](http://www.jianshu.com/p/308f3c54abdd)

[Retrofit和RxJava的一起使用](http://www.devwiki.net/2016/03/25/Retrofit-Use-Course-3/)
​	
##补充
###RESTful
	REST（Resources Representational State Transfer）资源表现层转化


###Volley,Retrofit与OkHttp的区别
	Volley,Retrofit是帮你封装了具体的请求，线程切换以及数据转换，而OkHttp是基于HTTP协议封装的一套请求客户端，虽然它也可
	以开线程，但根本上它更偏向于真正的网络请求，跟HttpClient,HttpUrlConnection的职责是一样的。
	
###应用程序通过 `Retorfit`请求网络，实际上是使用`Retrofit`接口层封装请求参数，`Header，Url`等信息，之后由 `OkHttp` 完成后续的请求操作，在服务端返回数据之后， `OkHttp` 将原始的结果交给 `Retrofit` ，后者根据用户的需求对结果进行解析。