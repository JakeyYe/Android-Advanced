#关于Android项目要了解的库（二）

-------
[多个开源库的介绍](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0813/3296.html)
###greenDao
加上下面那两个，这三个都是关于数据库的库。


###ormLite


###Realm
`Realm is a mobile database;a replacement for SQLite & ORMs.`是一个移动端的数据库。


###PhotoView
图片浏览缩放插件

- 首先在工程的build.gradle上面添加JitPack仓库
	
	```allprojects {
		repositories {
      	...
      	maven { url "https://jitpack.io" }
			}
		}```

- 其次，在模块的build.gradle上面添加依赖
```dependencies {
   compile 'com.github.chrisbanes:PhotoView:1.3.0'
}```


###富文本

使用该库可以方便地实现不同形式的文本

    compile 'com.github.iwgang:simplifyspan:1.1'

###轮播图片

`RollViewPager`一个图片轮播的控件

    compile 'com.jude:rollviewpager:1.2.9'

参考[控件github页面介绍](https://github.com/Jude95/RollViewPager/blob/master/README_ch.md)

###Android日志记录—Logger,Timber,logback
- Logger
	依赖 compile 'com.orhanobut:logger:1.15'支持更高级的Log,不过Log都是打印在控制台里，适合用于开发调试。

    Logger的使用：

    1，添加依赖,在Module的build.gradle文件中添加依赖

	2，在自定义`Application`的`onCreate()`中设置`Logger.init(TAG)；`

	3，就可以直接使用了，简单使用方式如下：

	`Logger.d("hello");`

	`Logger.e("hello");`

	`Logger.w("hello");`

	`Logger.v("hello");`

	`Logger.wtf("hello");`

	`Logger.json(JSON_CONTENT);`

	`Logger.xml(XML_CONTENT);`

	`Logger.log(DEBUG, "tag", "message", throwable);`

   更多参考[作者文档](https://github.com/orhanobut/logger)

- Timber
	Timber是对Android的Log类进行封装的一个工具类。
	依赖 `compile 'com.jakewharton.timber:timber:4.3.1'`支持Log输出到控制台，也支持输出到其他地方，比如文件等。
```使用方法：
在Application 的 onCreate() 方法中添加 Timber.plant(new Timber.DebugTree())。

接着就可以在你想打印日志的地方调用：Timber.v() 等方法，且不需要输入 TAG，Timber 会直接用当前的类名作为 TAG。

如果你想修改默认 TAG，则可以在使用 Timber.tag(<tag-name>)。```
- logback
	支持将Log输出到更多地方。

###现代I/O操作函数库okio
okio作为java.io和java.nio的补充，是由square公司开发的一个函数库，使得开发者可以更方便的访问，存储和处理数据。一开始作为okhttp的一个组件存在，当然现在我们也可以单独使用它。

###Android的Crash崩溃解决方案——Bugly的使用
腾讯的Bugly可以在app出现崩溃的时候上传错误信息，定位错误原因和语句，并且可以查看影响的用户数和程序Crash次数等等信息。
参考[官方文档](https://bugly.qq.com/androidsdk)

###Android Support Annotations注解
添加依赖 `compile 'com.android.support:support-annotations:20.0.0'`
Support Library自身也使用这些注解。

有三种类型的注解可供我们使用：

- NUllness注解

- 资源类型注解

- IntDef和StringDef注解


###事件驱动编程库
- EventBus,出自greenrobot。这个函数库专为Android而优化过，并具有某些高级特性和订阅者优先级。
- Otto,出自Square。

###EventBus3.0
	添加依赖compile 'org.greenrobot:eventbus:3.0.0'
`EventBus is a publish/subscribe event bus optimized for Android.`
`EventBus`是一款针对Android优化的发布/订阅（`publish/subscribe`）事件总线。主要功能是替代`Intent,Handler,BroadCast`在`Fragment,Activity,Service,线程之间传递消息的`。

`EventBus`作为一个消息总线，有三个主要的元素：

- `Event`：事件，可以是任意类型的对象。
- `Subscriber`：事件订阅者，接收并处理订阅的事件。在EventBus 3.0中，不在使用约定的方法来处理事件，可以自定义处理事件的方法名。
- `Publisher`:事件发布者，用于通知`Subscriber`有事件发生。可以在任意线程任意位置发送事件，直接调用`eventBus.post(Object)`方法，可以自己实例化`EventBus`对象但一般使用默认的单例就好了:`EventBus.getDefault()`,根据post函数参数的类型，会自动调用订阅相关类型事件的函数。
- `ThreadMode`:定义函数在何种线程中执行。`ThreadMode`总共有四种类型，分别为：`MAIN UI主线程,BACKGROUND 后台线程,POSTING 和发布者处在同一个线程,ASYNC 异步线程`。
 
	```@Subscribe(threadMode=ThreadMode.MAIN)``` //在UI线程中执行
	```public void onEvent(MessageEvent event){```
	```//TODO somethings
	}```
	

关键方法：

1）`EventBus.getDefault.register(this);`//订阅事件

2）`EventBus.getDefault.post(Object);`//发布事件

3）`EventBus.getDefault.unregister(this);`//取消订阅


参考[EventBus 3.0 源码分析](http://www.jianshu.com/p/f057c460c77e)

[Android-EventBus－3.0.0使用](http://www.jianshu.com/p/bd645ace4f73)

[EventBus 源码解析](http://a.codekk.com/detail/Android/Trinea/EventBus%20%E6%BA%90%E7%A0%81%E8%A7%A3%E6%9E%90)

参考`GitBook`中的`android-rd-senior-advanced.pdf`中的`Android`事件驱动编程（二）,已下载

###html-textview
`TextView to display simple HTML content，TextView`来显示简单的`HTML`内容.

依赖：

	compile 'org.sufficientlysecure:html-textview:3.1'

##jsoup
	Java HTML Parser

	添加依赖compile 'org.jsoup:jsoup:1.10.2'
jsoup是一款Java的HTML解析器，可直接解析某个URL地址，HTML文本内容。它提供了一套非常省力的API，可通过DOM,CSS以及类似于jQuery的操作方法来取出和操作数据。

参考[官方文档	](https://jsoup.org/)

[使用 jsoup 对 HTML 文档进行解析和操作](https://www.ibm.com/developerworks/cn/java/j-lo-jsouphtml/)

[Java上的jQuery？解析HTML利器—Jsoup](http://www.cnblogs.com/mokafamily/p/3558620.html)

##Lottie
 
`Lottie`是`Airbnb`开源的动画项目，支持`Android，iOS，ReactNative`三个平台，`Lottie`是将`json`文件转化为动画，使动画的制作更加简单了。该项目展示的所有动画都是在`After Effects`创建的，通过`Bodymovin`插件将在`After Effects`创建的动画导出为`json`文件，如果通过该开源库将`json`文件展示出来,就是动画效果了。`Lottie`使用`json`文件来作为动画数据源，`json`文件是通过[Bodymovin](https://github.com/bodymovin/bodymovin)插件导出的，json文件是描述每个元素的动画执行路径和执行时间，Lottie的功能就是读取这些数据，然后绘制到屏幕上。

	添加依赖 compile 'com.airbnb.android"lottie:1.5.0'


参考 [从json文件到炫酷动画-Lottie实现思路和源码分析](http://www.jianshu.com/p/81be1bf9600c)