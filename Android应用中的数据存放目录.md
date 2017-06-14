##Android应用中的文件目录

在data/data目录下存放每个应用程序的文件包目录，目录名就是应用程序在AndroidManifest.xml文件中定义的包。

在/data/data/<package name>/每个目录下，一般有这么几个子目录：

- databases:存放数据库；
- cache:存放缓存数据；
- files:存放应用程序自己控制的文件；
- lib:存放使用的包。
- shared_prefs:存放SharedPreference文件


Context context=this.getApplicationContext();
context.getCacheDir();//获取/data/data/<package name>/cache目录

context.getDatabasePath("数据库名");//获取具体数据库存放目录，在databases目录之下
context.getFilesDir();//获取/data/data/<package name>/files目录


//获取自身apk的路径
context.getPackageCodePath();
context.getPackageResoucePath();

参考： [Android应用程序的数据存放目录解说](http://blog.csdn.net/yihui823/article/details/6722456)

