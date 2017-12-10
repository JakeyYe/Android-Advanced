## Android Proguard（混淆）

	ProGuard is a Java class file shrinker, optimizer, obfuscator, and preverifier. 
	ProGuard是一个Java类文件压缩，优化，混淆和预校验器。它可以检测并删除未使用的类，字段，方法和属性。它可以优化字节码，并删除未使用的指令。它可以将类的，字段和方法使用短无意义的名称
	进行重命名。
给Android项目进行Proguard混淆打包，可以使apk体积减小点，apk瘦身，还可以混淆项目代码，增加反编译难度。启用通过ProGuard实现代码压缩。

	buildTypes {
          
          release { //发布版本
              minifyEnabled true //为true代码压缩
              shrinkResources true //为true,资源压缩
              //混淆的配置文件，前一个文件为系统提供的混淆文件，后一个文件时自定义的混淆文件
              proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
          }
    }

	资源压缩只与代码压缩协同工作。代码压缩器移除所有未使用的代码后，资源压缩器便可确定应用仍然使用的资源，所以只有同时设置
	 minifyEnable,shrinkResources为true,shrinkResources设置才有效。proguard-android.txt是系统自带的混淆文件，proguard-rules.pro
	是用户自定义的混淆文件，最后的混淆结果由这两个文件共同作用决定的。


### ProGuard（混淆）
	ProGuard是包含代码压缩，优化，混淆等一系列行为的过程,混淆过程会有如下几个功能：
	1,压缩：移除无效的类，类成员，方法等（-dontshrink命令禁用压缩）；
	2，优化：分析和优化方法的二进制代码，根据proguard-android-optimize.txt的描述，优化可能会造成已写潜在风险，不能保证在所有版本的Dalvik上都正常运行，proguard-android.txt是默认将优化关闭了的；
	3，混淆：把类名，类成员名，方法名替换为简短且无意义的名称（-dontobfuscate命令禁用混淆）；
	4，预校验：添加预校验信息，这个预校验是作用在Java平台上的，Android平台上不需要这项功能，去掉之后还可以加快混淆速度。

	在Android项目中我们可以将“优化”，“预校验”关闭，对应命令是 -dontoptimize,-dontpreverify(proguard-android.txt文件已经包含这两条命令的，不需要开发者额外配置)


### Proguard混淆原则

	这里形容的通用配置，也就是需要添加一些不需要混淆的代码，如：
	1，反射用到的类不混淆
	2，JNI方法不混淆
	3，AndroidManifest.xml文件中的类不混淆，四大组件和Application的子类和Framework层下所有的类默认不会进行混淆
	4，Parcelable的子类和CREATOR静态成员变量不混淆，系统提供的默认混淆文件已经默认设置不会进行混淆了
	5，使用GSON，fastjson等框架时，所写的JSON对象类不混淆，否则无法将JSON解析成对应的对象
	6，使用第三方开源库或者引用其他第三方的SDK包时，需要在混淆文件中加入对应的混淆规则
	7，有用到WebView的JS调用也需要保证写的接口不混淆（proguard-rules.pro文件中已写，只需要打开即可）
[Doc/3\_ProGuard基础语法和打包配置\.md at master · D\-clock/Doc](https://github.com/D-clock/Doc/blob/master/Android/Gradle/3_ProGuard%E5%9F%BA%E7%A1%80%E8%AF%AD%E6%B3%95%E5%92%8C%E6%89%93%E5%8C%85%E9%85%8D%E7%BD%AE.md)


### ProGuard混淆语法规则
	关键字：
	keep:保留类和类中的成员，防止它们被混淆或移除；
	keepnames
	keepclassmembers
	keepclassmembersnames
	keepclasseswithmembers
	keepclasseswithmembersnames
	通配符：
	<field>
	<method>
	<init>
	*
	**
	***
	...
[ProGuard混淆的世界](http://ntop001.github.io/2014/04/10/something-about-proguard/)


[Android安全攻防战，反编译与混淆技术完全解析（下） \- 郭霖的专栏 \- CSDN博客](http://blog.csdn.net/guolin_blog/article/details/50451259)

[官方文档之用户指南](https://developer.android.com/studio/build/shrink-code.html "压缩代码和资源")

[ProGuard使用手册英文版](https://stuff.mit.edu/afs/sipb/project/android/sdk/android-sdk-linux/tools/proguard/docs/index.html#/afs/sipb/project/android/sdk/android-sdk-linux/tools/proguard/docs/manual/usage.html)

### 代码增加破解难度：混淆或加壳
	1，加壳：将原apk中的dex文件取出，添加壳dex组成新apk,这一般直接使用第三方加壳技术就可以了，可以了解一下技术原理。
	2,混淆：http://blog.csdn.net/guolin_blog/article/details/50451259，https://www.diycode.cc/topics/380 要实践才能记住