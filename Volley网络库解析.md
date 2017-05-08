##Volley源码解析
###Volly

	Volly是Google官方出的一套小而巧的异步请求库，该框架封装的扩

	展性很强，支持HttpClient,HttpUrlConnection进行网络请求。
	
	Volley的使用场景特点：特别适合数据量小，通信频繁的网络操作。

##Volley重要类：

1.`Volley`:该类主要是用来创建`RequestQueue`类对象并创建网络请求类`HttpStack`的，该类中有四个四个重载方法`newRequestQueue()`方法。

2，`RequestQueue`：请求队列类，类中有多个队列，用来承载不同情况类型的请求,类中还有两个重要调度器线程类对象：`CacheDispatcher,NetworkDispatcher`。

3，`CacheDispatcher`：实际是`Thread`类，用来处理走缓存的请求。

4，`NetworkDispatcher`：实际是`Thread`类，用来处理走网络的请求。

5，`Request`：请求类的抽象基类，子类有`StringRequest，JsonObject Request,JsonArrayRequest`等等，代表不同类型的请求。

5，`Response`：请求的响应类。

6，`Cache`:缓存操作基类接口,`Volley`可以设置是否缓存，设置的缓存是磁盘缓存。

7，`Network`:网络操作基类接口。

8，`HttpStack`:处理网络请求，返回结果。


附上画的`UML`类图：

![Volley UML类图](C:\Users\Mr.Ye\Documents\UMLworkspace\Volley.jpg "")


###[Volley解析一](http://www.jianshu.com/p/5dd50bcbcd6d)

###[Volley源码解析](http://p.codekk.com/blogs/detail/54cfab086c4761e5001b2542)
