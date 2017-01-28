#关于Android项目要了解的库（一）
---

*放在这两个标准资源库的Jcenter和Maven Central的library，可以直接取这两个资源库的网站查找library的最新版本。http://www.jianshu.com/p/3c63ae866e52*

###RxJava函数响应式编程
####RxAndroid是RxJava的增强版，是针对Android专门设计的。

	实现异步操作的库，RxJava - 用于构成使用Java VM的观察序列异步和基于事件的程序库 - 为JVM反应扩展。
	RxJava最核心的两个东西是Observables(被观察者，事件源)和Subscribers(观察者)。Observables发出一系列事件，Subscribers处理这些事件。

RxJava四个基本概念：

`Observable`:可观察者，即被观察者

`Observer`:观察者

`Subscriber` :`RxJava`内置的一个实现了`Observer`的抽象类，`Subscriber`对`Observer`接口接口进行了一些扩展，但它们的基本使用方式是一样的

`subscribe`订阅方法 ，`Observable`和`Observer`通过该方法实现订阅关系,从而`Observable`可以在需要的时候发出事件来通知`Observer`。
`Scheduler`调度器，线程控制器，`RxJava`通过它来指定每一段代码应该运行在什么样的线程里。`RxJava`内置了几个`Scheduler`。通过设置调度器`subscribeOn(Scheduler.io())` 和 `observeOn(AndroidSchedulers.mainThread())` 实现 “后台线程取数据，主线程显示”的程序策略。
 
*响应式代码的基本组成部分是Observable和Subscriber(事实上Observer才是最小的构建快，在实践中使用最多的是Subscriber),Observable发送消息，Subscribers用于消费消息。*

####RxJava内置Scheduler，使用Scheduler管理线程
- Schedulers.immediate(): 直接在当前线程运行，相当于不指定线程。这是默认的 Scheduler。
- Schedulers.newThread(): 总是启用新线程，并在新线程执行操作。
Schedulers.io(): I/O 操作（读写文件、读写数据库、网络信息交互等）所使用的 Scheduler。行为模式和 newThread() 差不多，区别在于 io() 的内部实现是是用一个无数量上限的线程池，可以重用空闲的线程，因此多数情况下 io() 比 newThread() 更有效率。不要把计算工作放在 io() 中，可以避免创建不必要的线程。
- Schedulers.computation(): 计算所使用的 Scheduler。这个计算指的是 CPU 密集型计算，即不会被 I/O 等操作限制性能的操作，例如图形的计算。这个 Scheduler 使用的固定的线程池，大小为 CPU 核数。不要把 I/O 操作放在 computation() 中，否则 I/O 操作的等待时间会浪费 CPU。
- 另外， Android 还有一个专用的 AndroidSchedulers.mainThread()，它指定的操作将在 Android 主线程运行

####Operators
Operators在消息发送者Observable和消息消费者Subscriber之间起动操纵消息的作用。RxJava拥有大量的operators.

比如map() operator可以将已被发送的消息转换成另外一种形式。

Observable和Subscribers与它们之间的一系列转换步骤是相互独立的。

`filter()`方法是进行过滤操作的方法，`filter()`方法返回false的值将不会发出到`subscriber`。

		给Android开发者的RxJava详解 https://gank.io/post/560e15be2dca930e00da1083 （清楚详细）

 		RxJava Essentials 中文翻译版 https://rxjava.yuxingxin.com/（已下载）
		某学姐博客http://mouxuejie.com/blog/2016-03-27/rxjava-basis/

	

###Retrofit
*单独文件介绍了*

###Agera
	agera是一个能帮助Android开发者更好的开发函数式，异步和响应式程序的框架，要求Android的SDK版本在9以上
	agera博客分析http://blog.chengyunfeng.com/?p=984
	http://zjutkz.net/2016/04/23/%E8%A6%81%E5%81%9A%E4%B8%80%E4%B8%AA%E6%9C%89%E5%86%92%E9%99%A9%E7%B2%BE%E7%A5%9E%E7%9A%84%E4%BA%BA%EF%BC%81%E5%BC%80%E5%90%AF%E6%BC%AB%E6%BC%AB%E7%9A%84agera%E4%B9%8B%E6%97%85/

