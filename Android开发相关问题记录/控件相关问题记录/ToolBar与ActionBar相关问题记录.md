## Toolbar与ActionBar相关问题记录

ToolBar使用过程：

	mToolBar=findViewById();

	setSupportActionBar(mToolBar);//将ActionBar内部的标题栏切换为ToolBar，也就是把ActionBar的内核换为ToolBar

	mActionBar=getSupportActionBar();//获取ActionBar
	//getSupportActionBar()方法继承自android.support.v7.app.AppCompatActivity

	//这些是 ActionBar的API，不是Toolbar的
	mActionBar.setDisplayHomeAsUpEnable(true);//增加一个返回箭头，id为android.R.id.home

	mActionBar.setDisplayShowHomeEnable(true);//设置应用程序图标为返回操作按钮
	
	mActionBar.setDisplayShowHomeEnable(true);//使左上角图标是否显示，是应用程序图标

	mActionBar.setDisplayShowCustomEnable(true);//使自定义的普通View能在title上显示，即mActionBar.setCustomView能起作用

[ToolBar、ActionBar与Menu的纠葛（以及navigationIcon、setHomeButtonEnabled、setDisplayHomeAsUpEnabled） \- 赛艇队长 \- 博客园](http://www.cnblogs.com/bellkosmos/p/5382272.html)

#### Toolbar上动态设置Menu

**Toolbar.inflateMenu() 在Toolbar上加载Menu**

几个重要方法：

- onOptinsItemSelected()--处理Menu中Item点击事件的
- onCreateOptionsMenu()--这个方法只在第一次调用
- onPrepareOptionsMenu()--这个方法会在**第一次调用**，和调用下面这个方法时也会回调该方法
- invalidateOptionsMenu()--调用这个方法会去回调onPrepareOptionsMenu方法的

[Toolbar动态改变menu \- FlowLeaf \- CSDN博客](http://blog.csdn.net/u011102153/article/details/53072105)

[Android动态修改ToolBar的Menu菜单 \- CSDN博客](http://blog.csdn.net/q4878802/article/details/51160424)

问题记录1 [Toolbar的Title与NavigationIcon距离异常 \- 简书](http://www.jianshu.com/p/27563ef79c0e)

问题记录2 [ToolBar的setTitle\(\)方法不生效解决方法 \- CSDN博客](http://blog.csdn.net/wshngyf/article/details/51761609)