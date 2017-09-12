## Android动画（还要继续补充）

	Android动画分类总结：
	1，视图动画（补间动画/View Animation）
	2，帧动画（Drawable Animation）
	3，属性动画(Property Animation)


### 属性动画（Property Animation）
	插值器：根据时间的流逝的比例，计算出属性的变化后的比例
	估值器：根据属性的变化后的比例，设置属性此刻的值

#### 注意点

	1，View Animation中并没有串行执行动画的方法提供的。