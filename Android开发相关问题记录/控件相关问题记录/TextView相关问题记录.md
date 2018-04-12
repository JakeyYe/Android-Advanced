## TextView相关问题记录

Chronmeter是继承自TextView的，可以直接用来展示时间进度的控件；
[Android Chronometer（计时器） \- 简书](https://www.jianshu.com/p/9630285e7cc7)

TextView.setCompoundDrawables(四个参数)；设置TextView四周上的Drawable图标；不过还要加上setBounds()方法；
不过可以直接使用setCompoundDrawablesWIthIntrinsicBounds()方法，这个方法相当于将setBounds()方法合并进去了；

[android TextView的setCompoundDrawables\(\)方法 \- 简书](http://www.jianshu.com/p/1ac91c3e0a77)

[TextView中使用占位符](http://blog.csdn.net/lingdianalex/article/details/52582935)

TextView中text添加空格是使用 “&#160;”，也可以在strings.xml文件中使用；

[TextView中使用空格](http://blog.csdn.net/rnclcl/article/details/16801779)

TextView的重要属性：

- android:maxLength:该属性的作用就是直接限制显示的长度，长度以外的文本直接不显示，文本的范围包括英文，符号，数字，汉子，长度的计算是直接计算个数，不管是英文字母还是中文文字；

- android:maxEms:作用是设置该TextView的最大宽度，多余的换行显示，要结合android:layout_width="wrap_content"一起使用；
[android TextView setEms 方法名字 \- CSDN博客](http://blog.csdn.net/JavaLive09/article/details/38661773)


[Android 解决TableRow中TextView或Edittext超出屏幕，不能自动换行或换行问题 \- CSDN博客](http://blog.csdn.net/fan7983377/article/details/52054333)

[Android开发学习笔记：TextView的属性详解\-IT的点点滴滴\-51CTO博客](http://blog.51cto.com/liangruijun/627123)