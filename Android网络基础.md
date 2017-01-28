# Android网络基础

----

## Android提供了多种网络请求的方法

- 基于TCP协议的网络通信（对应IP,端口）

  `SeverSocket  ,Socket`

- 使用`URLConnection`访问网络资源（使用URL统一资源定位符）

  `URLConnection`用于与指定站点交换数据

- 使用`HttpURLConnectio`访问网络

  `HttpURLConnection`是`URLConnection`的子类，在其基础上做了些改进，增加了一些用于操作Http资源的便捷方法。

- `HttpClient`处理 `Session` , `Cookie`

  `HttpClient` 就是一个增强版的`HttpURLConnection`.

##OkHttp3.0
OkHttpClient client=new OkHttpClient();//创建一个OkHttpClient对象

Request  //请求
Response //任务，将请求封装为任务