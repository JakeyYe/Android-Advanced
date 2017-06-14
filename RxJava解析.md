##RxJava函数响应式编程
###RxAndroid是RxJava的增强版，是针对Android专门设计的。

	实现异步操作的库，RxJava - 用于构成使用Java VM的观察序列异步和基于事件的程序库 - 为JVM反应扩展。
	RxJava最核心的两个东西是Observables(被观察者，事件源)和Subscribers(观察者)。Observables发出一系列事件，Subscribers处理这些事件。
	
	RxJava的异步实现，是通过一种扩展的观察者模式来实现的，RxJava作为一个工具库，使用的就是通用形式的观察者模式（相对对
	应的是专用观察者模式，例如只用于监听控件点击的）。

RxJava四个基本概念：

`Observable`:可观察者，即被观察者

`Observer`:观察者

`Subscriber` :`RxJava`内置的一个实现了`Observer`的抽象类，`Subscriber`对`Observer`接口进行了一些扩展，是继承自`Observer`的，但它们的基本使用方式是一样的。

`subscribe`:订阅方法 ，`Observable`和`Observer`通过该方法实现订阅关系,从而`Observable`可以在需要的时候发出事件来通知`Observer`。

`Scheduler`:调度器，线程控制器，`RxJava`通过它来指定每一段代码应该运行在什么样的线程里。`RxJava`内置了几个`Scheduler`。通过设置调度器`subscribeOn(Scheduler.io())` 和 `observeOn(AndroidSchedulers.mainThread())` 实现 “后台线程取数据，主线程显示”的程序策略。
 
*响应式代码的基本组成部分是Observable和Subscriber(事实上Observer才是最小的构建快，在实践中使用最多的是Subscriber),Observable发送消息，Subscribers用于消费消息。*

###RxJava内置Scheduler，使用Scheduler管理线程
- Schedulers.immediate(): 直接在当前线程运行，相当于不指定线程。这是默认的 Scheduler。
- Schedulers.newThread(): 总是启用新线程，并在新线程执行操作。
- Schedulers.io(): I/O 操作（读写文件、读写数据库、网络信息交互等）所使用的 Scheduler。行为模式和 newThread() 差不多，区别在于 io() 的内部实现是是用一个无数量上限的线程池，可以重用空闲的线程，因此多数情况下 io() 比 newThread() 更有效率。不要把计算工作放在 io() 中，可以避免创建不必要的线程。
- Schedulers.computation(): 计算所使用的 Scheduler。这个计算指的是 CPU 密集型计算，即不会被 I/O 等操作限制性能的操作，例如图形的计算。这个 Scheduler 使用的固定的线程池，大小为 CPU 核数。不要把 I/O 操作放在 computation() 中，否则 I/O 操作的等待时间会浪费 CPU。
- 另外， Android 还有一个专用的 AndroidSchedulers.mainThread()，它指定的操作将在 Android 主线程运行

###Operators,RxJava操作符
Operators在消息发送者Observable和消息消费者Subscriber之间起动操纵消息的作用。RxJava拥有大量的operators.

比如map() operator可以将已被发送的消息转换成另外一种形式。

Observable和Subscribers与它们之间的一系列转换步骤是相互独立的。

`filter()`方法是进行过滤操作的方法，`filter()`方法返回false的值将不会发出到`subscriber`。


###使用RxAndroid添加依赖：

	compile 'io.reactivex:rxandroid:1.2.0'
	compile 'io.reactivex:rxjava:1.1.5'

[给Android开发者的RxJava详解](https://gank.io/post/560e15be2dca930e00da1083)

[RxJava Essentials 中文翻译版（已下载）]( https://rxjava.yuxingxin.com/)

[某学姐博客](http://mouxuejie.com/blog/2016-03-27/rxjava-basis/)