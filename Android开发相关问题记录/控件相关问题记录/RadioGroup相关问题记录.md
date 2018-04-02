## RadioGroup相关问题记录

	RadioButton.setEnable()设置是否可以点击
	RadioButton.setChecked()设置是否选中
	可以设置RadioButton的Background属性，在该Drawable中设置selector，设置state_checked为false和true不同状态下的不同背景；

#### RadioGroup和RadioButton可以实现单选效果,还可以实现简单的单选切换背景的效果
[自定义RadioGroup](http://blog.csdn.net/zhangli_/article/details/50718518)

#### 扩展RadioButton,灵活控制Drawable的大小
[Android 扩展RadioButton 灵活控制drawable的大小 \- qq402164452的博客 \- CSDN博客](http://blog.csdn.net/qq402164452/article/details/53539773)

#### ListView，RecyclerView，RadioGroup 分别实现单选等基本操作要熟悉

ListView实现的单选多选的缺点就是ListView Item的布局不能自定义，只能使用系统提供的简单布局

[ListView用系统布局实现单选RadioButton和多选CheckBox \- 简书](https://www.jianshu.com/p/d0e21d2672fc?utm_campaign=maleskine&utm_content=note&utm_medium=pc_all_hots&utm_source=recommendation)

还有一种实现方式是ListView通过notifyDataSetChanged()方法，设置选中项标志位，重新刷新布局；