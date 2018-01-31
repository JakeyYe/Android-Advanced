#`Android项目架构模式`

	MVP把Activity中的UI逻辑抽象成View接口，把业务逻辑抽象成Presenter接口，Model类还是原来的Model。

###1.`MVP`,M代表`Model`，V代表`View`，P代表`Presenter`。`Model`一部分是处理业务逻辑，一部分是提供`View`显示的数据。`View`代表的是一个接口，一个将UI界面提炼而抽象出来的接口。`Presenter`是`Model`和`View`之间的桥梁。

	在MVP模式里通常包含4各元素：
    1）View:负责绘制UI元素，与用户进行交互（在Android中体现为Activity/Fragment）；
	2）View interface:需要View实现的接口，View通过View interface与Presenter进行交互，降低耦合，方便进行单元测试；
	3）Model:负责存储，检索，操作数据（有时也实现一个Model interface用来降低耦合）；
	4）Presenter：作为View与Model交互的中间纽带，负责处理与用户交互的逻辑。

	MVP使用技巧
	1，Presenter创建基类，利用复用，减少类体积。
	2，View接口，抽离出常用的View功能，例如加载，利用接口组合减少View接口类暴涨。

![MVP模式的使用](https://sfault-image.b0.upaiyun.com/376/202/3762022390-56fde71603d5d_articlex "MVP模式的使用")
上面一张简单的MVP模式的UML图，从图中可以看出，使用MVP，至少需要经历以下步骤：

创建IPresenter接口，把所有业务逻辑的接口都放在这里，并创建它的实现PresenterCompl（在这里可以方便地查看业务功能，由于接口可以有多种实现所以也方便写单元测试）
创建IView接口，把所有视图逻辑的接口都放在这里，其实现类是当前的Activity/Fragment
由UML图可以看出，Activity里包含了一个IPresenter，而PresenterCompl里又包含了一个IView并且依赖了Model。Activity里只保留对IPresenter的调用，其它工作全部留到PresenterCompl中实现
Model并不是必须有的，但是一定会有View和Presenter。

[Android MVP模式 简单易懂的介绍方式 \- 中二病也要开发ANDROID \- SegmentFault](https://segmentfault.com/a/1190000003927200)

**感觉MVP架构模式是有逻辑可循的，是一套有着基本标准的架构模式，所以完全可以模仿着模式一步步来码代码，是有迹可循的。**

参考 [在Android开发中使用MVP模式](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0202/2397.html)

### MVP模式的好处
	
- 分离了视图逻辑和业务逻辑，降低了耦合
- Activity只处理生命周期的任务，代码变得更加简洁
- 视图逻辑和业务逻辑分别抽象到了View和Presenter的接口中去，提高代码的可阅读性
- Presenter被抽象成接口，可以有多种具体的实现，所以方便进行单元测试
- 把业务逻辑抽到Presenter中去，避免后台线程引用着Activity，导致Activity的资源无法被系统回收从而引起内存泄漏和OOM。
	