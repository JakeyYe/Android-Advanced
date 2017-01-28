
# Retrofit2.0
 `A type-safe HTTP client for Android and Java`
  Android和Java的类型安全HTTP客户端

 Retrofit 是 Square 公司出品的默认基于 OkHttp 封装的一套 RESTful 网络请求框架,Retrofit 的封装可以说是很强大，里面涉及到一堆的设计模式，你可以通过注解直接配置请求，你可以使用不同的 http 客户端，虽然默认是用 http ，可以使用不同 Json Converter 来序列化数据，同时提供对 RxJava 的支持，使用 Retrofit + OkHttp + RxJava + Dagger2 可以说是目前比较潮的一套框架，但是需要有比较高的门槛。 
 
  Retrofit就是对OkHttp做了一层封装， 把网络请求都交给了OkHttp ，我们只需要通过简单配置就能使用Retrofit来进行网络请求。

   Retrofit提供的请求方式注解有@GET和@POST,参数注解有@PATH和@Query等

###Retrofit的使用三步：
	1，创建Retrofit实例
	2，接口定义
	3，接口调用


Retrofit通过`.client()`可以设置不同的底层网络库,默认是使用Http的。
Retrofit+RxJava使用方式

Retrofit+OkHttp3进行网络请求
  参考

	官方文档`http://square.github.io/retrofit/`

	详细介绍
	http://www.jianshu.com/p/308f3c54abdd

	https://github.com/hehonghui/android-tech-frontier/tree/master/issue-7/Retrofit%E5%BC%80%E5%8F%91%E6%8C%87%E5%8D%97

	Retrofit和RxJava的一起使用  http://www.devwiki.net/2016/03/25/Retrofit-Use-Course-3/
	
	https://www.zybuluo.com/xujun94/note/479910

	http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0915/3460.html


	http://www.tuicool.com/articles/NnuIva

	http://www.jianshu.com/p/a3ddd6401ecb