## Android 多媒体之MediaStore

MediaSore是Android系统提供的一个多媒体数据库，Android系统会将系统中的多媒体文件的相关信息存储到系统中的这个数据库中，开发者直接通过ContentResolver即可对数据库进行操作，可以很方便地获取到系统中的多媒体文件；

[Android 多媒体之MediaStore \- CSDN博客](http://blog.csdn.net/wbwjx/article/details/70544881)

#### 通过MediaStore获取Android系统中的多媒体数据（图片，视频，音乐）

[Android获取本机各种类型文件列表（音乐、视频、图片、文档等） \- Chay\_Chan的博客 \- CSDN博客](http://blog.csdn.net/Chay_Chan/article/details/76984665)

#### 文件的几种操作
[java 实现文件/文件夹复制、剪切、删除 \- 蜗牛/ 的博客 \- ITeye博客](http://xqjay19910131-yahoo-cn.iteye.com/blog/1294119)

#### Android 删除文件夹中的图片并同步到媒体库中去

[Android 删除文件夹中的图片并同步到媒体库 \- CSDN博客](http://blog.csdn.net/mingyunxiaohai/article/details/72772126)

使用链接中的方法去更新媒体库，不是所有手机都有效，不过有个简单的方法解决，就是展示多媒体库中的文件时，先判断一下，文件是否为空；

MediaScannerConnection.scanFile()对单个文件多媒体库扫描，而不是对整个媒体文件进行扫描，这样是有效；
[android 媒体库数据更新解决办法总结 \- CSDN博客](http://blog.csdn.net/wurensen/article/details/44100029)

将对文件的操作，变为直接对多媒体数据库的操作，如直接操作多媒体数据库通过_id删除文件，这样就相当于更新了多媒体库了，这也是一种方法；
[android 图片添加时更新媒体库的方法 \- CSDN博客](http://blog.csdn.net/ddddwwww2/article/details/53162230)