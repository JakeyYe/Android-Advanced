## ListView相关问题记录

#### 为什么调用ListView的适配器的notifyDataSetChanged()方法没有效果？ 
	1，数据源没有更新，调用notifyDataSetChanged无效。
	2，数据源更新了，但是它指向了新的的引用，调用notifyDataSetChanged无效。
	3，数据源更新了，但是adapter没有收到消息通知，无法动态更新列表。

[参考](http://www.chongchonggou.com/g_68521422.html)

#### ListView.notifyDataSetChanged()方法是将数据全部更新的，可以只将可见范围的Item更新数据的 

[ListView局部更新](http://www.10tiao.com/html/330/201701/2653578459/2.html)

#### ListView和RecyclerView的比较，什么情况下使用Recycler View比较有优势？RecyclerView和ListView的使用场景：
	
	列表页展示界面，需要支持动画，或者频繁更新的，局部刷新，建议使用RecyclerView,更加强大完善，易扩展；其他情况（如微信卡包列表页）两者都可以，但是ListView在使用上会更加方便，快捷。

### ListView的onItemClickListener和onItemLongClickListener事件？
	ListView中如果同时设置长按和短按事件监听器，会发现长按触发时，短按事件也会触发，这是因为onItemLongClickListener默认返回false，如果该接口中的方法返回false就会同时触发短按事
	件，只要设置为true，也没问题了

	延伸到RecyclerView,RecyclerView的这种情况怎么样？	
	RecyclerView的Item点击事件，系统并未提供，我们可以自己写一个接口回调。

### ListView的几种适配器
- ArrayAdapter适合非常简单的数据显示，很方便，很简单。

- SimpleAdapter可以自定义Item布局，用于显示交简单的布局及控件，但布局内的控件如按钮等无法获取到焦点，当然也就无法获取到他们的点击事件。

- SimpleCursorAdapter与SimpleAdapter相似，只是他的数据源是Cursor类型而已。

- BaseAdpter子类最常用的ListView数据适配器，通过继承BaseAdpter可以较灵活的实现数据的绑定，同时通过使用ViewHolder等可以很好的提高ListView的绘制效率。另一个很重要的原因，BaseAdpter类适配器绑定的Item布局中的子控件可以获取到触摸焦点，也就是说，通过这种方式，我们可以获取Item布局中一些对象的点击，长按，check等方法,**而前面几种Adapter:ArrayAdapter,SimpleAdapter,SimpleCursorAdapter都是不能设置ListView Item的点击事件，只使用于展示一组数据**。


### ListView中Item高度设置

使用LayoutInflater.inflate(int resourceId,ViewGroup root,boolean attachToRoot);方法即可

或者使用下面的方式 [android 关于listview item设置高度的问题解决方法 \- CSDN博客](http://blog.csdn.net/coderinchina/article/details/50670505)