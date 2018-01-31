## Android Statusbar(状态栏)设置

在Android 5.0及其以上系统，可以直接通过系统API实现状态栏变色效果；

	Activity.setStatusbarColor();

Android 设置状态栏的工具类，可以在4.4及以上系统实现沉浸式状态栏/状态栏变色（沉浸式状态栏也就是将ContentView的内容绘制到状态栏位置上）；

[StatusBarUtil 状态栏工具类（实现沉浸式状态栏/变色状态栏）](https://jaeger.itscoder.com/android/2016/03/27/statusbar-util.html)


实现沉浸式状态栏效果时，ContentView布局上的内容会跑到状态栏上，不过在布局根视图上设置 fitSystemWindows 属性为true，系统自动为视图添加一个状态栏/导航栏高度的padding，这样就不会出现前面那样的情况了；

SYSTEM_UI_FULLSCREEN/SYSTEM_UI_FLAG_HIDE_NAVIGATION 主要是用于动态切换隐藏/显示系统状态栏/导航栏的；

在Activity上使用的主题中加上 android：windowTranslucentStatus="true" (**该属性能够实现透明状态栏效果，是在 Android 4.4 版本加上的，所以在 Android 4.4 以上版本使用都可以实现该效果**) 则可以将Activity的布局延伸到状态栏位置，不过内容也会随之展示在状态栏位置上，在Activity的根布局上加上 android:fitSystemWindow=“true”属性，系统就会自动为视图添加一个状态栏/导航栏高度的padding，这样Activity布局上的内容就不会再 状态栏上显示了；

[Android 状态栏操作，你想知道的都在这里了 \| YiFeng's Zone](http://yifeng.studio/2017/02/19/android-statusbar/)