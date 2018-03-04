## RxJava2 看源码

看源码看Sample [amitshekhariitbhu/RxJava2\-Android\-Samples: RxJava 2 Android Examples \- Migration From RxJava 1 to RxJava 2 \- How to use RxJava 2 in Android](https://github.com/amitshekhariitbhu/RxJava2-Android-Samples)

RxJava 函数响应式编程[Rxjava2入门教程一：函数响应式编程及概述 \- 简书](https://www.jianshu.com/p/15b2f3d7141a)

1，CompositeDisposable.clear()和dispose()方法的区别：

	clear()和dispose()方法的作用都是dispose在CompositeDisposable集合中的所有Disposable对象，但是调用dispose()方法后会使CompositeDisposable.add()方法不能再添
	加Disposable对象，该方法会返回false；

2，Observable和Flowable

![v2\-b6a6da8d2b90129984268ff5db4e9ebb\_hd\.jpg \(720×882\)](https://pic3.zhimg.com/80/v2-b6a6da8d2b90129984268ff5db4e9ebb_hd.jpg)

3，RxJava 2中提供的几对观察者模式

1. Observable/Observer：基本的观察则和被观察者；

2. Single/SingleObserver：Single只能发射一个单一数据通知或者一个错误通知，不能发射完成通知；看SingleObserver接口中的方法即可；

3. Completable/CompletableObserver：只发射一个完成通知，或者一个异常通知，不能发射数据，其中完成通知与异常通知只能发射一个；看CompletableObserver接口中的方法即可；

4. Maybe/MaybeObserver：可发射一个单一数据（发射多个只有第一个有效），或者发射一个完成通知，或者一个异常通知，这三个只能发射其中一个，**从概念来说，它是Single和Completable的结合体**；看MaybeObserver接口中的方法即可；

[Rxjava2入门教程一：函数响应式编程及概述 \- 简书](https://www.jianshu.com/p/15b2f3d7141a)

[Rxjava2入门教程六：Single、Completable、Maybe——简化版的Obse\.\.\. \- 简书](https://www.jianshu.com/p/66a55abbadef)

4，Flowable

Flowable的异步缓冲池不同于Observable，Observable的异步缓存没有大小限制，可以无限制向里添加数据，直至OOM，二Flowable的异步缓冲池有个固定容量，其大小为128；

BackpressureStrategy的作用便是用来设置Floawable通过异步缓冲池存储数据的策略；
[Rxjava2入门教程五：Flowable背压支持——几乎可以说是对Flowable最全面而详\.\.\. \- 简书](https://www.jianshu.com/p/ff8167c1d191)

5，RxJava 2 中的Subject和Processor

Subject既是Observable又是Observer，官网称Subject可以看出一个桥梁或者代理；
Subject包含四种类型分别是AsyncSubject、BehaviorSubject、ReplaySubject和PublishSubject；

Processor是reactive-streams中的一个接口继承自Subscriber和Publisher，和Subject相似，也有Subjet相似的四种类型，AsyncProcessor、BehaviorProcessor、ReplayProcessor和PublishProcessor，和Subject四种类型的区别是，Subject的不支持背压，而Processor的支持背压；

	io.reactivex.subjects.AsyncSubject,
	io.reactivex.subjects.BehaviorSubject,
	io.reactivex.subjects.PublishSubject,
	io.reactivex.subjects.ReplaySubject

	io.reactivex.processors.AsyncProcessor,
	io.reactivex.processors.BehaviorProcessor,
	io.reactivex.processors.PublishProcessor,
	io.reactivex.processors.ReplayProcessor

[RxJava 的 Subject \- 简书](https://www.jianshu.com/p/99bd603881bf)

6，RxJava 2 设置全局性的异常捕获器

	static {
        RxJavaPlugins.setErrorHandler(new Consumer<Throwable>() {
            @Override
            public void accept(Throwable throwable) throws Exception {
                //捕获ObservableOnSubscribe这类接口中的subscribe方法抛出的异常
                //如果不设置这个，将会把错误直接抛出，这样Activity将会直接退出
                Log.d(TAG, "accept: throwable ");
            }
        });
    }