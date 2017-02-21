#Android Proguard混淆
---
	ProGuard is a Java class file shrinker, optimizer, obfuscator, and preverifier. 
	ProGuard是一个Java类文件收缩，优化，混淆和预校验器。它可以检测并删除未使用的类，字段，方法和属性。它可以优化字节码，并删除未使用的指令。它可以将类的，字段和方法使用短无意义的名称进行重命名。
给Android项目进行Proguard混淆打包，可以使apk体积减小点，apk瘦身，还可以混淆项目代码，增加反编译难度。启用通过ProGuard实现代码压缩。

	buildTypes {
          debug {  //debug调试版本
              minifyEnable true //为true压缩代码
              shrinkResources true //为true,压缩资源
              }
          release { //发布版本
              minifyEnabled true //为true压缩代码
              shrinkResources true //为true,压缩资源
              //混淆的配置文件
              proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
              }
    }

	资源压缩只与代码压缩协同工作。代码压缩器移除所有未使用的代码后，资源压缩器便可确定应用仍然使用的资源，所以只有同时设置
	 minifyEnable,shrinkResources为true,shrinkResources设置才有效。proguard-android.txt是系统自带的混淆文件，proguard-rules.pro
	是用户自定义的混淆文件，最后的混淆结果由这两个文件共同作用决定的。

1，Proguard混淆配置文件通用配置

这里形容的通用配置，也就是需要添加一些不需要混淆的代码，比如Android的四大组件的相关代码，自定义View相关代码，项目中引用的第三方jar包相关代码等等。


自定义要保留的代码（自定义proguard-rules.pro文件）
要修正错误并强制ProGuard保留特定代码，在ProGuard配置文件中添加一行`-keep`代码，例如

	-keep public class MyClass


[官方文档之用户指南](https://developer.android.com/studio/build/shrink-code.html,"压缩代码和资源")

[ProGuard手册](https://stuff.mit.edu/afs/sipb/project/android/sdk/android-sdk-linux/tools/proguard/docs/index.html#,"点击查看ProGuard手册")

[Android ProGuard混淆](http://www.jianshu.com/p/60e82aafcfd0,)


