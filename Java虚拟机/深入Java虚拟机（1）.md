## 深入Java虚拟机（1）

[理解Android虚拟机体系结构 \- 安卓 \- 伯乐在线](http://android.jobbole.com/82413/)

[深入学习Android：虚拟机&运行时 \- 知乎专栏](https://zhuanlan.zhihu.com/p/24414378)

[Android ART运行时无缝替换Dalvik虚拟机的过程分析 \- CSDN博客](http://blog.csdn.net/luoshengyang/article/details/18006645)
#### JVM的内部体系结构分为三部分
	
1）类加载器（ClassLoader）子系统

 作用：用来装载.class文件，装载又分为三个步骤：装载，链接，初始化

2）执行引擎

 作用：执行字节码，或者执行本地方法

3）运行时数据区

 方法区，堆，java栈，PC寄存器，本地方法栈

[JVM 的 工作原理，层次结构 以及 GC工作原理 \- 我们俩 \- SegmentFault](https://segmentfault.com/a/1190000002579346)

#### JVM内存区域(JVM内存模型)
Java虚拟机在执行Java程序的过程中会把他所管理的内存划分为若干个不同的数据区域。Java虚拟机规范将JVM所管理的内存分为一下几个运行时数据区：程序计数器、本地方法栈、Java虚拟机栈、Java堆、方法区。

![Java虚拟机内存区域](http://img.blog.csdn.net/20131226151744250)

[【深入Java虚拟机（1）】：Java内存区域与内存溢出 \- ImportNew](http://www.importnew.com/19946.html)