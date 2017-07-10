#`Gradle for Android`
	Android Applications使用gradle构建，gradle是一门高级语言并广泛用于Java中，提供的Android插件为Android app开发提供了
	很多的功能
[Gradle for Android](http://www.jianshu.com/p/cfa802396c6a)

###1，一个`Android`项目文件中至少有两个`build.gradle`文件，其中一个是项目全局的`build.gradle`文件，其他的都是`Module`的`build.gradle`文件。

###2，`gradle`的各部分：

  - `apply plugin`领域：表示`Gradle`所引入的插件。在`Module`的`build.gradle`文件的最顶部声明`apply plugin:``com.android.application`，表示该`Module`是`Android`项目的主`Module`,是一个`Android Application`,而声明为`apply plugin:``com.android.library`表示该`Module`为一个库（`Module`）。

  - `android{...}`:描述了该`Android Module`构建过程中所用到的所有参数。
  - `defaultConfig{...}`:位于`android{...}`内，表示默认配置，会同时应用到debug和release版本上。
  - `dependencies{...}`：描述了该`Android Module`构建过程中所依赖的所有库,库的形式包括两种：`jar`和`aar`,使用`aar`更加好。
  - `compileOptions{...}`:位于`android{...}`内，java版本号。
  - `buildTypes{...}`:位于`android{...}`内，编译类型，默认两种类型`debug，release`。
  - `signingConfigs{...}`:位于`android{...}`内，签名配置。
  - `proguardFiles`这部分有两段，前一部分代表系统默认的android程序的混淆文件，该文件已经包含了基本的混淆声明，免去了我们一部分混淆工作，该文件的目录是再`/tool/proguard/proguard-android.txt`，后一段是我们项目里的自定义的混淆文件，目录在`app/proguard-rules.pro`，在这个文件里你可以声明一些第三方依赖的一些混淆规则，最终的混淆结果是由这两部分文件的共同作用的。

###更多参考[官方文档](http://google.github.io/android-gradle-dsl/current/index.html)

###3,构建全局配置
  声明全局参数：在项目全局的`build.gradle`文件中，通过`ext`领域可以指定全局的配置信息，如下所示：

	ext {
       compileSdkVersion =24
	   buildToolsVersion ="24.0.2"
	   minSdkVersion =19
	}

  引用全局配置参数：在项目全局的`build.gradle`文件中配置好全局参数之后，就可以在个`Module`中通过`rootPrject.ext`引用全局参数，如下所示：

	android {
       compileSdkVersion rootProject.ext.compileSdkVersion
	}

	
###深入了解参考[Gradle for Android 问题总结](http://www.jianshu.com/p/9dcec4a14c52#)