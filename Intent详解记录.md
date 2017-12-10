## Intent详细记录

	Activity之间，Service之间，BroadcastReceiver之间都是通过Intent进行通信的，而另外一个ContentProvider本身就是一个通信机制，不需要通过Intent。

#### 1，Intent,中文翻译为“意图”，是一个消息传递对象，可以使用它从其他应用组件请求操作，在Android中提供了`Intent`机制来协助应用间的交互和通讯。`Android`根据此`Intent`的描述，负责找到对应的组件，将`Intent`传递给 调用的组件，并完成组件的调用。`Intent`不仅可用于应用程序之间，也可用于应用程序内部的`Activity/Service`之间的交互。因此，可以将`Intent`理解为不同组件之间通信的“媒介”专门提供组件互相调用的相关信息。

###2，`Intent`的属性，`Intent`有以下几个属性：动作（`Action`），数据（`Data`），分类（`Category`），类型（`Type`），组件（`Compent`），以及扩展（`Extra`），其中最常用的是`Action`动作和`Data`属性。                     
`Action`属性：`Action`是指`Intent`要完成的动作，是一个字符串常量。有两个重要的action:

- Intent.ACTION_VIEW，其值为“android.intent.action.VIEW”，当你有一些数据想通过其他Activity展示给用户的时候，你可以将Intent的action指定为ACTION_VIEW,比如在一个图片应用中查看一张图片，或者在一个地图应用中展现一个位置；
- Intent.ACTION_SEND，其值为“android.intent.action.SEND”，该action常用来做“分享”使用，当你有一些数据想通过其他的APP(如QQ,微信等)分享出去的时候，就可以使用此action构建Intent对象，将数据分享出去；

`Data`属性：`Intent`的`Data`属性是执行动作的`URL`和`MIME`(数据类型)类型。

`Type`属性：数据类型，显示指定Intent的数据类型（MIME）；**不能同时调用setType()和setData()方法的，因为不同的Data对应不同的Type，所以更新其中一个，另一个就设置成无效，如果要同时设置，则需要使用setDataAndType()方法**；

`Category`属性：类别，包含了处理该Intent的组件的种类信息，起着对Action的补充说明的作用：
如：
CATEGORY_HOME:表示返回Home界面；
CATEGORY_LAUNCHER:表示Intent的接受者应该在Launcher中作为顶级应用出现；

`Component`属性：表示要显式启动的组件的类名称；

`Extras`属性：附加信息；

`Flag`属性：该属性用于通知系统以何种启动模式启动目标Activity，或者启动之后采取怎样的操作；
如：FLAG_ACTIVITY_NEW_TASK:通知系统目标Activity在新的Task中启动；

[Android中Intent概述及使用 \- CSDN博客](http://blog.csdn.net/iispring/article/details/48417779)

#### 注意点
(1)setType和setData只能有一个生效
(2)如若同时设置setType和setData,可使用用函数setDataAndType



参考 
[官方文档之Intent 和 Intent 过滤器](https://developer.android.com/guide/components/intents-filters.html)

[官方文档之Intent](https://developer.android.google.cn/reference/android/content/Intent.html)

[Intent概述](http://www.cnblogs.com/smyhvae/p/3959204.html)

[使用Intent调用系统应用进行一些操作](http://blog.csdn.net/yulei_qq/article/details/21233901)



#### 使用Intent进行分享数据（文本，视频等）

使用Android Intent进行原生分享，就是用到Intent.ACTION_SEND这个Action，这对不同的Type分享不同类型的数据；

Type:

- text/*:文本类型
- image/*:图片类型
- video/*：视频类型
- audio/*：音频分享

[调用android自带分享功能，分享图片文字等信息。 \- CSDN博客](http://blog.csdn.net/wanglining1987/article/details/52698535)

[android调用系统播放器播放视频\-小坑一个 \- CSDN博客](http://blog.csdn.net/jw20082009jw/article/details/54583115)



[android调用系统分享实现朋友圈同时分享文字和图片（可多张） \- 简书](http://www.jianshu.com/p/d1852ace3fd5)


#### 使用Intent进行原生分享（可以做到）或者使用第三方SDK来进行分享
[史上最详细Android集成QQ，微信，微博分享（不用第三方）持续更新中 \- Android干货 \- SegmentFault](https://segmentfault.com/a/1190000004926845)