## Android样式开发

[Android Attr、Style和Theme详解 \- 简书](http://www.jianshu.com/p/d448ee26671d)

Android的样式开发，不需要全部记住，但要总结清楚，要会用，需要用的时候，就直接翻看自己的总结，这样也能快速熟悉。

	Android中的样式与网页设计中层叠样式表的原理类似-可以通过它将设计与内容分离。
	
	某些样式属性任何View元素都不提供支持，只能以主题形式应用，这些样式属性应用于整个窗口而非任何类型的View,这些属性在R.attr中是以window开头。


### [Android样式开发-小钢](https://keeganlee.me/post/android/20150830)

### Ripple标签，用于显示点击出现波纹效果
#### [Ripple标签](http://www.jianshu.com/p/3339f0ebb335)

### 为什么项目中会有这两个文件styles和styles-v21?
[走着官方的教程入门Material Design（一） \- 简书](http://www.jianshu.com/p/4c2d90d850df)

### 主题中比较重要的属性
	windowNoTitle-去掉标题栏(也就是ActionBar那部分)（使用AppCompat的主题，不需要加android:前缀，该属性是该主题内自定义的属性）
	android:windowIsTranslucent

	隐藏ActionBar可以通过修改我们继承的主题为：Theme.AppCompat.Light.NoActionBar，当然也可以通过设置以下属性完成：
	<item name="windowActionBar">false</item>
	<item name="android:windowNoTitle">true</item>

### Android Theme
	//5.0以上系统使用的主题(res\values-v21文件夹中)
 	<style name="AppTheme" parent="android:Theme.Material.Light">
     <!-- Customize your theme here. -->            
 	</style>

 	//5.0以下系统使用的主题(res\values文件夹中)
	<!--Theme.AppCompat 主题可为一些小组件提供 Material Design 风格-->
 	<style name="AppTheme" parent="Theme.AppCompat.Light">
     <!-- Customize your theme here. -->
 	</style>

	Holo Theme
	在4.0之前Android可以说是没有设计可言的，在4.0之后推出了Android Design，从此Android在设计上有了很大的改善，而在程序实现上相应的就是Holo风格，所以你看到有类似 
	Theme.Holo.Light、 Theme.Holo.Light.DarkActionBar 就是4.0的设计风格，但是为了让4.0之前的版本也能有这种风格怎么办呢？这个时候就不得不引用v7包了，所以对应的就有 
	Theme.AppCompat.Light、Theme.AppCompat.Light.DarkActionBar，如果你的程序最小支持的版本是API14（即Android 4.0），那么可以不用考虑v7的兼容。

	Material Design Theme
	Android在5.0版本推出了Material Design的概念，这是Android设计上又一大突破。对应的程序实现上就有Theme.Material.Light、 
	Theme.Material.Light.DarkActionBar等，但是这种风格只能应用在在5.0版本的手机，如果在5.0之前应用Material Design该怎么办呢？同样的引用appcompat-v7包，这个时候的
	Theme.AppCompat.Light、Theme.AppCompat.Light.DarkActionBar就是相对应兼容的Material Design的Theme。
[Android关于Theme\.AppCompat相关问题的深入分析 \- 简书](http://www.jianshu.com/p/6ad7864e005e)

	API 21:(Android Material Design)
	Theme.Material Material根主题
	Theme.Material.Light Material白主题
	
	兼容包v7所带的主题：（现在只需要知道是兼容API 21 以上的主题风格就可以了）
	Theme.AppCompat 兼容主题的根主题
	Theme.AppCompat.Light 兼容主题的白色主题

[总结一下Android中主题\(Theme\)的正确玩法\_安卓\_何问起](http://hovertree.com/h/bjaf/py9end45.htm)



#### 注意点
	使用android系统中自带的主题要加上“android:”，如：android:Theme.Material.Light
	使用v7兼容包中的主题不需要前缀，直接：Theme.AppCompat.Light

	主题的来源：
	1，来自Android系统自带的
	2，来自兼容包（比如V7兼容包）
	3，开发者自定义主题

	compile 'com.android.support:appcompat-v7:21.0.3'中的21代表的是API 21，也就是该兼容包是API 21所推出的兼容包，所以你的应用若支持API 21以下的版本，则API 21以下版本所显示的主
	题Theme.AppCompat就是Theme.Material的主题，也就是使用Theme.AppCompat可以在API 21以下版本实现Theme.Material的主题风格。---AppCompat v21可以提供Android 5.0特性支持。