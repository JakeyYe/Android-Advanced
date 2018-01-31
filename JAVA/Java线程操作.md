## Java线程操作

#### [Java中的Runnable、Callable、Future、FutureTask的区别与示例 \- CSDN博客](http://blog.csdn.net/bboyfeiyu/article/details/24851847)

#### [Java多线程实现的四种方式](http://www.voidcn.com/blog/x2145637/article/p-6506536.html)

#### [Java多线程](http://www.jianshu.com/p/0408cb633bc4)

#### [多线程知识点总结 \| XBlog](http://www.xkjchen.com/uncategorized/2016/06/21/Thread_Summary/)

### Thread的终止操作的两种方式：

1. 标记位
1. Thread.interrupt()

实际上，在Thread的sleep和Object的wait方法的底层实现中，都会检测interrupt标记位，当发现该标记位为true时会抛出InterruptedException异常（当线程在活动之前或活动期间处于正在等待、休眠或占用状态且该线程被中断时，抛出该异常），因此当调用sleep和wait方法时都需要捕获并处理InterruptedException,且可以在catch到该异常后停止自己，从而达到终止阻塞中的线程的目的；

[Android java 中如何优雅的结束线程 \- 废墟的树的专栏 \- CSDN博客](http://blog.csdn.net/feiduclear_up/article/details/43270375)


### Thread 的暂停和继续操作

关键点时 Object.wait()和Object.notify()（Object.notifyAll()）方法，Object.wait()方法可使调用该方法的线程处于等待状态，Object.notify()方法可唤醒处于"wait"状态的线程；

[Java 线程暂停与继续 \- CSDN博客](http://blog.csdn.net/sdojqy1122/article/details/7256531)