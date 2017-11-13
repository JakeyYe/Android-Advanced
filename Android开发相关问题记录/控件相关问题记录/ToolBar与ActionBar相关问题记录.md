## Toolbar与ActionBar相关问题记录

ToolBar使用过程：

	mToolBar=findViewById();

	setSupportActionBar(mToolBar);//将ActionBar内部的标题栏切换为ToolBar，也就是把ActionBar的内核换为ToolBar

	mActionBar=getSupportActionBar();//获取ActionBar
	//getSupportActionBar()方法继承自android.support.v7.app.AppCompatActivity

	mActionBar.setDisplayHomeAsUpEnable(true);//增加一个返回箭头，id为android.R.id.home

	mActionBar.setDisplayShowHomeEnable(true);//设置应用程序图标为返回操作按钮
	
	mActionBar.setDisplayShowHomeEnable(true);//使左上角图标是否显示，是应用程序图标

	mActionBar.setDisplayShowCustomEnable(true);//使自定义的普通View能在title上显示，即mActionBar.setCustomView能起作用

[ToolBar、ActionBar与Menu的纠葛（以及navigationIcon、setHomeButtonEnabled、setDisplayHomeAsUpEnabled） \- 赛艇队长 \- 博客园](http://www.cnblogs.com/bellkosmos/p/5382272.html)