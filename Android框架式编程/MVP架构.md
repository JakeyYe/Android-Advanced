## MVP架构
	三层结构：View,Presenter,Model

View

1. 提供UI交互
2. 在presenter的控制下修改UI
3. 将业务事件交由presenter处理

Presenter

1. 对UI的各种业务事件进行相应处理
2. 与Model层交互，获取数据更新UI

Model

1. 从网络，数据库，文件，传感器等读写数据


![Android框架式编程之MVP](http://images2015.cnblogs.com/blog/682616/201703/682616-20170316100617713-1230796637.png)

[Android框架式编程之MVP架构 \- 灰色飘零 \- 博客园](http://www.cnblogs.com/renhui/p/6557230.html)