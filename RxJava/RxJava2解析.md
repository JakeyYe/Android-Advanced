## RxJava2

[RxJava2 学习资料推荐](https://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650823932&idx=1&sn=198b18f2f9359e2eee1ffc8703d31905&chksm=80b78862b7c001741916c681d070ca3c1a58eef5632ea394797029d0335f312816afecf87e7d&mpshare=1&scene=1&srcid=0920pW30MFTgeQRTXaU1XVHo&pass_ticket=uMLfEXNPeBmNUcqpUjh7OOK0zDtImVzpV57XXtqVcvfn4qBdjiTIHoKa9HgQdfs%2F#rd)

	RxJava1和RxJava2的核心思想是没有变化的，只不过RxJava2更新了一些新东西。

**在RxJava 2 中，内置了几个线程选项：**

- Schedulers.io()代表io操作的线程，通常用于网络，读写文件等io密集型的操作；
- Schedules.computation()代表CPU计算密集型的操作，例如需要大量计算的操作；
- Schedules.newThread()代表一个常规的新线程；

**RxAndroid 提供的线程选项：**

- AndroidSchedulers.mainThread()代表Android的主线程。

在RxJava内部使用的是线程池来维护这些线程，所以效率也挺高的。

**RxJava 2 中的Observable和Flowable**

在2.x版本定义Flowable来表示可背压的数据源，而Observable则表示不能背压的数据源。

Flowable的功能与Observable大致相同，但有一个主要区别：Observer请求多少数据，Flowable就发射多少数据。如果你有一个Observable比它指定的Observer发射更多的数据，那么就可以考虑切换到Flowable。

**RxJava2是如何实现操作符的呢？**

其实，每调用一次操作符的方法，就相当于在上层数据源和下层观察者之间桥接了一个新的Observable；桥接的Observable内部会实例化有新的ObservableOnSubscribe和Observer，ObservableOnSubscribe负责发送数据源，Observer负责处理数据源。

### Operator操作符
	map:是一个变换操作符，它的作用就是对上游发来的每一个事件应用一个函数，使得每一个事件都按照指定的函数去变化。
	flatMap:就是把一个T类型对象转换为另一个Observable<R>,但是发送并不一定按照原来的顺序。
	concatMap:和flatMap的作用是一样的，但是发送顺序是原来的发送顺序。
	zip:将两种Observable进行合并操作再传递给下游，其中的两种Observable会按顺序进行合并；
	filter:过滤操作符；
	sample:sample取样，这个操作符每隔指定的时间就从上游中取出一个事件发送给下游；
	Backpressure:背压，上游发送事件太快了，而下游又处理不及，导致存储上游事件的队列满了，这样可能会发生OOM;

### 重要点

- subscribeOn()是用来指定Observable运行所在的线程的，**多次调用subscribeOn()方法，只有第一次有效，只会使用最接近源Observable的那个，其余的都会被忽略**。
- observeOn()是用来指定Observer运行所在的线程的，多次调用，都会随着切换线程，**所以是最接近 Observer 的那个才会有效**。
- doOnNext()方法是在Observer.onNext()方法之前被调用的。
- Func1和Action1的异同点：都是继承自Function接口，两个接口中都是只有一个call方法，不同点是Func1是有返回值的，而Action1是没有返回值的；Func系列和Action系列都是这样的特点。
- 当Android系统尝试销毁包含正在运行的Observable的Activity时会发生内存泄漏，所在在Activity/Fragment销毁前，要停止内部的Observable的运行，停止不是取消订阅，因为即时取消订阅Observable还是继续发送事件，只不过Observer接收不到而已，还是会持有引用，而是要终止序列，RxLifecycle库是通过发出onComplete()或onError()方法终止Observable序列的；

[amitshekhariitbhu/RxJava2\-Android\-Samples: RxJava 2 Android Examples \- Migration From RxJava 1 to RxJava 2 \- How to use RxJava 2 in Android](https://github.com/amitshekhariitbhu/RxJava2-Android-Samples)


	Observable.create(new ObservableOnSubscribe<T>(){
       public void subscribe(ObservableEmitter<T> emitter) throws Exception{

       }
	})
	.subscribeOn()
	.doOnSubscribe(){//可通过后面的subscribeOn()指定运行的线程

	}
	.subscribeOn()
	.observableOn()
	.subscribe(new Observer<T>(){

	});