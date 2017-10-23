# 自定义View
	自定义View,尤其是制作一些复杂炫酷的效果的时候，实际上是将一些简单的东西通过数学上的精密计算组合到一起形成的效果。

### 几个重要的函数
	1，构造函数
	2，测量大小（onMeasure）
	3，确定View大小（onSizeChanged）
	4，确定子View布局位置（onLayout）
	5，绘制内容（onDraw）
	6，三个事件方法（分发/拦截/处理）
	7，对外提供操作方法和监听回调

	
### 核心方法
	invalidate():引起View树的重绘，要在UI线程中调用
	postInvalidate()：和上面的方法一致，只不过要在非UI线程中调用
	requestLayout():引起View的三个流程的重新执行（measure-layout-draw）

![invalidate和requestLayout的区别](http://upload-images.jianshu.io/upload_images/1734948-b4493f7b0234dd69.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240 "invalidate和requestLayout的区别")

[安卓自定义View教程目录](http://www.gcssloop.com/customview/CustomViewIndex)