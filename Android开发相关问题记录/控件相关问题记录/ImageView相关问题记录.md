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