###Volly

Volly是Google官方出的一套小而巧的异步请求库，该框架封装的扩展性很强，支持HttpClient,HttpUrlConnection,甚至支持OkHttp,而且Volly里面也封装了ImageLoader。

Volly,OkHttp ,Retrofit都是比较好的开源网络库

参考`https://zhuanlan.zhihu.com/p/21879931`

### OkHttp3

添加依赖`compile 'com.squareup.okhttp3:okhttp:3.4.1'`，
也需要添加依赖 `compile 'com.squareup.okio:okio:1.11.0'`（因为OkHttp内部依赖Okio）,该库的作用 `Okio is a new library that complements java.io and java.nio to make it much easier to access, store, and process your data.`使用它可以更容易访问，存储和处理数据。
`Okio`提供了两种数据类型`ByteString`和`Buffer`.

还需要添加网络访问权限`<uses-permission android:name="android.permission.INTERNET"/>`


OkHttp是一个开源的针对Java和Android程序，封装的一个高性能http请求库，用的是`HttpUrlConnection`进行网络请求的,但是使用时还需要自己再做一层封装，这样才能像使用一个框架一样更加顺手。

GET a URL 直接向指定的资源URL发出请求,读取数据
POST to a SERVER 提交数据到服务端（提交表单或上传文件）

同步调用 client.newCall(request).execute();

异步调用 client.newCall(request).enqueue(new Callback(){...})
使用enqueue()方法，将call放入请求队列中，然后将OkHttp会在线程池中进行网络访问。

OkHttp3较详细讲解 `http://blog.csdn.net/biezhihua/article/details/50603624`

参考OkHttp3使用指南 `http://www.jianshu.com/p/457d3ab27584`

参考 Android OkHttp完全解析`http://blog.csdn.net/lmj623565791/article/details/47911083`


### NoHttp

目前出的新的网络请求库，支持换底层OkHttp,URLConnection。

参考`http://gold.xitu.io/post/58038d1c570c35006c7ddc83`

###ImageLoader图片加载库

图片加载库比较熟知的有 ` UniversalImageLoader、Picasso、Fresco、Glide`。

 - UniversalImagerLoader 作者已经不维护了
 - Picasso Squre出品
 	
		依赖 `compile 'com.squareup.picasso:picasso:2.5.1'`
 - Volley ImageLoader Google官方出品，不能加载本地图片
 - Fresco Facebook出品
 
		依赖： compile 'com.facebook.fresco:fresco:0.12.0'
		com.facebook.drawee.view.SimpleDraweeView直接作为ImageView的控件 ，Fresco的简单使用.
		getStart: https://www.fresco-cn.org/docs/getting-started.html中文文档

 - Glide 沿袭Picasso的简洁风格，做了一些改进
 
		依赖 compile 'com.github.bumptech.glide:glide:3.7.0'

		参考这里较全面http://mrfu.me/2016/02/27/Glide_Getting_Started/
		http://www.voidcn.com/blog/android_study_ok/article/p-6168423.html

		Glide官方使用文档中文版 https://www.gitbook.com/book/muzhi1991/android-glide-wiki/details（已下载）
        全局搜索图片加载的地方，全部换成了下面的代码：

        Glide.with(mContext)
             .load(url)
             .placeholder(R.drawable.loading_spinner)//设置占位图
             .error(R.drawable.imagenotfound)//加载错误图
             .crossFade()
             .into(myImageView);
		Glide 做了所有的网络请求和处理在后台线程中，一旦结果准备好了之后，切回到 UI 线程然后更新 View(ImageView).

	Glide转换，也就是将显示的ImageView转换为其他的形式，比如圆形图片等，主要用到这个库glide-transformations。
	
	使用：
			
			Glide.with()
				.XXX
				.....
				.bitmapTransform（）//这一句
	参考这里 http://www.voidcn.com/blog/android_study_ok/article/p-6168423.html


 Picasso和Glide的对比
