## Android内存泄漏情况记录
	使用LeakCanary来检测内存泄漏

	性能优化中的一步：内存泄漏优化。

	强引用，软引用，弱引用，虚引用
	（Java中的引用，类似于C++的指针，通过引用，可以对堆中的对象进行操作，例如，在某个函数中，当创建了一个对象，该对象被分配在堆中，
	通过这个对象的引用才能对这个对象进行操作）。
	栈空间----》堆空间
	1,强引用：强引用可以直接访问目标对象，强引用在任何时候都不会被系统回收，JVM宁愿抛出OOM异常，也不会回收强引用所指向的对象，强引用所以可能会导致内存泄漏；
	2，软引用：可以使用java.lang.ref.SoftReference使用软引用，如果一个对象只有软引用指向时，只有当系统内存不足时，系统才会回收该软引用；
	3，弱引用：WeakReference,在系统GC时，只要发现弱引用，不管系统堆空间是否足够，都会将对象进行回收。（弱引用使用案例WeakHashMap）
	4，虚引用：PhantomReference一个持有虚引用的对象，和没有引用几乎是一样的，随时都可能被垃圾回收器回收，必须结合ReferenceQueue一起使用。

注意：

- 何时使用软引用，何时使用弱引用？[Android性能提升之强引用、软引用、弱引用、虚引用使用 \- 逆流的鱼yuiop \- CSDN博客](http://blog.csdn.net/hejjunlin/article/details/52637333)
- 软引用，弱引用都非常适合用来保存那些可有可无的缓存数据，这样做，当系统内存不足时，这些缓存数据就会被回收，不会导致内存溢出，而当内存资源充足时，这些缓存数据又可以存在相当长的时间。
- ReferenceQueue类表示引用队列，它可以和这三种引用类联合使用，以便跟踪Java虚拟机回收所引用的对象的活动，当这些引用对象被回收，Java虚拟机就会把这些引用加入到与之关联的引用队列中去。

[Java中堆内存和栈内存详解 \- 蛊惑Into \- 博客园](http://www.cnblogs.com/whgw/archive/2011/09/29/2194997.html)

### Android内存泄漏情形记录

- 非静态内部类持有外部类的实例，如Handler,Runnable，AsyncTask持有外部类（如Activity）的引用
- 静态变量导致的内存泄漏
- 单例模式导致的内存泄漏
- 线程造成的内存泄漏，如Activity中的线程一直运行，而Activity已经销毁了，这个时候也要将线程关闭，否则可能造成内存泄漏；
（Executor框架提供了Java线程池的能力，ExecutorService扩展了Exector提供了管理线程生命周期的关键能力，线程池的shutdownNow()会尝试停止池内所有在执行的线程，原理也是发出中断请求，通过线程池来结束线程；使用标识位来结束线程）
- 属性动画导致内存泄漏（主要是属性动画中的无限循环播放，解决方法：在适当的时机调用Animator.cancel()方法）
- Dialog导致的内存泄漏，在当前Dialog所依附的Activity销毁之前，没有将当前的Dialog销毁（dismiss）的话，会导致内存泄漏
- 使用资源文件结束后未关闭，在使用一些资源性对象比如(Cursor，File，Stream，ContentProvider，Sensor传感器等)往往都用了一些缓冲，我们在不使用的时候，应该及时关闭它们，以便它们的缓冲及时回收内存。它们的缓冲不仅存在于Java虚拟机内，还存在于Java虚拟机外。如果我们仅仅是把它的引用设置为null,而不关闭它们，往往会造成内存泄露--注册与解注册

[LearningNotes/Android内存泄漏总结\.md at master · francistao/LearningNotes](https://github.com/francistao/LearningNotes/blob/master/Part1/Android/Android%E5%86%85%E5%AD%98%E6%B3%84%E6%BC%8F%E6%80%BB%E7%BB%93.md)
