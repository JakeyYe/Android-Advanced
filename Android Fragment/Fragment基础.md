## Fragment基础


#### Fragment的几个方法

1，show(),hide()方法是让Fragment的View setVisibility方法设置Fragment隐藏还是显现，不会调用生命周期方法；

2，replace()是会销毁视图的，即调用onDestroyView，onCreateView等一系列生命周期方法；


#### onHiddenChanged()方法的回调时机

跳转新的Fragment时，旧的Fragment会回调onHiddenChanged()方法，不会回调onStop()等生命周期方法，而新的Fragment在创建时是不会回调onHiddenChanged()方法的；

#### FragmentManager用来管理Activity中的Fragment的

每个Fragment以及宿主Activity（继承自FragmentActivity）都会在创建时，初始化一个FragmentManager对象，它是处理好Fragment嵌套问题的关键，通过它来理清不同层次的栈视图；

[Fragment全解析系列（二）：正确的使用姿势 \- 简书](http://www.jianshu.com/p/fd71d65f0ec6)