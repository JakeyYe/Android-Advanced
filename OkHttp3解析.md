#`OkHttp3`	
	An HTTP &HTTP/2 client for Android and Java application.(HTTP网络框架)
	compile 'com.squareup.okhttp3:okhttp:3.6.0'当前最新版本
	OkHttp的最底层是使用Socket,而不是URLConnection,它通过Platform的Class.forName()反射获得当前Runtime使用的Socket库。

	OkHttp3使用场景特点：数据量大，网络请求频繁等。

##`OkHttp`中的重要类：
1，`OkHttpClient:OkHttp`请求客户端，`Builder`模式实现

2，`Dispatcher:`本质是异步请求的调度器，负责调度异步请求的执行，控制最大请求并发数和单个主机的最大并发数，并持有有一个线程池负责执行异步请求，对同步请求只是作统计操作。

3，`Request：`网络请求，`Builder`模式实现

4，`Response`：网络请求对应的响应，`Builder`模式实现，真正的`Response`是通过`RealCall.getResponseWithInterceptorChain()`方法获取的。

5，`ConnectionPool：Socket`连接池

6，`Interceptor`：`Interceptor`可以说是`OkHttp`的核心功能，它就是通过`Interceptor`来完成监控管理，重写和重试请求的。

7，`Cache:`可以自定义是否采用缓存，缓存形式是磁盘缓存，`DiskLruCache`。

	不管是同步请求还是异步请求，都是通过RealCall.getResponseWithInterceptorChain()方法获取请求结

	果的，只不过在前者在主线程中执行，而后者在线程池中的线程中执行的。

###[OkHttp源码解析](http://www.dieyidezui.com/okhttp-3-4-x-yuan-ma-pou-xi/)

###[根据Interceptor分析OKHttp](https://www.zybuluo.com/Warning1943/note/699633)

###[OkHttp3源码分析](http://www.jianshu.com/p/aad5aacd79bf)