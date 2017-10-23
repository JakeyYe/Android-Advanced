## Android应用中的文件目录

在data/data目录下存放每个应用程序的文件包目录，目录名就是应用程序在AndroidManifest.xml文件中定义的包。

在/data/data/<package name>/每个目录下，一般有这么几个子目录：

- databases:存放数据库；
- cache:存放缓存数据；
- files:存放应用程序自己控制的文件；
- lib:存放使用的包。
- shared_prefs:存放SharedPreference文件


Context context=this.getApplicationContext();

context.getCacheDir();//获取/data/user/0/Package Name/cache 目录

context.getDatabasePath("数据库名");//获取具体数据库存放目录，在databases目录之下,获取的路径为 /data/user/0/Package Name/databases/数据库名 

context.getFilesDir();//获取的路径 /data/user/0/Package Name/files 目录


//获取自身apk的路径，下面两个返回的路径是一样的

	context.getPackageCodePath();
	context.getPackageResoucePath();

参考： [Android应用程序的数据存放目录解说](http://blog.csdn.net/yihui823/article/details/6722456)


## 要注意Context和Environment这两个与内部存储和外部存储有关的类
如果按照路径特征，我们可以将文件存储的路径分为量大类，一类是路径中包含包名的，另一类是路径中不包含包名的，含有包名的路径，因为是和某个App有关，所以对这些文件夹的访问都是通过调用Context里的方法，而不包含包名的路径，和具体的某一个App无关，我们可以通过Environment中的方法来访问。

[android中的文件操作详解以及内部存储和外部存储](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2013/0923/1557.html)

	//判断SD卡是否挂载
	Environment.getEnternalStorageState().equals(Environment.MEDIA_MOUNTED);
[Android Environment类详解](http://blog.csdn.net/u010542873/article/details/51351708)

### [彻底理解Android内部存储和外部存储](http://blog.csdn.net/u012702547/article/details/50269639)


### Android系统文件目录结构

Google建议我们APP的数据存储在外部存储的私有目录中该APP的包名下，这样用户卸载APP之后，相关的数据会被一并删除，其中外部存储中的公有目录有九大类，比如DCIM,DOWNLOAD等这种系统为我们创建的文件夹，私有目录就是android这个文件夹；

	根目录 ： /

	/data
     /data 该目录存放所有安装应用的包（包名就是应用的包名）
          /应用包名 ------该文件夹下的文件都是该应用私有的（*内部存储*目录）
                   /cache  -------应用内缓存文件
		   		   /files  -------应用内普通文件
		           /databases -----应用内数据库文件
		           /shared_prefs --应用内的SharedPreferences文件



     /app 该目录存放着我们安装的的app的apk文件

	/mnt

	/storage ------------外部存储目录
		/sdcard(文件名可能不是这个，国产ROM可能会该名称)
				（以下几个目录，不包括android目录，是外部存储中的公有目录）
        	/DCIM     (XX公有目录--系统我们创建的文件夹)
        	/Download （下载公有目录--系统为我们创建的文件夹）
        	/Movies    (电影公有目录--系统为我们创建的文件夹)
        	/Music     （音乐公有目录--系统为我们创建的文件夹）
        	/Picture   （图片公有目录--系统为我们创建的文件夹）
			/android(Android)-------外部存储的私有目录
				/data  -----该文件夹下以包名为文件夹名作为每个应用的*外部存储*来存放文件
					/应有包名
