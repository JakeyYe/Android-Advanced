## apk 瘦身 

	apk 瘦身，尽可能减小 apk 文件安装包的大小；

### apk 瘦身可以从这几个方面下手

#### 1，资源文件瘦身

资源文件是占apk大部分容量的，所以最应该减小资源文件的大小，其中图片资源文件占的容量是最大的；

	只保留一份资源文件（只保留drawable-xxhdpi目录下的图片资源）；
	尽可能使用XML文件（Drawable XML/Color）、.9.png文件，svg代替单纯的图片文件；
	使用 JPG 代替 PNG 图片，由于 JPG 没有 Alpha通道，所以文件更小，适用于不需要透明度的图片；
	要使用图片，也要使用软件进行压缩；

#### 2，so 文件也挺大的

	so文件只使用armeabi CPU架构的就看可以了，这个可以兼容大部分的CPU架构；abiFilters,只保留arm主流架构的so文件；

#### 3，代码混淆，移除未用的资源文件

	minifyEnabed/shrinkResources，开启ProGuard工具除了会混淆源代码外，还会移除未使用的类和类方法等；

#### 4，代码方面，控制使用开源库


[Android应用瘦身，从18MB到12\.5MB \| 技术视界](http://blog.coderclock.com/2017/01/24/android/Android%E5%BA%94%E7%94%A8%E7%98%A6%E8%BA%AB%EF%BC%8C%E4%BB%8E18MB%E5%88%B012.5MB/)

