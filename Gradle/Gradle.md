# `Gradle for Android`
	Android Applications使用gradle构建，gradle是一门高级语言并广泛用于Java中，提供的Android插件为Android app开发提供了很多的功能

	Gradle是以Groovy语言为基础，面向Java应用为主，基于DSL(领域特定语言)语法的自动化构建工具：
	1，Gradle也是一门语言
	2，Gradle是一个自动化构建工具

	Gradle中有两个最基本的概念：project和task。Gradle里面的所有东西都基于这两个概念。project通常指一个项目，而task指构建过程中的任务。一次构建可以有1到n个project，而每个project有1
	到n个task。
[Doc/2\_Gradle语法基础解析\.md at master · D\-clock/Doc](https://github.com/D-clock/Doc/blob/master/Android/Gradle/2_Gradle%E8%AF%AD%E6%B3%95%E5%9F%BA%E7%A1%80%E8%A7%A3%E6%9E%90.md)

[Gradle for Android](http://www.jianshu.com/p/cfa802396c6a)

[Gradle插件用户指南（中文版）](http://rinvay.github.io/android/2015/03/26/Gradle-Plugin-User-Guide%28Translation%29/)

[第一篇：groovy对DSL的语法支持 \- 身带吴钩 \- 博客园](http://www.cnblogs.com/chenjie0949/p/4755389.html)
### 1，一个`Android`项目文件中至少有两个`build.gradle`文件，其中一个是项目全局的`build.gradle`文件，其他的都是`Module`的`build.gradle`文件。

### 2，`gradle`的各部分：

  - `apply plugin`领域：表示`Gradle`所引入的插件。在`Module`的`build.gradle`文件的最顶部声明`apply plugin:``com.android.application`，表示该`Module`是`Android`项目的主`Module`,是一个`Android Application`,而声明为`apply plugin:``com.android.library`表示该`Module`为一个库（`Module`）。

  - `android{...}`:描述了该`Android Module`构建过程中所用到的所有参数。
  - `defaultConfig{...}`:位于`android{...}`内，表示默认配置，会同时应用到debug和release版本上。
  - `dependencies{...}`：描述了该`Android Module`构建过程中所依赖的所有库,库的形式包括两种：`jar`和`aar`,使用`aar`更加好。
  - `compileOptions{...}`:位于`android{...}`内，java版本号。
  - `buildTypes{...}`:位于`android{...}`内，编译类型，默认两种类型`debug，release`。
  - `signingConfigs{...}`:位于`android{...}`内，签名配置。
  - `proguardFiles`这部分有两段，前一部分代表系统默认的android程序的混淆文件，该文件已经包含了基本的混淆声明，免去了我们一部分混淆工作，该文件的目录是再`/tool/proguard/proguard-android.txt`，后一段是我们项目里的自定义的混淆文件，目录在`app/proguard-rules.pro`，在这个文件里你可以声明一些第三方依赖的一些混淆规则，最终的混淆结果是由这两部分文件的共同作用的。

#### 更多参考[官方文档](http://google.github.io/android-gradle-dsl/current/index.html)

### 3,构建全局配置(两种方式)
  3.1 声明全局参数：在项目全局的`build.gradle`文件中，通过`ext`领域可以指定全局的配置信息，如下所示：

	ext {
       compileSdkVersion =24
	   buildToolsVersion ="24.0.2"
	   minSdkVersion =19
	}

  引用全局配置参数：在项目全局的`build.gradle`文件中配置好全局参数之后，就可以在个`Module`中通过`rootPrject.ext`引用全局参数，如下所示：

	android {
       compileSdkVersion rootProject.ext.compileSdkVersion
	}


3.2 在gradle.properties文件声明全局参数，然后调用

3.3 在项目根目录下创建一个config.gradle文件，可用来保存项目配置常量，如果没有可直接在根目录下创建该文件，如这样的：
	//config.gradle文件
	ext {
    plugins = [
            library    : 'com.android.library',
            application: 'com.android.application',
            maven      : 'com.github.dcendents.android-maven',
            bintray    : 'com.jfrog.bintray'
    ]

    android = [
            applicationId    : "com.yanzhenjie.recyclerview.swipe.sample",
            compileSdkVersion: 25,
            buildToolsVersion: "25.0.3",
    ]

    bintray = [
            version       : "1.1.3"
	]

    dependencies = [
            appCompat        : 'com.android.support:appcompat-v7:25.3.1'
    ]
	}

	//build.gradle文件中使用config.gradle文件中的配置
	apply plugin: rootProject.ext.plugins.application

	android {
    compileSdkVersion rootProject.ext.android.compileSdkVersion

    defaultConfig {
        applicationId rootProject.ext.android.applicationId
    }
	}

	dependencies {
    compile rootProject.ext.dependencies.swipeRecyclerView
	}
	
### 深入了解参考[Gradle for Android 问题总结](http://www.jianshu.com/p/9dcec4a14c52#)

### [buildscript和allprojects的作用和区别是什么？ \- 简书](http://www.jianshu.com/p/ee57e4de78a3)