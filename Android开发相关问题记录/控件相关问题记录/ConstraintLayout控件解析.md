## ConstraintLayout布局管理器解析

尽量不用鼠标控制控件对控件做约束，而是直接使用代码来控制控件，鼠标控制效果不好控制；

[ConstraintLayout 终极秘籍（上） \- 云在千峰](http://blog.chengyunfeng.com/?p=1030)

[ConstraintLayout布局使用详解 \- Android \- 掘金](https://juejin.im/entry/5a0f93b4f265da432717ce87)

	ConstraintLayout-一种约束(Constraint)构建布局；

	ConstraintLayout可以看作是RelativeLayout的升级版,可以实现LinearLayout和RelativeLayout布局管理器实现的效果，可以有更
	多的手段来控制里面的子View的布局，所以对于复杂的布局用ConstraintLayout一个布局容器实现较好；

ConstraintLayout使用Constraint指定每个widget来决定它们在layout中的位置，可以使用Android Studio Layout编辑器界面来手动或者自动指定约束；


#### ConstraintLayout 本身使用的属性

- android:maxHeight/maxWidth 设置ConstraintLayout布局管理器本身的最大宽高值；

- android:minHeight/minWidth 设置ConstraintLayout 布局管理器本身的最小宽高值；


#### Guideline

Guideline 是用来辅助定位的一个不可见的元素；


#### 相对位置设置（layout_constraintXXX_toXXXOf）

设置控件与控件之间的相对位置，就像RelativeLayout布局管理器的使用；

`app:layout_constraintA_toBOf`属性：如果A和B相同，则是两个控件对齐关系；如果不相同，那A和B相对位置关系；


#### 偏移位置 （bias偏移量）

在设置控件的居中属性之后，通过偏移量可以设置让控件更偏向于依赖控件的某一方，偏移量设置为0~1之间的值相对属性：

- `layout_constraintHorizontal_bias`  //水平偏移
- `layout_constraintVertical_bias`  //垂直偏移


设置偏移属性的注意点：

- 设置偏移之前，一定要设置一个相对位置，如果没有相对位置，偏移就会无效；
- 水平偏移量是屏幕宽度的偏移倍数，垂直偏移量是屏幕高度的偏移倍数；


#### 可见性属性

当控件设置为Gone时，但是设置的约束条件还是有效的；

还有一种是 app:layout_goneMarginLeft="100dp" 这样的效果；

#### ConstraintLayout 子View尺寸约束

可以有三种不同的取值：确定值，wrap_content,0dp(也就是match_constraint)


#### 控制子View的宽高比

layout_constraintDimensionRatio 控制子View的宽高比；


参考[ConstraintLayout 学习总结 \- 简书](https://www.jianshu.com/p/e8f851045d10)


[Android ConstraintLayout详解 \- 简书](http://www.jianshu.com/p/a8b49ff64cd3)

[ConstraintLayout 属性详解 和Chain的使用 \- CSDN博客](http://blog.csdn.net/zxt0601/article/details/72683379)
