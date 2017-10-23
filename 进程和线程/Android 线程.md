# 多线程
[JAVA多线程和并发基础面试问答 \| 并发编程网 – ifeve\.com](http://ifeve.com/java-multi-threading-concurrency-interview-questions-with-answers/)
## Android中的线程使用

### 应用启动时会创建一个名为“主线程（UI线程）”的执行线程，词线程非常重要，因为它负责将事件分配给相应的用户界面小组件，其中包括绘图事件。此外，它也是应用与Android UI工具包组件（android.widget和android.view包中的组件）进行交互的线程，因此它也被称为“UI线程”。

### 运行在同一进程的所有组件均在UI组件中实例化，并且对每个组件的系统调用均由该线程进程分派。

### Android UI工具包并非线程安全工具包，因此，不能通过工作线程来操作UI，而只能通过UI线程操作用户界面，因此，Android的单线程模式必须遵守两条规则：

  1)，不要阻塞UI线程

  2)，不要在UI线程之外访问Android UI工具包中的组件

### Android提供了几种途径来从其他线程访问UI线程的方法：

  1).`Activity.runOnUiThread(Runnable)`

  2).`View.post(Runnable)`

  3).`View.postDelayed(Runnable,long)`

## Java多线程
	Java中，可运行的程序都是又一个或多个进程组成的。进程则是由多个线程组成的。最简单的一个进程，会包括main线程以及GC线程。

### 线程的6种状态(根据Thread.State来看的)
- NEW：至今尚未启动的线程处于这种状态；
- RUNNABLE：正在Java虚拟机中执行的线程处于这个状态；
- BLOCKED：受阻塞并等待某个监听器锁的线程处于这种状态；
- WAITING：无限期地等待另一个线程来执行某一特定操作的线程处于这种状态；
- TIMED_WAITING：等待另一个线程来执行取决于指定等待时间的操作的线程处于这种状态；
- TERMINATED：已退出的线程处于这种状态。

一个线程可以在一个给定的时间点上只能有一个状态。这些状态是不反映任何操作系统线程状态的虚拟机状态。

![线程状态](http://incdn1.b0.upaiyun.com/2016/08/665f644e43731ff9db3d341da5c827e1.png)

![线程状态转换图](http://img.blog.csdn.net/20160425000221919?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

	另一种关于Thread状态的说法：
	New（创建状态）,Runnable（就绪状态）,Running（运行状态）,Blocked/Waiting（阻塞/等待）,Dead(结束)

![](https://cdn.journaldev.com/wp-content/uploads/2012/12/Thread-Lifecycle-States.png)

[Thread Life Cycle in Java \- Thread States in Java \- JournalDev](https://www.journaldev.com/1044/thread-life-cycle-in-java-thread-states-in-java)
### 关键概念-并发，并行，同步，异步
- 并发
- 并行
- 同步
- 异步


[Java中的多线程你只要看这一篇就够了 \- ImportNew](http://www.importnew.com/21089.html)



### Thread比较难理解的方法

- join():该方法的作用是把A.join()所对应的线程A加入到调用该方法的线程B中运行，可以将两个交替执行的线程合并为顺序执行的线程；
- join(long millis):该方法的作用是线程B至等待millis毫秒，而不管线程A是否运行完成；
[Java多线程中join方法的理解 \- 每天进步一点点！ \- ITeye博客](http://uule.iteye.com/blog/1101994)
- notify:唤醒在此对象监视器上等待的单个线程；
- notifyAll:唤醒在此对象监视器上等待的所有线程；
- wait：在其他线程调用此对象的 notify() 方法或 notifyAll() 方法前，导致当前线程等待。换句话说，此方法的行为就好像它仅执行 wait(0) 调用一样；
- yield：暂停当前正在执行的线程对象，并执行其他线程；
- sleep:暂指定的毫秒数内让当前正在执行的线程休眠（暂停执行）

### Thread同步锁
	
	同步锁就是synchronized

	在JDK 5中，Java又引入了一个相似的概念Lock,锁，功能与synchronized是类似的。(详情参看《Java并发操作》)

### Java中的守护线程和非守护线程
	User和Daemond两者几乎没有区别，唯一的不同之处就在于虚拟机的离开：如果User Thread已经全部退出运行了，只剩下Daemon Thread存在了，虚拟机也就退出了，因为没有了被守护者，Daemon也就没有工作可做了，也就没有继续运行程序的必要了。

	JRE判断程序是否执行结束的标准是所有的用户线程执行完毕，而不管守护线程是否执行完毕。

User Thread(用户线程)
Daemon Thread(守护线程)
	用个比较通俗的比喻，任何一个守护线程都是整个JVM中的所有非守护线程的保姆；
	一个守护线程是在后天执行并且不会阻止JVM终止的线程，一个守护线程创建的子线程依然是守护线程；
	守护线程最典型的应用就是GC(垃圾回收器)，它就是一个很称职的守护者；


### Future/FutrueTask
	Future接口，它表示异步计算的结果。它提供了检查计算是否完成的方法，以等待计算的完成，并获取计算的结果。
	
	FutureTask是Future的一个基础实现，我们可以将它同Executors使用处理异步任务；
	FutureTask类是Future的一个具体实现类，Future可实现Runnable，所以可通过Executor来执行；
		FutureTask<String> future =
        new FutureTask<String>(new Callable<String>() {
         public String call() {
           return searcher.search(target);
        }});
        executor.execute(future);

	Callable也就相当于Runnable；
	Callable接口使用泛型去定义它的返回类型，它和Runnable接口很相似，但是它可以返回一个泛型定义类型的对象或者抛出一个异常；
	在线程池提交Callable任务后返回一个Futrure对象，使用它我们可以知道Callable任务的状态和得到Callable返回的执行结果，Future提供了get()方法让我们可以等待Callable结束并获取它的执行结果。
[Java Callable Future Example \- JournalDev](https://www.journaldev.com/1090/java-callable-future-example)

[Java中的Runnable、Callable、Future、FutureTask的区别与示例 \- Mr\.Simple的专栏 \- CSDN博客](http://blog.csdn.net/bboyfeiyu/article/details/24851847)