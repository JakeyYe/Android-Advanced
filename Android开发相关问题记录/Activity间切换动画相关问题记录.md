## Activity间切换动画相关问题记录

[Android Activity切换动画多种实现方式与封装 \- SoulQw \- CSDN博客](http://blog.csdn.net/u014626094/article/details/52489889)

#### Android切换动画的几种实现方式：

1，Activity.overridePendingTransition()

在startActivity()方法之后设置该方法，设置开始动画，覆写finish()方法在super.finish()之后设置该方法，设置结束动画；

2，ActivityOptionsCompat

这个类是support v4中新加的类，为Activity添加各种动画；

3，AppTheme,直接在主题中修改Activity动画样式