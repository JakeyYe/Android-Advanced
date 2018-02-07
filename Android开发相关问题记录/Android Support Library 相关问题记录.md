## Android Support Library相关问题记录

[支持库 \| Android Developers](https://developer.android.com/topic/libraries/support-library/index.html)

[支持库功能 \| Android Developers](https://developer.android.com/topic/libraries/support-library/features.html)

为了避免实用了最新功能开发的`APP`只能在最新系统的设备上运行的尴尬，官方把新版系统`framework`最新功能的接口提取出来放到了 `Android Support Library`(支持包)中，开发者在遇到低版本中不能实用高版本提供的`API`这种情况时就可以实用支持包中具有同样功能的`API`了，这个支持包会打包进`APP`里，这样使用了新版本系统上功能的`APP`也可以向后兼容以前的系统版本设备了；

使用支持包中的类除了让我们免于判断`APP`运行的系统版本外，还可以使`APP`在各个版本中保持同样的用户体验，如在 5.0 以下系统中也可以使用`Material Desing`设计；

`APP`编译时用的`Android SDk(android.jar)`是不会打包进我们的`APP`中的，因为`APP`编码是使用`android.jar`中的接口就是`Android`设备里的系统框架层（`framework`）对外提供的接口；

![Support Library](https://upload-images.jianshu.io/upload_images/1621638-1f66aafb225df824.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/700)

上图中的 `V4 Support Libraries`和 `V7 Support Libraries` 都是支持` Android 2.3` 版本以上系统的，其实现在只需要兼容的版本是4.4以上，所以其实不需要使用这些 `Support Library`的，使用比较多的是`v4 core-ui library`支持库中的`ViewPager/DrawLayout/NestedScrollView`等控件，`v4 fragment library`支持库中的`Fragment`；

	//引入整个V4支持库，包括其5个子库
	compile `com.android.support:support-v4:24.2.1`


	注意：由于依赖的支持库会打包进apk，所以官方推荐开发者在编译时使用ProGuard工具预处理release版本的apk。ProGuard工具除了
	混淆源代码外，还会移除那些依赖的支持库中没有使用到的类，达到apk瘦身的效果。

[Android Support Library的前世今生 \- 简书](https://www.jianshu.com/p/f5f9a4fd22e8)