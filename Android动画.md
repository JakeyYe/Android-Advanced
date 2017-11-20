## Android动画（还要继续补充）

	Object                      Object                                                                     
     Animation                   Animator                                                                       
       AlphaAnimation               AnimatorSet                                                                 
       AnimationSet                 ValueAnimator                                                                    
       DummyAnimation                 ObjectAnimator                                                                       
       Rotate3dAnimation              TimeAnimator                                                                        
       RotateAniamtion
       ScaleAnimation
       TranslateAnimation


	Android动画分类总结：
	1，视图动画（补间动画/View Animation）
	2，帧动画（Drawable Animation）
	3，属性动画(Property Animation)

### 三种动画原理解析：

- View Animation：对场景里的对象不断做图像变化，从而形成动画效果；
- 帧动画：通过连续展示一系列图片形成的动画效果；
- 属性动画：通过动态地改变对象的属性从而达到动画的效果；

可以好好看看这个[Android动画原理分析 \- krosshuang \- 博客园](https://www.cnblogs.com/kross/p/4087780.html)

### 属性动画（Property Animation）
	插值器：根据时间的流逝的比例，计算出属性的变化后的比例
	估值器：根据属性的变化后的比例，设置属性此刻的值

		ObjectAnimator->PropertyValuesHolder->KeyframeSet->Keyframe(Animator关键类)
		KeyframeSet继承Keyframes接口（Keyframe是个接口），KeyframeSet是动画帧集合，Keyframe代表一个动画帧，
	Keyframes接口中的方法是对Keyframe的各种操作的方法。

#### 注意点

	1，View Animation是可以同过设置startOffset属性来串行执行动画的，可以做到按顺序播放动画。
[动画\(Animation\) 之 \(闪烁、左右摇摆、上下晃动等效果\) \- CSDN博客](http://blog.csdn.net/feng88724/article/details/7000314)

	2，一种播放的属性动画在合适的时机要停止，否则可能造成内存泄漏。