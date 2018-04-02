## PopupWindow相关问题记录

	Android关于弹窗的实现大致有两种方式实现：AlertDialog和PopupWindow,当然还有使用Activity并配合Dialog主题实现弹窗的；

	PopupWindow和AlertDialog两者的最主要的区别就是显示位置问题：
	位置是否固定，AlertDialog显示位置相对是固定的，直接显示在Window的中间位置，而PopupWindwo则可以在Window的任意位置显示；

可以借鉴[Android PopupWindow的封装使用](https://www.cnblogs.com/jzyhywxz/p/7039503.html)

- PopupWindow的背景边框阴影效果是通过设置一个有阴影边框的背景Drawable来实现的；
- PopupWindow.showAsDropDown()方法中的偏移量无效的解决方法，直接调用showAsDropDown(View)方法：在不会超出屏幕的情况下PopupWindow的左上角位置会在anchor的左下角或者左上角显示，若可能超出屏幕，将向左偏移；第二个参数如果直接设置为`-contentView.getMeasureWidth()`的话，那么contentView的左上角会在anchor的左上角或左下角位置，如果再加上一个正值，那么PopupWindow的位置就会向右移动，但是不会超出屏幕；

#### 重要点记录

- PopupWindow.mFocusable变量，作用是设置PopupWindow是否可以接受焦点事件，要设置为true后（通过PopupWindow.setFocusable(true)或PopupWindow的含有三个参数的构造函数，最后一个参数代表该属性），点击PopupWindow外部会消失，Back键也会消失，**该值默认为false**，若为false，这两个事件都不会起作用；


- PopupWidow.setTouchable(true);作用时设置PopupWindow可接受触摸事件，设置这个，点击外部区域不会消失，而且点击Back键也不消失，该值默认为true，所以不用显式设置；


- PopupWindow.setOutsideTouchable(true)；作用是设置可接受外部区域的触摸事件，默认为false，**设置为true后**，可接受外部区域点击事件，点击外部区域会消失，但是点击Back键还是不消失；


- PopupWindow.setBackgroundDrawable(new ColorDrawable());作用是设置PopupWindow的背景，如果不设置背景，有些版本就会出现一个问题：无论点击外部区域还是Back键都无法dismiss弹框；
- PopupWindow.showAsDropDown()方法是设置PopupWindow显示在某个控件之下，可以设置左右偏移量，相当于下拉弹框；


- PopupWindow.showAtLocation()方法可以指定PopupWindow在Window上的任意位置，**注意：第一个参数不是anchor View，而是为了从父视图来获取getWindowToken（）标记的，获取一个创建新Window的Window Token值（令牌）**，第二个参数是通过Gravity控制PopupWindow弹出的大致位置，后面两个参数是弹出位置在x/y方向上的偏移量；


- 创建PopupWindow的时候指定宽高值为contentView的宽高值时，showAsDropDown()方法能够自适应，如果设置为wrap_content,showAsDropDown()方法会认为下面的空间一直很充足，这样就不会自适应，可能会被挡住，所以：如果PopupWindow里面有ListView,ScrollView时，一定要动态设置PopupWindow的大小；

#### PopupWindow.showAtLocation(View parent,int gravity,int x,int y)方法解析：
第一个参数上面已经说了，不是anchor View,只是通过该View获取创建新Window的Window Token（看源码），第二个参数的作用是设置相对于Window的位置，如Gravity.TOP.Gravity.START等，注意，如果设置了后面两个位置精确值，第二个参数就没有效果了，可以设置为Gravity.NO_GRAVITY了；



#### PopupWindow.showAsDropDown(View anchor,int xOff,int yOff,int gravity)方法解析：
主要是第四个参数，第四个参数的作用是 @param gravity Alignment of the popup relative to the anchor，相对于anchor View（锚）的对齐方式；

如果单独设置第二，三个参数，那么这两个值代表的偏移量是没有效果的，只有同时设置后三个参数，偏移量下x/y值才会起作用；

创建PopupWindow时候指定高宽时showAsDropDown能够自适应，如果设置为wrap_content,showAsDropDown会认为下面空间一直很充足，注意：如果PopupWindow里面有ListView,ScrollView时，一定要动态设置PopupWindow的大小


#### PopupWindow弹出的动画效果，默认是直接弹出和消失的

通过PopupWindow.setAnimationStyle()方法设置动画弹出和消失的效果；

直接参考这里 [Android PopupWindow使用方法小结 \- 式 \- 博客园](https://www.cnblogs.com/jzyhywxz/p/7039503.html)

###整体参考自该Demo [SmartPopupWindow](https://github.com/PopFisher/SmartPopupWindow)