## Android开发之启动页
	记录：应用未退出黑屏后亮屏的生命周期是onRestart()->onStart()->onResume()

1）Android启动页优化，去调用黑屏（白屏）

启动页优化有两种方式（**都是两步操作，启动页自定义的主题都只是设置给首先启动的Activity而已，还要在super.onCreate()之前切换自己的Theme**）：

1，**设置启动Activity的theme，在theme中通过android:windowBackground属性设置为我们想要的背景**

	<style name="LaunchTheme" parent="Theme.Appcompat.NoActionBar">
		<item name="windowNoTitle">true</item>
		<item name="windowFullScreen">true</item>
		<item name="android:windowBackground">@drawable/xxxx(@color/xxxx)</item>
	</style>

	该主题是设置给第一个启动的Activity A的，不要设置给Application，不然所有Activity都会继承该主题，还有就是在Activity A中的onCreate()方法要重新设置该Activity本来的主
	题，要在super.onCreate()方法之前设置。这种方式是会运行完onResume()方法才会显示真正的界面的。


2，**使用全屏透明主题android:Theme.Translucent.NoTitleBar.FullScreen**

	<!--使用全屏透明主题-->
	<style name="FullScreen" parent="android:Theme.Translucent.NoTitleBar.Fullscreen"/>
	单独设置给首先启动的Activity作为主题，也要在super.onCreate()方法之前设置真正的主题，这种方式也是运行完onResume()方法才会进入应用，完全显示界面的。


2）从用户点击launcher图标到看到界面第一帧为应用启动过程，主要会经过以下这些方法：

	main()->Application:attachBaseContext()->onCreate()->Activity:onCreate()->onStart()->onResume()


[Android 应用启动界面自定义 \- 云在千峰](http://blog.chengyunfeng.com/?p=741)

[Android冷启动实现APP秒开 \- 简书](http://www.jianshu.com/p/03c0fd3fc245)

### 记忆：Observable.timer()操作符，延迟执行某个操作，第一个参数代表延迟时长，第二个参数代表延迟时长的单位；