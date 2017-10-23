# `OkHttp3`	
	An HTTP &HTTP/2 client for Android and Java application.(HTTP网络框架)
	compile 'com.squareup.okhttp3:okhttp:3.6.0'当前最新版本
	OkHttp的最底层是使用Socket,而不是URLConnection,它通过Platform的Class.forName()反射获得当前Runtime使用的Socket库。

	OkHttp3使用场景特点：数据量大，网络请求频繁等。

## `OkHttp`中的重要类：
1，`OkHttpClient:OkHttp`请求客户端，`Builder`模式实现

2，`Dispatcher:`本质是异步请求的调度器，负责调度异步请求的执行，控制最大请求并发数和单个主机的最大并发数，并持有有一个线程池负责执行异步请求，对同步请求只是作统计操作。

3，`Request：`封装网络请求，就是构建请求参数（如url，header,请求方式，请求参数），`Builder`模式实现

4，`Response`：网络请求对应的响应，`Builder`模式实现，真正的`Response`是通过`RealCall.getResponseWithInterceptorChain()`方法获取的。

5，`Call`：是根据Request生成的一个具体的请求实例，且一个`Call`只能被执行一次。

6，`ConnectionPool：Socket`连接池

7，`Interceptor`：`Interceptor`可以说是`OkHttp`的核心功能，它就是通过`Interceptor`来完成监控管理，重写和重试请求的。

8，`Cache:`可以自定义是否采用缓存，缓存形式是磁盘缓存，`DiskLruCache`。

	不管是同步请求还是异步请求，都是通过RealCall.getResponseWithInterceptorChain()方法获取请求结

	果的，只不过在前者在主线程中执行，而后者在线程池中的线程中执行的。


### 思想记录：
	OkHttp3，网络请求库，同步请求RealCall.execute()和异步请求RealCall.enqueue(),请求任务都是交给Dispatcher调度请求任务的处理，请求通过一条拦截链，每一个拦截器处理一部分工作，最后一个拦截器，完成获取请求任务的响应，会将响应沿着拦截链向上传递。


### OkHttp3的缓存设置
[Retrofit2\.0\+okhttp3缓存机制以及遇到的问题 \- Picasso\_L的专栏 \- CSDN博客](http://blog.csdn.net/picasso_l/article/details/50579884)



#### [OkHttp源码解析](http://www.dieyidezui.com/okhttp-3-4-x-yuan-ma-pou-xi/)

#### [根据Interceptor分析OKHttp](https://www.zybuluo.com/Warning1943/note/699633)

#### [OkHttp 3.7源码分析-云栖社区](https://m.aliyun.com/yunqi/articles/78105?spm=5176.100239.0.0.9MCZtW)

#### [深入浅出OkHttp源码](https://www.diycode.cc/topics/640)