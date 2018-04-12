## Android 图片操作总结

[解决Android拍照保存在系统相册不显示的问题 \- CSDN博客](https://blog.csdn.net/xiaanming/article/details/8990627)

将生成的Bitmap插入到手机的相册中，获取到图片路径，通过这个方法将图片放入系统相册中，但是不能指定文件名称，名称由系统使用一串数字表示；

	String filePath=MediaStore.Images.Meida.insertImage(getContentResolver(),bitmap,null,null);
	//注意：将图片放入系统相册中后将这个图片路径是不能通过QQ分享的，会提示这个文件错误，要通过QQ分享，只能将文件保存在一般目录里；
	
	
	
![Android中的图片的读取，显示](https://img-blog.csdn.net/20150514172932952)

[Android 图片文件读取 \- CSDN博客](https://blog.csdn.net/ccpat/article/details/45727427)