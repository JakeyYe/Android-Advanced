## RxJava2 看源码

看源码看源码

Disposable 查阅一下，这个的作用？？？

那如果有多个Disposable 该怎么办呢, RxJava中已经内置了一个容器 CompositeDisposable, 每当我们得到一个Disposable时就调用 CompositeDisposable.add()将它添加到容器中, 在退出的时候, 调用CompositeDisposable.clear() 即可切断所有的水管.

看英文文档

https://www.jianshu.com/p/9e3930fbcb26?utm_campaign=maleskine&utm_content=note&utm_medium=pc_all_hots&utm_source=recommendation

https://github.com/amitshekhariitbhu/RxJava2-Android-Samples