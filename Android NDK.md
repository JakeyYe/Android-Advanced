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


### 谈谈 ABI 和 so

CPU架构 -> ABI -> .so

Android 支持多种 CPU 架构，每一种 CPU 架构，都定义了一种 ABI （Application Binary Interface，应用二进制接口），ABI 定义了其所对应的 CPU 架构能够执行的二进制文件（如 .so 文件） 的格式规范，决定了二进制文件如何与系统进行交互；

so (shared object,共享库)是机器可以直接运行的二进制代码，是Android 上的动态链接库，类似于 Windows 上的dll,每一个 Android 应用所支持的ABI是其 APK 提供的 .so 文件决定的；

[谈谈Android的so \| Allen's Zone](http://allenfeng.com/2016/11/06/what-you-should-know-about-android-abi-and-so/)

