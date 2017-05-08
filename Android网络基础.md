# Android网络基础

----
	添加网络权限 <use-permission android:name="android.permission.INTERNET">

## Android提供了多种网络请求的方法，主要是两种图形方式：Http通信和Socket通信

- 基于`TCP/IP`协议的网络通信（对应`IP`,端口号）

  `SeverSocket  ,Socket`,`Socket`是支持`TCP/IP`协议的网络通信基本操作单元，`Socket`本身不算是协议，是操作系统为应用程序提供的一套针对`TCP或UDP`的编程接口`（API）`。

- 使用`URLConnection`访问网络资源（使用URL统一资源定位符）

  `URLConnection`用于与指定站点交换数据

- 使用`HttpURLConnection`访问网络

  `HttpURLConnection`是`URLConnection`的子类，在其基础上做了些改进，增加了一些用于操作Http资源的便捷方法。

- `HttpClient`处理 `Session` , `Cookie`

  `HttpClient` 就是一个增强的`HttpURLConnection`, `HttpClient`是`Apache`公司提供的库。

	在Android 6.0版本中，HttpClient库被移除了，HttpURLConnection是以后唯一的选择了。


## Socket连接和HTTP连接
	由于通常情况下Socket连接就是TCP连接，因此Socket连接一旦建立，通信双方即可开始相互发送数据内容，直到双方连接断开。
	
	而HTTP连接使用的是“请求-响应”的方式，不仅在请求时需要先建立连接，而且需要客户端向服务端发出请求后，服务端才能回复数据。

	有个比较形象的描述：HTTP是轿车，提供了封装或者显示数据的具体形式；而Socket是发动机，提供了网络通信的能力。


## Socket连接和TCP/IP连接
	TCP/IP 只是一个协议栈，就像操作系统的运行机制，必须要具体实现，同时还要提供对外的操作接口。这个就像操作系统会提供标准的
	编程接口，比如 Win 32 编程接口一样，TCP/IP 也要提供可供程序员做网络开发所用的接口，这就是 Socket 编程接口。
	实际上，传输层的TCP是基于网络层的IP协议，而应用层的HTTP	协议又是基于传输层的TCP协议，而Socket本身不算是协议，就是上面
	所说的，它只是提供了一个针对TCP或者UDP编程的接口（API）。
###参考 
###[Android网络通信](http://www.jianshu.com/p/0e5383721145)
###[参考二](http://zhoujianghai.iteye.com/blog/1195988)
###[参考三](http://2277259257.iteye.com/blog/2271518)