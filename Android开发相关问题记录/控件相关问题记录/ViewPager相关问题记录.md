## ViewPager相关问题记录

[ViewPager 超详解：玩出十八般花样](https://mp.weixin.qq.com/s?__biz=MzAxMTI4MTkwNQ==&mid=2650824705&idx=1&sn=346c8bacea281cde8c30ae4a9f4b949d&chksm=80b7b49fb7c03d899bfbbd8336edb57857a04b75b07b7e2f06a93eace02f1c9707b954900674&scene=0&pass_ticket=uMLfEXNPeBmNUcqpUjh7OOK0zDtImVzpV57XXtqVcvfn4qBdjiTIHoKa9HgQdfs%2F#rd)

- ViewPager 的基本使用（简介，适配器）
- ViewPager+TabLayout+Fragment 的使用
- ViewPager 轮播图的使用（指示器，标题，自动轮播，首尾循环）
- ViewPager 切换效果 （PageTransformer）
- ViewPager 切换效果进阶

#### ViewPager的使用
	ViewPager控件(ViewPager+Fragment)
	PagerAdapter
	ViewPager.OnPageChangeListener

#### ViewPager+Fragment(就是ViewPager中每个界面都使用一个Fragment来显示)使用懒加载
	关键点是 Fragment.getUserVisibleHint()/setUserVisibleHint()方法（Fragment只有在ViewPager中这两个方法才有作用），获取提示（hint）判断Fragment是否真正显
	示，以便懒加载布局。