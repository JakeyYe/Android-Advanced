#Intent详细记录

###1，Intent,中文翻译为“意图”，是一个消息传递对象，可以使用它从其他应用组件请求操作，在Android中提供了`Intent`机制来协助应用间的交互和通讯。`Android`根据此`Intent`的描述，负责找到对应的组件，将`Intent`传递给 调用的组件，并完成组件的调用。`Intent`不仅可用于应用程序之间，也可用于应用程序内部的`Activity/Service`之间的交互。因此，可以将`Intent`理解为不同组件之间通信的“媒介”专门提供组件互相调用的相关信息。

###2，`Intent`的属性，`Intent`有以下几个属性：动作（`Action`），数据（`Data`），分类（`Category`），类型（`Type`），组件（`Compent`），以及扩展信（`Extra`），其中最常用的是`Action`动作和`Data`属性。                     
`Action`属性：`Action`是指`Intent`要完成的动作，是一个字符串常量。

`Data`属性：`Intent`的`Data`属性是执行动作的`URL`和`MIME`(数据类型)类型。

...

参考 
[官方文档之Intent 和 Intent 过滤器](https://developer.android.com/guide/components/intents-filters.html)

[官方文档之Intent](https://developer.android.google.cn/reference/android/content/Intent.html)

[Intent博客介绍](http://blog.csdn.net/yulei_qq/article/details/21233901)

[博客介绍](http://www.cnblogs.com/smyhvae/p/3959204.html)