`http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0327/2650.html`
 

参考`https://zhuanlan.zhihu.com/p/21397115`


###MVC
	MVC(Model-View-Controler)


###MVP
	MVC（Model-View-Controller，模型-视图-控制器）模式
	http://www.jianshu.com/p/9a6845b26856#
	
	MVC，MVVM模式


###MVVM
  MVVM ， Model-View-ViewModel

- Model  代表数据对象层
- View  代表布局，layout
- ViewModel  代表绑定数据，将Model 和 View联系起来

###Butterknife
	ButterKnife是一个Android系统的View注入框架，能够通过‘注解’的方式来绑定View的属性或方法。
总的来说，ButterKnife 有以下使用：

- View 绑定
- Resource 绑定
- 非 Activity 绑定
- View List 绑定
- Listener 绑定

一个注解框架，使用后可以减少一些代码量

添加依赖
这里以 Android Studio Gradle 为例，为项目添加 ButterKnife，注意两个步骤都要完成：

1. Project 的 build.gradle 添加：
  ` dependencies {
   classpath 'com.neenbedankt.gradle.plugins:android-apt:1.8'
   }`

2. App 的 build.gradle 添加：

	apply plugin: 'com.neenbedankt.android-apt'

	dependencies {
	compile 'com.jakewharton:butterknife:8.2.0'
	apt 'com.jakewharton:butterknife-compiler:8.2.0'
	}

Android Butterknife Zelezny这个插件参考`http://www.tuicool.com/articles/Q3mmay/`


### Gson
 Google官方的JSON解析库Gson
 
详细介绍
	http://blog.csdn.net/oqihaogongyuan/article/details/50944755


### RxBus
 基于RxJava写的事件总线

###EasyRecyclerView
EasyRecyclerView实际上不是RecyclerVIew，是FramLayout，是继承这个帧布局的布局管理器，在该布局管理器里包含RecyclerView组件。

	包含：
    protected RecyclerView mRecycler;//RecyclerView

    protected ViewGroup mProgressView;//进度布局

    protected ViewGroup mEmptyView;//数据为空布局

    protected ViewGroup mErrorView;//数据出错布局

	protected SwipeRefreshLayout mPtrLayout;//SwipeRefreshLayout刷新组件

	当然还包括各组件的事件监听器等（未列出）

    //高级的recyclerview,添加依赖：
    compile 'com.jude:easyrecyclerview:4.2.6'（最新版）
    compile 'com.android.support:recyclerview-v7:24.2.0'
	参考作者的介绍 https://github.com/Jude95/EasyRecyclerView/blob/master/README_ch.md
	更详细的介绍 C:\Users\Mr.Ye\Downloads\PDF资料文件/Android EasyRecyclerView详细讲解.pdf (已下载)

###dataBinding
 Android自带的一个数据绑定库,就是Android的一个Support库，Data Binding是一个实现数据和UI绑定的框架，是一个实现MVVM(Model-View-ViewModel)模式的工具，有了Data Binding在Android中也可以很方便地实现MVVM开发模式。在build.gradle文件中加上一下代码就可以使用了。

	android{
	   ....	
	   dataBinding {//设置可以使用dataBinding,是一个support 
         enabled = true
       }
	}
参考官方文档 `https://developer.android.com/topic/libraries/data-binding/index.html`
官方文档的中文版 `http://www.jianshu.com/p/b1df61a4df77`

Android Data Binding代码实战 `https://www.aswifter.com/2015/07/11/android-data-binding-example/`

`http://connorlin.github.io/2016/07/02/Android-Data-Binding-%E7%B3%BB%E5%88%97-%E4%B8%80-%E8%AF%A6%E7%BB%86%E4%BB%8B%E7%BB%8D%E4%B8%8E%E4%BD%BF%E7%94%A8/`

