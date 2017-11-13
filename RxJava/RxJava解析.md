## RxJava函数响应式编程
### RxAndroid是RxJava的增强版，是针对Android专门设计的。

	实现异步操作的库，RxJava - 用于构成使用Java VM的观察序列异步和基于事件的程序库 - 为JVM反应扩展。
	RxJava最核心的两个东西是Observables(被观察者，事件源)和Subscribers(观察者)。Observables发出一系列事件，Subscribers处理这些事件。
	
	RxJava的异步实现，是通过一种扩展的观察者模式来实现的，RxJava作为一个工具库，使用的就是通用形式的观察者模式（相对对
	应的是专用观察者模式，例如只用于监听控件点击的）。

	RxJava异步处理，能够自如地切换线程，利用subscribeOn()和observeOn()来实现线程控制，让事件的产生和消费发生在指定的线程中。

[用一张图解释RxJava中的线程控制 \- 泡在网上的日子](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2016/0510/4249.html)

![1462844481168297\.png \(1126×676\)](http:/www.jcodecraeer.com/uploads/20160510/1462844481168297.png)

RxJava四个基本概念：

`Observable`:可观察者，即被观察者

`Observer`:观察者

`Subscriber` :`RxJava`内置的一个实现了`Observer`的抽象类，`Subscriber`对`Observer`接口进行了一些扩展，是继承自`Observer`的，但它们的基本使用方式是一样的。

`subscribe`:订阅方法 ，`Observable`和`Observer`通过该方法实现订阅关系,从而`Observable`可以在需要的时候发出事件来通知`Observer`。

`Scheduler`:调度器，线程控制器，`RxJava`通过它来指定每一段代码应该运行在什么样的线程里。`RxJava`内置了几个`Scheduler`。通过设置调度器`subscribeOn(Scheduler.io())` 和 `observeOn(AndroidSchedulers.mainThread())` 实现 “后台线程取数据，主线程显示”的程序策略。
 
- subscribeOn（）它指示Observable在一个指定的调度器上创建（只作用于被观察者创建阶段）。只能指定一次，如果指定多次则以第一次为准，也就是用来指定Observable.create中的代码在那个Scheduler中执行。
- observeOn（）指定在事件传递（加工变换）和最终被处理（观察者）的发生在哪一个调度器。可指定多次，每次指定完都在下一步生效。
- unsubscribeOn:有些Observable会依赖一些资源，当该Observable完成后释放这些资源。如果释放资源比较耗时的话，可以通过unsubscribeOn来释放资源代码执行的线程。

**subscribeOn()作用的是ObservableOnSubscribe,observeOn()作用 的是Observer或Subscriber**

**响应式代码的基本组成部分是Observable和Subscriber(事实上Observer才是最小的构建快，在实践中使用最多的是Subscriber),Observable发送消息，Subscribers用于消费消息。**

### RxJava内置Scheduler，使用Scheduler管理线程
- Schedulers.immediate(): 直接在当前线程运行，相当于不指定线程。这是默认的 Scheduler。
- Schedulers.newThread(): 总是启用新线程，并在新线程执行操作。
- Schedulers.io(): I/O 操作（读写文件、读写数据库、网络信息交互等）所使用的 Scheduler。行为模式和 newThread() 差不多，区别在于 io() 的内部实现是是用一个无数量上限的线程池，可以重用空闲的线程，因此多数情况下 io() 比 newThread() 更有效率。不要把计算工作放在 io() 中，可以避免创建不必要的线程。
- Schedulers.computation(): 计算所使用的 Scheduler。这个计算指的是 CPU 密集型计算，即不会被 I/O 等操作限制性能的操作，例如图形的计算。这个 Scheduler 使用的固定的线程池，大小为 CPU 核数。不要把 I/O 操作放在 computation() 中，否则 I/O 操作的等待时间会浪费 CPU。
- 另外， Android 还有一个专用的 AndroidSchedulers.mainThread()，它指定的操作将在 Android 主线程运行

### Operators,RxJava操作符-针对事件序列的处理和再发送
Operators在消息发送者Observable和消息消费者Subscriber之间起动操纵消息的作用。RxJava拥有大量的operators.

比如map() operator可以将已被发送的消息转换成另外一种形式。

Observable和Subscribers与它们之间的一系列转换步骤是相互独立的。

`filter()`方法是进行过滤操作的方法，`filter()`方法返回false的值将不会发出到`subscriber`。


### 使用RxAndroid添加依赖：

	compile 'io.reactivex:rxandroid:1.2.0'
	compile 'io.reactivex:rxjava:1.1.5'

#### 当使用RxJava形式的Retrofit时，Retrofit把请求封装进Observable中

[给Android开发者的RxJava详解](https://gank.io/post/560e15be2dca930e00da1083)

[RxJava Essentials 中文翻译版（已下载）]( https://rxjava.yuxingxin.com/)

[某学姐博客](http://mouxuejie.com/blog/2016-03-27/rxjava-basis/)

[一起来造一个RxJava，揭秘RxJava的实现原理 \- TellH的博客 \- CSDN博客](http://blog.csdn.net/tellh/article/details/71534704)
