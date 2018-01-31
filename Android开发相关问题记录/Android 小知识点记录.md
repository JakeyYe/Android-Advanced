## Android一些小点记录

#### Android设置透明，半透明效果

透明度 0~255,0为完全透明，255为完全不透明

android:background="@android:color/transparent" //透明效果
 
ARGB值
半透明 #e0000000
透明 #00000000

[Android设置透明、半透明等效果\-Alex\_Michel\-51CTO博客](http://blog.51cto.com/2960629/742499)

#### 数值保留几位小数

[Java小数点位数保留 \- 简书](http://www.jianshu.com/p/00fff555986b)

#### Java文件大小转换工具类，B,KB,MB,GB

[我的Android进阶之旅\-\-\-\-\-\->Java文件大小转换工具类 \(B,KB,MB,GB,TB,PB之间的大小转换\) \- CSDN博客](http://blog.csdn.net/ouyang_peng/article/details/50717699)


#### "merge"标签只能置于布局的根布局

#### android:desendantFocusability属性，该属性就是设置父布局和子布局获取焦点的优先级

#### .gitignore文件
.gitignore文件就是github用来控制那些文件要提交，那些文件不提交的；


#### Android Studio项目下的libs文件夹和jniLibs文件夹有什么区别？

	Android Studio项目正常文件存放逻辑是将所有的.so和.jar包文件都放在这里，jniLibs文件夹一般是开发者自定义的文件夹，改变了原有的项目文件存放结构，将libs文件夹下的文件转移到新建的jniLibs文件夹下了。

     sourceSets {
        main {
			//通过这转移文件
            jniLibs.srcDirs = ['libs']
        }
    }

#### URL和URI
	URL 统一资源定位符
	URI 统一资源标识符
	两者都定义了what the resource is,URL还定义了how to get the resource,这个标识符还是一个可以获取上述对象的路径

#### TypedValue.applyDimension()方法也可进行单位转换，它是将方法封装起来了（单位转换，该方法是将其他单位长度（dp,sp）装换为px单位长度，不能反过来转换）

#### LinearLayout线性布局中的layout_weight属性设置问题：
	严格的说法应该是对当前剩余空间按权重平分；
	当布局管理器下的控件宽度都为0dp时，其控件比例就是权重比例，当宽度为match_parent或wrap_content时，其控件所占比例就不是权重的比例了，需要根据上面那段话自行计算比例了
	
[LinearLayout线性布局管理器layout_weight属性详解](http://blog.csdn.net/xiaanming/article/details/13630837)

#### release版本去掉log(关于ProGuard更深入的记录于Android进阶中Android Proguard单独文件)
[使用gradle进行打包，添加混淆配置将log输出删去](http://www.jianshu.com/p/4b61391a665f)

	ProGuard的作用：ProGuard读取输入的代码，进行压缩，优化，混淆三个操作（可以任意开启或关闭其中的任一个操作）


#### assets 文件的使用，assets文件夹中的文件在打包成apk时会原样打包进apk中，并且不会生成引用ID；
AssetManager manager=Context.getAssets();//获取AssetManager来调用assets文件夹中的文件；

问题：assets、res和raw单个文件夹路径的区别？


#### 子类的构造方法如果要引用super的话，必须把super放在函数的首位，注意是构造方法；

Activity的onCreate()、onStart()、onResume()方法要确保先执行父类的方法后，再执行自己要执行的操作逻辑；

如果子类和父类适当地隔离（子类资源依赖性方面），super.X()方法调用就不需要遵守任何执行顺序规范；

#### getWindow().addFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN);getWindow.clearFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN);

这两个方法可以在Activity中动态改变全屏与否；

	FLAG_FULLSCREEN
	Window flag: hide all screen decorations (such as the status bar) while this window is displayed;