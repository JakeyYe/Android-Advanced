## JVM内存模型

### JVM内存模型分为

- 线程私有：程序计数器，虚拟机栈，本地方法栈；
- 共享数据区：堆（Heap），方法区（内部还有一个常量池）；

（Java内存粗略划分为栈和堆，栈是指虚拟机栈，堆是指Java堆（Heap））

- 程序计数器：是一块较小的内存空间，可以把它看作当前线程正在执行的字节码的行号指示器；
- Java虚拟机栈：是描述Java方法运行过程的内存模型；
- 本地方法栈：本地方法栈和Java虚拟机栈实现的功能类似，只不过本地方法栈是本地方法运行的内存模型；
- 堆：是用来存放对象的内存空间，几乎所有的对象都存储在堆中；
- 方法区：Java虚拟机规范中定义方法区是堆的一个逻辑部分，方法区中存放已经被虚拟机加载的类信息、常量、静态变量、即时编译期编译后的代码等；
- 运行时常量池：方法区中存放三种数据：类信息、常量、静态变量、即时编译期编译后的代码，其中常量存储在运行时常量池中；
![jvm内存模型](http://gityuan.com/images/jvm/jvm_memory_1.png)

### 堆内存是如何划分?

Java对象都在堆上创建，为了GC,堆内存分为三个部分，也可以说是三代，分别称为

1）新生代（young generation）：新生代又进一步分为Eden区，Survivor 1区和Survivor 2区；

2）老年代（Tenured/old generation）

3）永久代(perm area)：永久代有一些特殊，它用来存储类的元信息；

![堆内存\.png \(657×352\)](https://yemengying.com/qiniu/image/image/%E5%A0%86%E5%86%85%E5%AD%98.png)

参考：[【译】Java中的垃圾回收机制 \| Giraffe's Home](https://yemengying.com/2016/05/13/jvm-GC/)

### GC垃圾回收器常用算法

1，标记清除算法:将垃圾回收分为两个阶段：标记阶段和清除阶段；

2，复制算法

3，标记整理算法


### 注意点
1)作为一个Java开发者是不能强制JVM执行GC的，GC的触发由JVM依据堆内存的大小来决定；

2)System.gc()和Runtime.gc()会向JVM发送执行GC的请求，但是JVM不保证一定会执行GC;

[深入理解JVM\(一\)——JVM内存模型 \- CSDN博客](http://blog.csdn.net/u010425776/article/details/51170118)

[专栏：探索Java虚拟机 \- CSDN博客](http://blog.csdn.net/column/details/jvm-learn.html)

[Jvm内存模型 \- Gityuan博客 \| 袁辉辉博客](http://gityuan.com/2016/01/09/java-memory/)

[JVM 垃圾回收器工作原理及使用实例介绍](https://www.ibm.com/developerworks/cn/java/j-lo-JVMGarbageCollection/)