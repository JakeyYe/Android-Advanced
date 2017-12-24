## 反射2

根据虚拟机的工作原理，一般情况下，类需要经过：加载->验证->准备->解析->初始化->使用->卸载 这个过程；

 每个Java文件最终都会被编译为一个 .class 文件，这些Class对象承载了这些类的所有信息，包括父类、接口、构造函数、方法、属性等，这些Class文件在程序运行时会被ClassLoader加载到虚拟机中。

当一个类被加载以后，Java虚拟机就会在内存中自动产生一个Class对象，而我们一般情况下用 new 来创建对象，实际上本质都是一样的。


![反射有关的几个类](http://mmbiz.qpic.cn/mmbiz/MOu2ZNAwZwOeHq9X3jbmmcicAm819wO5oJeKdZJvPR6KU7iaqtpujiaxGUKicL5ytdI4m4niagU1L9oWNktaibIzcMNA/?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1)


	getDeclaredXXX()方法获取的是仅限于本类中所有不受访问限制的；
	getXXX()方法获取的是包括父类的但仅限与public修饰府的；

调用类静态方法和调用实例方法是有点区别的，调用实例方法一定需要一个类的实例，而调用静态方法不需要实例的引用，其实这是JVM在执行方法上的区别；


[Java反射以及在Android中的特殊应用](https://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650824708&idx=1&sn=1e66667522e5b4602eeb5391276a561f&chksm=80b7b49ab7c03d8c69e4f6ad64939679c830d23a524d900e6263dba20d946c8e68b9e2462898&mpshare=1&scene=1&srcid=1223DxDoLX6JRQiC71J1LNKA&pass_ticket=PW4kVAtcmG7hyamujQrntdgKJC9e1E3Cu2IS%2BY7uThROxMkKycfGFJwrO4rdiPfh#rd)

[一个事半功倍的Java反射库 \- 技术小黑屋](http://droidyue.com/blog/2017/01/09/joor-examples/index.html)