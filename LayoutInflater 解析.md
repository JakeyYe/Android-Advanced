## LayoutInflater解析

LayoutInflater也就是“布局加载器”，用来加载布局（View/ViewGroup）的，是通过单例模式获取的；

	三种方式获取LayoutInflater：
	LayoutInflater layoutInflater=Context.getSystemService(Context.LAYOUT_INFLATER_SERVICE);
	LayoutInflater l2=LayoutInflater.from(Context);
	LayoutInflater l3=Activity.getLayoutInflater();


LayoutInflater.inflate()方法有四个重载方法：

- inflate(int res,ViewGroup root);
- inflate(int res,ViewGroup root,boolean attachToRoot);
- inflate(XmlPullParser parser,ViewGroup root);
- inflate(XmlPullParser parser,ViewGroup root,boolean attachToRoot);

要弄懂其所代表的含义；

看这一个就可以了  [Android LayoutInflater源码解析 \| Allen's Zone](http://allenfeng.com/2017/02/24/how-android-layout-inflater-work/)