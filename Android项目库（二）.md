#关于Android项目要了解的库（二）

-------
*多个开源库的介绍：
`http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0813/3296.html`*
###greenDao
以下三个都是数据库


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
	参考这里https://github.com/Jude95/RollViewPager/blob/master/README_ch.md

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

    更多就参考作者文档 	`https://github.com/orhanobut/logger`
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
参考官方文档：`https://bugly.qq.com/androidsdk`

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

参考GitBook中的android-rd-senior-advanced.pdf中的Android事件驱动编程（二）,已下载

###html-textview
TextView to display simple HTML content，TextView来显示简单的HTML内容.

依赖：

	compile 'org.sufficientlysecure:html-textview:3.1'