# EventBus 3.0详解

### 什么是EventBus?(what)
	EventBus是一个Android端优化的publish/subscribe消息总线，简化了应用程序内各组件间、组件与后台线程间的通信。比如请求网络，等网络返回时通过Handler或BraodcastReceiver通知UI,两个
	Fragment之间需要通过Listener通信，应用程序内各组件间、组件与后台线程间的通信，这些需求都可以通过EventBus来实现。

	EventBus是Android的中央发布/订阅事件系统。事件被发布（EventBus.post(Object)）到总线，该总线将其传递给具有事件类型的匹配处理程序方法的订阅者。为了接收事件，用户必须使用
	（EventBus.register(Object)）向总线注册自己。一旦注册，订阅者将收到事件，直到（EventBus.unregister(Object)）被调用。事件处理方法必须由"Subscribe"注解，必须是public，不返回
	（void）,并且只有一个参数（事件）。

### 怎么使用？（how）

	// 先添加依赖greenDao/EventBus(最新版)
    compile 'org.greenrobot:eventbus:3.0.0'
	
	1，EventBus.getDefault().register(this);//EventBus注册

	2，EventBus.getDefault().post(Event);//publish发布事件

	3，onHandleEvent(Event event);//Subscribe订阅（处理）事件，可以指定在那个线程运行处理事件方法，在要处理发布事件的类中声明该方法，也就是在**注册的类**中声明该方法

	4，Event.getDefault().unregister();//在适当的时机解注册EventBus

![EventBus各角色协作图](http://images2015.cnblogs.com/blog/950883/201606/950883-20160618080626370-1336092255.png)

### 重要点

EventBus负责存储订阅者、事件相关信息，订阅者和发布者都只和EventBus关联，这样保证了事件发布和订阅充分解耦。

每个新建的EventBus发布和订阅事件都是相互隔离，即一个EventBus对象中的发布者发布事件，另一个EventBus对象中的订阅者不会收到该订阅。

ThreadMode-订阅方法执行线程

- POSTING:表示订阅方法运行在发送事件的线程；（订阅方法默认执行线程）
- MAIN：表示订阅方法运行在UI线程，由于UI线程不能阻塞，因此当使用MAIN的时候，订阅方法不应该执行耗时操作；
- BACKGROUND：表示订阅方法运行在后台线程，如果发送的事件线程不是UI线程，那么就使用该线程；如果是UI线程，那么新建一个后台线程来执行订阅方法，该线程是唯一一个后台线程，当事件超过一个时，事件会被放在队列中一次执行；
- ASYNC：订阅方法与发送事件始终不在同一个线程，即订阅方法始终会使用新的线程来运行。

Sticky事件
事件分为一般事件和Sticky事件，相对于一般事件，Sticky事件不同之处在于，当事件发布后，再有订阅者开始订阅该类型事件，依然能接收到该类型事件最近一个Sticky事件。

priority-优先级
设置该优先级的目的是，当一个事件有多个订阅者的时候，优先级高的会优先接收到事件。

[codeKK源码分析](http://p.codekk.com/blogs/detail/54cfab086c4761e5001b2538)

### EventBus优缺点
	优点：简化组件之间的通信方式，实现解耦让业务代码更加简洁，可以动态设置事件处理线程以及优先级；
	缺点：目前发现的唯一缺点就是类似之前策略模式一样的诟病，每个事件都必须自定义一个事件类，造成事件类太多，无形中加大了维护成本。
[Android消息传递之EventBus 3\.0使用详解 \- 总李写代码 \- 博客园](http://www.cnblogs.com/whoislcj/p/5595714.html)

[greenrobot/EventBus(github.com)](https://github.com/greenrobot/EventBus)

[使用快速解读-EventBus 3\.0的用法详解（一） \- neu \- SegmentFault](https://segmentfault.com/a/1190000004279679)

### EventBus和BroadcastReceiver
BroadcastReceiver代表系统的设计，有着系统的合理性，而EventBus如果使用不当，会打破这种系统合理性
[Android中EventBus的使用与相关原理分析 \- velsharoon](http://www.chenglong.ren/2016/11/19/android%E4%B8%ADeventbus%E7%9A%84%E4%BD%BF%E7%94%A8%E4%B8%8E%E7%9B%B8%E5%85%B3%E5%8E%9F%E7%90%86%E5%88%86%E6%9E%90/)


