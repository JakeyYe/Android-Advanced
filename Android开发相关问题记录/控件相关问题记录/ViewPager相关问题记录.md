## ViewPager相关问题记录

#### ViewPager的使用
	ViewPager控件(ViewPager+Fragment)
	PagerAdapter
	ViewPager.OnPageChangeListener

#### ViewPager+Fragment(就是ViewPager中每个界面都使用一个Fragment来显示)使用懒加载
	关键点是 Fragment.getUserVisibleHint()/setUserVisibleHint()方法（Fragment只有在ViewPager中这两个方法才有作用），获取提示（hint）判断Fragment是否真正显
	示，以便懒加载布局。