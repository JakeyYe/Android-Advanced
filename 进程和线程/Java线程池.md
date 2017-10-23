## Java线程池

### 线程池关键类：

Executor、ExecutorService线程池操作接口；

AbstractExecutorService继承自ExecutorService的线程池操作抽象类；

ThreadPoolExecutor继承自AbstractExecutorService抽象类的线程池具体实现类；

Executors线程池工厂类，可以很方便地创建几种类型的线程池对象；


### 线程池启动策略：

1、线程池刚创建时，里面没有一个线程。任务队列是作为参数传进来的。不过，就算队列里面有任务，线程池也不会马上执行它们。

2、当调用execute() 方法添加一个任务时，线程池会做如下判断：

	a. 如果正在运行的线程数量小于corePoolSize，那么马上创建线程运行这个任务；

	b. 如果正在运行的线程数量大于或等于corePoolSize，那么将这个任务放入队列。

	c. 如果这时候队列满了，而且正在运行的线程数量小于maximumPoolSize，那么还是要创建线程运行这个任务；

	d. 如果队列满了，而且正在运行的线程数量大于或等于maximumPoolSize，那么线程池会抛出异常，告诉调用者“我不能再接受任务了”。

3、当一个线程完成任务时，它会从队列中取下一个任务来执行。

4、当一个线程无事可做，超过一定的时间（keepAliveTime）时，线程池会判断，如果当前运行的线程数大于corePoolSize，那么这个线程就被停掉。所以线程池的所有任务完成后，它最终会收缩到corePoolSize 的大小。

![线程池的处理流程](http://img.blog.csdn.net/20151222073427030?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)