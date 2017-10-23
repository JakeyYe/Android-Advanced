## 图片加载框架之Glide

	Glide的一整套图片加载机制的基本流程梳理

![Glide结构图](http://blog.qiji.tech/wp-content/uploads/2016/04/glide%E7%BB%93%E6%9E%84%E5%9B%BE.jpg)

[\[Android\] Glide 源码解析（一） – 技术学习小组](http://blog.qiji.tech/archives/8807)

[Glide源码分析 \| Hpw123](http://hpw123.win/2016/12/30/Glide%E6%BA%90%E7%A0%81%E5%88%86%E6%9E%90/)

注意点：

1）Glide.with()方法传入的实例会决定Glide加载图片的生命周期，如果传入的是Activity或Fragment实例，那么当这个Activity或Fragment被销毁时，图片加载也会被停止，如果传入的是ApplicationContext，那么只有当应用被停止时，图片加载才会停止。