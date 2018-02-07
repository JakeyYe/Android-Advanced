## 图片加载框架之Glide

	Glide的一整套图片加载机制的基本流程梳理

**看源码看源码**

Glide V3的使用直接查看郭霖的文章

Glide V4的使用 [Glide最新版V4使用指南 \- 三七的博客 \- CSDN博客](http://blog.csdn.net/u013005791/article/details/74532091)

Glide V3和Glide V4的区别[Glide v4 : 快速高效的Android图片加载库](https://muyangmin.github.io/glide-docs-cn/)

![Glide结构图](http://blog.qiji.tech/wp-content/uploads/2016/04/glide%E7%BB%93%E6%9E%84%E5%9B%BE.jpg)

[\[Android\] Glide 源码解析（一） – 技术学习小组](http://blog.qiji.tech/archives/8807)

[Glide源码分析 \| Hpw123](http://hpw123.win/2016/12/30/Glide%E6%BA%90%E7%A0%81%E5%88%86%E6%9E%90/)

注意点：

1）Glide.with()方法传入的实例会决定Glide加载图片的生命周期，如果传入的是Activity或Fragment实例，那么当这个Activity或Fragment被销毁时，图片加载也会被停止，如果传入的是ApplicationContext，那么只有当应用被停止时，图片加载才会停止,所以最好传入Activity/Fragment实例。

2)设置占位图后，加载出来的图片的大小可能会变化，所以可以将占位图当作ImageView的background；

3)当Glide与列表控件一起使用时，当列表在滑动时，调用Glide的pauseRequests()方法请求取消请求，滑动停止时，调用resumeRequests()方法恢复请求；