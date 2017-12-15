## Fragment基础

	如果使用Android 3.0以下的版本，需要引入v4包，然后Activity继承FragmentActivity，然后通过getSupportFragmentManager获取FragmentManager;

	现在根本不需要使用v4包，不需要使用兼容低版本的Fragment；

#### Fragment的几个方法

1，show(),hide()方法是让Fragment的View setVisibility方法设置Fragment隐藏还是显现，不会调用生命周期方法；

2，replace()是会销毁视图的，即调用onDestroyView，onCreateView等一系列生命周期方法；


#### onHiddenChanged()方法的回调时机

跳转新的Fragment时，旧的Fragment会回调onHiddenChanged()方法，不会回调onStop()等生命周期方法，而新的Fragment在创建时是不会回调onHiddenChanged()方法的；

#### FragmentManager用来管理Activity中的Fragment的

每个Fragment以及宿主Activity（继承自FragmentActivity）都会在创建时，初始化一个FragmentManager对象，它是处理好Fragment嵌套问题的关键，通过它来理清不同层次的栈视图；

getSupportFragmentManager()；//v4包 获取FragmentManager对象

getFragmentManager();//获取FragmentManager对象

FragmentTransaction transaction=FragmentManager().beginTransaction();//获取Transaction对象,开启一个事务

//对Fragment的几种操作

- transaction.add()；
- transaction.remove();
- transaction.replace();

//调用这两个方法来隐藏/展示Fragment,调用这两个方法不会调用生命周期方法，而是会调用onHiddenChanged()方法

- transaction.show()；
- transaction.hide();

- transaction.attach();
- transaction.detach();//会将view从UI移除，和remove()不同，此时Fragment的状态依然由FragmentManager维护；

//Transaction.commit()方法要在Activity.onSaveInstanceState()方法之前调用，否则会报错，不能在onSaveInstanceState()方法之后做commit操作； 

transaction.commit()//提交事务，使用Transaction做一些操作后，都要调用该方法来提交事务，来保证操作生效

[Fragment全解析系列（二）：正确的使用姿势 \- 简书](http://www.jianshu.com/p/fd71d65f0ec6)