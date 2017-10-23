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


### 属性动画（Property Animation）
	插值器：根据时间的流逝的比例，计算出属性的变化后的比例
	估值器：根据属性的变化后的比例，设置属性此刻的值

		ObjectAnimator->PropertyValuesHolder->KeyframeSet->Keyframe(Animator关键类)
		KeyframeSet继承Keyframes接口（Keyframe是个接口），KeyframeSet是动画帧集合，Keyframe代表一个动画帧，
	Keyframes接口中的方法是对Keyframe的各种操作的方法。

#### 注意点

	1，View Animation中并没有串行执行动画的方法提供的。

	2，一种播放的属性动画在合适的时机要停止，否则可能造成内存泄漏。