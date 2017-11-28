## RecyclerView相关问题记录

没事可以多看看 [Android RecyclerView 使用完全解析 体验艺术般的控件 \- CSDN博客](http://blog.csdn.net/lmj623565791/article/details/45059587)

- LayoutManager 负责RecyclerView的布局，水平布局还是竖直布局或者是瀑布流；
- ItemDecoration 负责Item之间的分隔线效果
- ItemAnimator 负责操作单个Item的动画效果，Item增加、移除动画，要使之产生动画效果，只能使用notifyItemInserted()与notifyItemRemoved()方法，而不是使用notifyDateSetChanged()方法；
- RecyclerView.Adapter 负责将数据显示在界面上

#### RecyclerView源码分析，RecyclerView的三个方法onCreateViewHolder/onBindViewHolder/getViewType三个方法的调用顺序和频率？

	要进行RecyclerView源码解析
	
	RecyclerView的使用步骤：
	mRecyclerView = findView(R.id.id_recyclerview);
	//设置布局管理器，LayoutManager负责控制RecyclerView的显示方式
	mRecyclerView.setLayoutManager(layout);
	//设置adapter，Adapter负责将数据展示在界面上
	mRecyclerView.setAdapter(adapter)
	//设置Item增加、移除动画，ItemAnimator负责Item增删的动画
	mRecyclerView.setItemAnimator(new DefaultItemAnimator());
	//添加分割线，ItemDecoration负责RecyclerView中Item间的分隔线
	mRecyclerView.addItemDecoration(new DividerItemDecoration(
                getActivity(), DividerItemDecoration.HORIZONTAL_LIST));


#### RecyclerView局部刷新

- notifyItemChanged(int position) 更新列表position位置上的数据可以调用
- notifyItemInserted(int position) 列表position位置添加一条数据时可以调用，伴有动画效果
- notifyItemRemoved(int position) 列表position位置移除一条数据时调用，伴有动画效果
- notifyItemMoved(int fromPosition, int toPosition) 列表fromPosition位置的数据移到toPosition位置时调用，伴有动画效果
- notifyItemRangeChanged(int positionStart, int itemCount) 列表从positionStart位置到itemCount数量的列表项进行数据刷新
- notifyItemRangeInserted(int positionStart, int itemCount) 列表从positionStart位置到itemCount数量的列表项批量添加数据时调用，伴有动画效果
- notifyItemRangeRemoved(int positionStart, int itemCount) 列表从positionStart位置到itemCount数量的列表项批量删除数据时调用，伴有动画效果

Adapter.notifyItemChanged(int position)方法是刷新单个Item整个布局,该方法会调用onBindViewHolder(ViewHolder,int)方法对item中的所有控件进行刷新；

Adapter.notifyItemChanged(int position,Object payload)方法可以对单个Item中的某个控件进行刷新，该方法会调用onBindViewHolder(ViewHolder,int,List)方法对Item中单个控件进行刷新；

[Android RecyclerView 真正的布局刷新的正确方式 \- qq402164452的博客 \- CSDN博客](http://blog.csdn.net/qq402164452/article/details/53464091)

#### RecyclerView.notifyItemRemoved()相关方法动态改变单个Item的问题

	通过该方法删除RecyclerView单个Item，但是传递的position不能直接使用onBindViewHolder()方法传递进来的position，而是应该使用ViewHolder.getAdapterPosition()当成Item下标位置；

[再说Android RecyclerView局部刷新那个坑 \- 享受技术带来的快乐 \- CSDN博客](http://blog.csdn.net/jdsjlzx/article/details/52893469)

[RecyclerView关于notifyItemRemoved的那点小事 \- Android移动开发技术文章\_手机开发 \- 红黑联盟](https://www.2cto.com/kf/201608/534945.html)

#### RecyclerView中Item之间的分隔线，左右两边间隔问题？

1）RecyclerView+CardView的情形：

要弄清楚CardView的属性，CardView中的contentPadding,cardUseCompatPadding等属性对间隔是有影响的；

card:cardUseCompatPadding 设置CardView上下之间的间隔，在RecyclerView中设置layout_marginLeft/Right属性，该属性设置RecyclerView左右之间的间距；


#### RecyclerView.ItemDecoration,该类是抽象类，自定义该类只需要覆写其中的方法，其中三个重要方法getItemOffsets(),onDraw(),onDrawOver()

- getItemOffsets() 负责在Item上下左右隔出空间，为每一个Item设置一定的偏移量，作用相当于设置padding
- onDraw() 负责在指定位置绘制一些用户指定的内容，在Item内容绘制之前绘制，所以可能被Item内容覆盖
- onDrawOver() 负责在指定位置绘制一些用户指定的内容，在Item内容绘制之后，所以可能会覆盖Item内容

[自定义RecyclerView\.ItemDecoration，实现Item的等间距分割以及分割线效果 \- 简书](http://www.jianshu.com/p/3b860938e503)

[RecyclerView之ItemDecoration由浅入深 \- 简书](http://www.jianshu.com/p/b46a4ff7c10a)


#### RecyclerView.ItemAnimator 定义RecyclerView单个Item的动画效果
[RecyclerView系列之六：item动画效果 \- 简书](http://www.jianshu.com/p/b375d552db63)