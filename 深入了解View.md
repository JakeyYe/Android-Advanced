#深入了解View

###1,任何一个视图都不可能凭空突然出现在屏幕上，它们都是要经过非常科学的绘制流程后才能显示出来的。每一个视图的绘制过程都必须经历三个最主要的阶段，即onMeasure()、onLayout()和onDraw()。
	View.measure()  ---> View.onMeasure()方法就是用于测量视图的大小的。
	View.layout()   ---> View.onLayout()方法是用于给视图进行布局的，也就是确定是视图的位置。
	View.draw() ---> View.onDraw()方法就是对视图进行绘制。

###2,自定义View组件，一定要写构造方法
 	public  CustomView(Context context) {}
 	public  CustomView(Context context, AttributeSet attrs) {}
 	public  CustomView(Context context, AttributeSet attrs, int defStyleAttr) {}
 	public  CustomView(Context context, AttributeSet attrs, int defStyleAttr, int defStyleRes) {}

	要点：一定要覆写带AttributeSet属性参数的构造方法，才能在XML资源文件中设置自定义View
	如果只覆写带Context属性参数的构造方法则只能在代码中声明该自定义View组件，带四个参数的构造方法是
	在API21才加上的，暂不考虑。有三个参数的构造函数中第三个参数是默认的Style，这里的默认的Style是指
	它在当前Application或Activity所用的Theme中的默认Style，且只有在明确调用的时候才会生效。

###3,getMeasuredWidth()和getWidth();

View.getHeight() 和 View.getWidth() 获取组件的宽高
一般情况下getMeasuredWidth和getWidth方法的值是一致的，这里只要记住一般情况下除了在onLayout方法中调用getMeasuredWidth方法外其它的地方用getWidth方法就行了。

- getMeasuredWidth方法获得的值是setMeasuredDimension方法设置的值，它的值在measure方法运行后就会确定
- getWidth方法获得是layout方法中传递的四个参数中的mRight-mLeft，它的值是在layout方法运行后确定的
- 一般情况下在onLayout方法中使用getMeasuredWidth方法，而在除onLayout方法之外的地方用getWidth方法。

###4,调用View.measure(0,0)发生了什么
####[调用View.measure(0,0)发生了什么](http://www.jianshu.com/p/dbd6afb2c890)

###5,测量，布局，绘制流程
####[Android View绘制流程（Measure）完全解析](http://www.jianshu.com/p/3299c3de0b7d)
####[Android View绘制流程（Layout）完全解析](http://www.jianshu.com/p/836bfdc36407)
####[Android View绘制流程（Draw）完全解析](http://www.jianshu.com/p/3e064c045f0f)