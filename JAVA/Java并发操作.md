## `Java`并发操作

[JAVA多线程和并发基础面试问答 \| 并发编程网 – ifeve\.com](http://ifeve.com/java-multi-threading-concurrency-interview-questions-with-answers/)

	Java并发操作：
	1，共享性：是指线程之间可以共享数据，这样就容易导致问题。
	2，互斥性：是指同时只允许一个访问者对其进行访问，具有唯一性和排它性。通常允许多个线程同时对数据进行读操作，但同一时间内只允许一个线程对数据进行写操作。通常将锁分为共享锁和排它锁，页叫做读锁和写锁。Java 中提供多种机制来保证互斥性，最简单的方式是使用Synchronized。
	3，原子性：就是对数据的操作是一个独立的，不可分割的整体。也就是一次操作，是一个连续不可中断的过程，数据不会被执行到一半时被其他线程所修改。保证原子性的最简单的方式就是操作系统指令，就是说如果一次操作对应一条操作系统指令，这样肯定能保证原子性，但是很多操作时不能通过一条指令就能完成的。
	4，可见性：就是保证线程访问的共享数据总是最新的，Java 中可通过Synchronized或Volatile来保证可见性
	5，顺序性：为了提高性能，编译器和处理器可能会对指令做重排序。
	

[Java并发编程：核心理论](https://mp.weixin.qq.com/s?__biz=MzIxNjA5MTM2MA==&mid=2652432605&idx=1&sn=e15d540a048756934b388db29d517532&scene=21#wechat_redirect)
	


### Synchroized关键字
当它用来修饰一个方法或者一个代码块时，能够保证在同一时刻最多只有一个线程执行该段代码。
#### Synchronized修饰的对象有一下几种：
- 修饰一个代码块，被修饰的代码块称为同步代码块，其作用的范围是大括号{}括起来的代码，作用的对象是调用这个代码块的对象。

	`synchronized(this){...}`

- 修饰一个方法，被修饰的方法称为同步方法，其作用范围是整个方法，作用的对象是调用该方法的对象。

	`public synchronized void test(){...}`

- 修饰一个静态的方法，其作用范围是整个静态方法，作用的对象是这个类的所有对象，它取得的锁是对象。

	`public synchronized static void test(){..}`
- 修饰一个类，其作用的范围是synchronized后面括号括起来的部分，作用的对象是这个类的所有对象，它取得的锁是对类的，该类所有对象共用同一把锁。

	`synchronized(TestClass.class){...}`



### Volatile关键字

	多线程的内存模型：main memory(主存)、working memory（线程栈），在处理数据时，线程会把值从主存load到本地栈，完成操作后再save回去，而volatiled关键字的作用就是，每次针对该变量的操
	作，都会激发一次load and save。
[Java中的多线程你只要看这一篇就够了 \- ImportNew](http://www.importnew.com/21089.html)

volatile能够保证可见性，但是不能保证原子性。它只能作用于变量，不能作用于方法。

volatile变量通常用做某个操作完成，发生中断或者状态的标识。

volatile与加锁机制的主要区别时：加锁机制既可以确保可见性又可以确保原子性，而volatile变量只有确保可见性。


### synchronized与Volatile
1,volatile只能修饰变量，而synchronized可以修饰变量，方法以及代码块。

2，volatile在多线程中不会存在阻塞问题，而synchronized会存在阻塞问题。

3，volatile能保证数据的可见性，但不能保证数据的原子性，synchronized既能保证数据的可见性，又能保证数据的原子性。

4，volatile解决的是变量在多线程之间的可见性，而synchronized解决的是多个线程之间访问资源的同步性。

### 参考 [Java中Synchronized的用法](http://blog.csdn.net/luoweifu/article/details/46613015)
###[volatile](http://www.cnblogs.com/MOBIN/p/5407965.html)



## [原子性 可见性 有序性](https://my.oschina.net/wangnian/blog/668490)

## [为什么volatile不能保证原子性而Atomic可以？](http://www.cnblogs.com/Mainz/p/3556430.html)


### java.util.concurrent.atomic包  原子操作,支持在单个变量上解除锁的线程安全编程。

### java.util.concurrent.locks 为锁和等待条件提供一个框架的接口和类
	Lock和synchronized
[Java并发编程：Lock \- 海 子 \- 博客园](http://www.cnblogs.com/dolphin0520/p/3923167.html)

### CountDownLatch是一种简单的同步模式，它可以让一个或多个线程等待完成它们的工作从而避免对临界资源并发访问引发的问题。

### ConcurrentHashMap是HashMap在并发环境下的版本

### CopyOnWriteArrayList是ArrayList在并发环境下的替代品

### CopyOnWriteArraySet是ArraySet在并发环境下的替代品

### BlockingQueue是并发环境下的Queue,Java7中引入了TransferQueue,它比BlockingQueue多一个transfer的方法，如果接收线程处于等待状态，该操作可以马上将任务交给它，否则就会阻塞直至取走该任务的线程出现。可以用TransferQueue代替BlockingQueue，因为它可以获得更好的性能。

### CountDownLatch倒计时锁（Java并发系列）
	CountDownLatch是一个同步辅助类，允许一个或多个线程等待直到在其他线程中执行的一组操作完成的同步辅助。
	CountDownLatch是通过“共享锁”实现的。
	CyclicBarrier则是允许N个线程相互等待。
	CountDownLatch的计数器是无法被重置的，CyclicBarrier的计数器可以被重置后使用，因此被称为是循环的barrier.

[什么时候使用CountDownLatch](http://www.importnew.com/15731.html)

[CountDownLatch](http://www.cnblogs.com/skywang12345/p/3533887.html)


#### [Java多线程系列目录](http://www.cnblogs.com/skywang12345/p/java_threads_category.html)
