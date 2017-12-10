## Android适配
	记录Android适配思想

[支持多种屏幕 \| Android Developers](https://developer.android.com/guide/practices/screens_support.html?hl=zh-cn)

### Android单位基本知识总结

	屏幕尺寸
	屏幕分辨率
	屏幕像素密度
	dp/dip(density-independent pixel密度无关像素)
	px(pixel)
	sp(scale-independent pixel独立比例像素)

[Android 屏幕适配：最全面的解决方案 \- 简书](http://www.jianshu.com/p/ec5a1a30694b)

### 屏幕适配问题

[适配适配](http://blog.csdn.net/lmj623565791/article/details/49990941)
	
	基本适配做法：
	1，控件大小尽量使用wrap_content，match_parent,而不要使用具体值；
	2，尽量使用svg图片
	3，文字的单位取sp,而不是dp或其他的
	4，定义多个资源文件，系统会根据屏幕大小加载适合的资源文件

	屏幕适配方面：
	1，“布局”适配：使用相对布局（RelativeLayout）
	2，“布局组件”适配：使用wrap_content,match_parent,weight
	3，“图片资源”适配：使用.9图和SVG图片