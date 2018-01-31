## ImageView相关问题记录

#### ImageView的src和background是不同的

1)**代码设置ImageView的src**:

	setImageDrawable(Drawable d);
	setImageBitmap(Bitmap b);
	setImageResource(int resId);

2)**代码设置ImageView的backgroup**

	setBackground(Draable d);
	setBackgroundResouce(int resId);
	setBackColor(int color);
	setBackgroundDrawable(Drawable d);


#### ImageView的scaleType属性总结

scaleType 属性决定了图片在 View 上显示时的样子，如进行何种比例的缩放，及显示图片的整体还是部分等等；

	android：scaleType="centerCrop"

[Android中的ImageView的scaleType属性详解 \- 生死看淡，不服就干！ \- CSDN博客](http://blog.csdn.net/jiangwei0910410003/article/details/16804357)
