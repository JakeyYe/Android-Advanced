## Handler相关问题记录

`Handler.removeCallbacks(Runnable r)`方法是将MessageQueue中的Message移除，而不进行处理，MessageQueue中的Message代表着这些Message还未处理，如果这些Message已经处于正在处理状态，那么这些Message将交由Handler处理，就不会在MessageQueue中了。

`Handler.removeCallbacks()`方法失效原因就是Message已经处于处理状态了，不在MessageQueue中了所以不能移除，方法失效；
[Handler\.removeCallbacks\(Runnable r\)失效原因 \- 简书](http://www.jianshu.com/p/8e8ac28f6c1a)