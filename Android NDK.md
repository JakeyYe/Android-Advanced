# Android NDK

	JNI应用场景有：1加密；2，音视频解码，图像操作；3，安全相关；4，游戏开发 等等。

	JNI只是一种转换规则，提供支持了Java调用C/C++代码。

	NDK是Android所提供的工具集合，通过NDK可以在Android中更加方便地通过JNI来访问本地代码，比如C或者C++。NDK还提供了交叉编
	译器，开发人员只需要简单地修改mk文件就可以生成特定CPU平台的动态库。

	NDK还提供了一份稳定、功能有限的API头文件声明。

	Android提供NDK来将C++代码编译为JNI库，然后可在Java环境下调用。

JNI调用常用的两个参数：

JNIEnv *env,jObject obj

第一个是指向虚拟机对象的指针，是一个二级指针，里面封装了很多方法和中间变量供我们使用；
第二个参数代表着调用该方法的Java对象的C语言表示。

### 参考 [Android NDK初体验](http://www.jianshu.com/p/ceb36559b6b3)

[向您的项目添加 C 和 C\+\+ 代码 \| Android Studio](https://developer.android.com/studio/projects/add-native-code.html#existing-project)

### 重点记录
	最新的Android Studio支持了通过CMake构造NDK的方式，通过CMake来编译C/C++文件.
	CMake是一款外部构建工具，可与Gradle搭配使用来构建原生库，如果只是使用ndk-build，则不需要使用这个组件。

[Android Studio 开发JNI笔记\-\-① \- 知乎专栏](https://zhuanlan.zhihu.com/p/25056906)

[在 Android Studio 2\.2 中愉快地使用 C/C\+\+ \| 湫水](http://wl9739.github.io/2016/09/21/%E5%9C%A8-Android-Studio-2-2-%E4%B8%AD%E6%84%89%E5%BF%AB%E5%9C%B0%E4%BD%BF%E7%94%A8-C-C-md/)

[Android Studio 2\.3下NDK开发流程 \- 郭霖 \| 十条](http://www.10tiao.com/html/227/201704/2650239332/1.html)