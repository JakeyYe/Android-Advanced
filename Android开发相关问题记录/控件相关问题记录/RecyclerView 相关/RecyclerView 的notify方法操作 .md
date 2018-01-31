## RecyclerView 的notify方法操作

RecyclerView 几种局部操作(增删改查)的方法：

- notifyItemChanged

- notifyItemRemoved

- notifyItemMoved

- notifyItemInserted


这些方法所展现的操作会有动画效果的，这种动画效果是由 **ItemAnimator** 指定的；

调用这几个方法来对 RecyclerView 进行局部操作之前，**要对对应的数据进行相对的改变**；

	//在 RecyclerView 中的指定位置插入一个新的Item
	list.add(2,"new add Item");
	notfyItemInserted(2);

	//移除 RecyclerView 中指定位置的一个Item
	list.remove(4);
	notifyItemRemoved(4);

	//将 RecyclerView 中的第 0 个位置的Item和第 1 个位置的进行位置交换
	list.add(1,list.get(0));
	list.remove(0);
	notifyItemMoved(0,1);

	//要注意这个方法的多个重载方法，使用其中的一个重载方法可对单个Item内的内容进行局部刷新
	notifyItemChanged()

[RecyclerView里notifyItemRemoved的坑 \- kyleada的专栏 \- CSDN博客](http://blog.csdn.net/wangkai0681080/article/details/50082825)

--------------------

- Adapter.notifyDataSetChanged()----重新绑定和重新布局所有可见的视图；

- Adapter.notifyItemChanged(int)----刷新单个Item的全部布局内容，还可以使用其重载方法 notifyItemChanged(int,Object)方法刷新单个Item里的一个或多个布局内容；

也可以直接使用 LayoutManager 获取指定位置的 ViewHolder 来修改布局，但是 RecyclerView 中的数据却没有修改，而前两种方式都是通过修改 RecyclerView 中的数据再刷新布局的的；