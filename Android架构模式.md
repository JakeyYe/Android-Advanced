#`Android项目架构模式`

###1.`MVP`,M代表`Model`，V代表`View`，P代表`Presenter`。`Model`一部分是处理业务逻辑，一部分是提供`View`显示的数据。`View`代表的是一个接口，一个将UI界面提炼而抽象出来的接口。`Presenter`是`Model`和`View`之间的桥梁。

	在MVP模式里通常包含4各元素：
    1）View:负责绘制UI元素，与用户进行交互（在Android中体现为Activity）；
	2）View interface:需要View实线的接口，View通过View interface与Presenter进行交互，降低耦合，方便进行单元测试；
	3）Model:负责存储，检索，操作数据（有时也实现一个Model interface用来降低耦合）；
	4）Presenter：作为View与Model交互的中间纽带，负责处理与用户交互的逻辑。
参考 [在Android开发中使用MVP模式](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2015/0202/2397.html)