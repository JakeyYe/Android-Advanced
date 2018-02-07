## startActivityForResult()方法相关问题记录

### 注意点：

1）requestCode应该大于0

2）setResult()应该在finish()方法之前调用，或者在onBackground()方法中的super.onBackground()方法之前调用

3）启动的Activity的启动模式，要是stardard标准模式，不能使用singleInstance或者singleTask启动模式

	//第二个参数一定要大于0
	startActivityForResult(Intent intent,int requestCode);
	onActivityResult(int requestCode,int resultCode,Intent data);
	//RESULT_OK,RESULT_CANCEL，setResult()方法要在finish()方法前被调用（可以看源码，源码能说明原因）
	setResult(int resultCode);
	//可以通过该方法的第二个参数返回一些数据，返回的这个Intent对象是从onActivityResult()这个方法的第三个参数获取，而不是直接通过getIntent()方法获取
	setResult(int resultCode,Intent data);
	

[Activity中onActivityResult存在的坑 \| 道听途说](http://dalufan.com/2016/01/03/android-activity-onActivityResult/)