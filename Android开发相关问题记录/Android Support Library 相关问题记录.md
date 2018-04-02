## Android Support Library相关问题记录

[支持库 \| Android Developers](https://developer.android.com/topic/libraries/support-library/index.html)

[支持库功能 \| Android Developers](https://developer.android.com/topic/libraries/support-library/features.html)

[Android Support Library的前世今生 \- 简书](https://www.jianshu.com/p/f5f9a4fd22e8)

[Google's Maven Repository 库版本信息](https://dl.google.com/dl/android/maven2/index.html)

为了避免实用了最新功能开发的`APP`只能在最新系统的设备上运行的尴尬，官方把新版系统`framework`最新功能的接口提取出来放到了 `Android Support Library`(支持包)中，开发者在遇到低版本中不能实用高版本提供的`API`这种情况时就可以实用支持包中具有同样功能的`API`了，这个支持包会打包进`APP`里，这样使用了新版本系统上功能的`APP`也可以向后兼容以前的系统版本设备了；

使用支持包中的类除了让我们免于判断`APP`运行的系统版本外，还可以使`APP`在各个版本中保持同样的用户体验，如在 5.0 以下系统中也可以使用`Material Design`设计；

`APP`编译时用的`Android SDK(android.jar)`是不会打包进我们的`APP`中的，因为`APP`编码是使用`android.jar`中的接口就是`Android`设备里的系统框架层（`framework`）对外提供的接口；

![Support Library](https://upload-images.jianshu.io/upload_images/1621638-1f66aafb225df824.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

上图中的 `V4 Support Libraries`和 `V7 Support Libraries` 都是支持` Android 2.3` 版本以上系统的，其实现在只需要兼容的版本是4.4以上，所以其实不需要使用这些 `Support Library`的，使用比较多的是`v4 core-ui library`支持库中的`ViewPager/DrawerLayout/NestedScrollView`等控件，`v4 fragment library`支持库中的`Fragment`；

	//引入整个V4支持库，包括其5个子库
	compile `com.android.support:support-v4:24.2.1`

	注意：由于依赖的支持库会打包进apk，所以官方推荐开发者在编译时使用ProGuard工具预处理release版本的apk。ProGuard工具除了
	混淆源代码外，还会移除那些依赖的支持库中没有使用到的类，达到apk瘦身的效果。

#### V4 Support Library
该库旨在与 Android 2.3 （API 9）及更高版本搭配使用；在 V4 支持库修订版 24.2.0 之前，存在一个 V4 支持库，之后的新版本将此库拆分为了 5 个库：

	v4 compat : com.android.support:support-compat:25.3.1
	v4 core-utils: com.android.support:support-core-utils:25.3.1
	v4 core-ui: com.android.support:support-core-ui:25.3.1
	v4 media-compat: com.android.support:support-media-compat:25.3.1
	v4 fragment: com.android.support:support-fragment:25.3.1


#### V7 appcompat Library(Android 2.3,API 9)
此库添加了对操作栏用户界面设计模式的支持，此库包含包含对 Material Design 用户界面实现的支持；注意：此库依赖 V4 支持库；

	com.android.support:appcompat-v7:25.3.1

	其中有：
	ActionBarDrawerToggle
	AlertDialog
	AppCompatActivity
	Toolbar
	PopupMenu
	SearchView

	//appcompat-v7 和 support-v4 包依赖树
	+--- com.android.support:appcompat-v7:25.1.0
	|    +--- com.android.support:support-annotations:25.1.0
	|    +--- com.android.support:support-v4:25.1.0
	|    |    +--- com.android.support:support-compat:25.1.0
	|    |    |    \--- com.android.support:support-annotations:25.1.0
	|    |    +--- com.android.support:support-media-compat:25.1.0
	|    |    |    +--- com.android.support:support-annotations:25.1.0
	|    |    |    \--- com.android.support:support-compat:25.1.0 (*)
	|    |    +--- com.android.support:support-core-utils:25.1.0
	|    |    |    +--- com.android.support:support-annotations:25.1.0
	|    |    |    \--- com.android.support:support-compat:25.1.0 (*)
	|    |    +--- com.android.support:support-core-ui:25.1.0
	|    |    |    +--- com.android.support:support-annotations:25.1.0
	|    |    |    \--- com.android.support:support-compat:25.1.0 (*)
	|    |    \--- com.android.support:support-fragment:25.1.0
	|    |         +--- com.android.support:support-compat:25.1.0 (*)
	|    |         +--- com.android.support:support-media-compat:25.1.0 (*)
	|    |         +--- com.android.support:support-core-	ui:25.1.0 (*)
	|    |         \--- com.android.support:support-core-	utils:25.1.0 (*)
	|    +--- com.android.support:support-vector-drawable:25.1.0
	|    |    +--- com.android.support:support-annotations:25.1.0
	|    |    \--- com.android.support:support-compat:25.1.0 (*)
	|    \--- com.android.support:animated-vector-drawable:25.1.0
	|         \--- com.android.support:support-vector-drawable:25.1.0 (*)

#### V7 recyclerView Library
v7 recyclerView库添加 RecyclerView类；

	com.android.support:recyclerview-v7:25.3.1

#### V7 cardView Library
v7 cardView库添加 CardView类；

	com.android.support:cardview-v7:25.3.1

#### Annotations Support Library
提供注解相关功能的支持库；

	com.android.support:support-annotations:25.3.1

#### Design Support Library
该库提供了 Material Design 设计风格的控件，如 DrawerLayout、FloatingActionBar、Snacker等等；
	
	com.android.support:design:25.3.1
	该库中有(该库主要是Material Design风格的控件)：
	AppBarLayout
	BottomNavigationView
	BottomSheetDialog
	CollapsingToolbarLayout
	CoordinatorLayout
	FloatingActionButton
	NavigationView
	Snacker
	TabLayout
	TextInputEditText
	TextInputLayout

	Design 包依赖树
	+--- com.android.support:design:25.1.0
	|    +--- com.android.support:support-v4:25.1.0 (*)
	|    +--- com.android.support:appcompat-v7:25.1.0 (*)
	|    +--- com.android.support:recyclerview-v7:25.1.0
	|    |    +--- com.android.support:support-annotations:25.1.0
	|    |    +--- com.android.support:support-compat:25.1.0 (*)
	|    |    \--- com.android.support:support-core-ui:25.1.0 (*)
	|    \--- com.android.support:transition:25.1.0
	|         +--- com.android.support:support-annotations:25.1.0
	|         \--- com.android.support:support-v4:25.1.0 (*)


#### Multidex Support Library
解决 Android 单个 dex 文件最多只能引用65536个方法的限制，当我们的方法数超过这个限制后，就需要分成多个dex文件，该库就是用来支持多个dex文件构建应用程序的；

	com.android.support:multidex:1.0.0


#### v13 Support Library
v13 支持库使用范围是 Android 3.2（API 13）及其以上版本；这个库跟 v4 fragment library 功能基本一样，也是提供兼容Fragment相关内容；区别是 v4 fragment library 需要依赖 v4 支持库集合里的其它 4 个子库，而 v13 Support Library 依赖的是 Android 3.2（API 13）及其以上版本的framework，也就是说 v4支持库除了v4 fragment library 以外，其它功能都在 Android 3.2(API 13)及其以上版本的framework中提供了。

	com.android.support:support-v13:25.3.1


[Difference between v4 and v13 support library in Android?](https://stackoverflow.com/questions/27213692/difference-between-v4-and-v13-suport-library-in-android)

### 关于Support Library考虑一个问题：如果我只是兼容4.4版本以上的Android系统，我还需要引用 Support Library吗？如果引用这么多 Support Library，不开启Proguard是否会全部打包进apk中？如果开启了Proguard,没有使用的Support Library中的代码是否会被打包进apk中？

	第一个问题：
	可能也需要引用，但不是为了兼容2.3这些低版本，引入这些库可能是需要使用库中的Material Design风格的控件等原因；

	第二个第三个问题：
	开启Proguard后，是会将Support Library中没有用到的类移除，不会打包进apk中的；