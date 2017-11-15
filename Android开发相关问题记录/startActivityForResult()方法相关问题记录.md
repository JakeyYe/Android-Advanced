## startActivityForResult()方法相关问题记录

### 注意点：

1）requestCode应该大于0

2）setResult()应该在finish()方法之前调用，或者在onBackground()方法中的super.onBackground()方法之前调用

3）启动的Activity的启动模式，要是stardard标准模式，不能使用singleInstance或者singleTask启动模式

[Activity中onActivityResult存在的坑 \| 道听途说](http://dalufan.com/2016/01/03/android-activity-onActivityResult/)