## Activity 之间切换出现黑屏或白屏


在要启动的Activity的主题中添加该属性

	<style name=“startActivityTheme” parent=“AppTheme”>
 		<item name=“android:windowIsTranslucent”>true</item>
	</style>

设置这样的属性，是为了设置该 Activity 的背景色为透明的，在其 View 展示出来之前，看到的将会是前一个 Activity；


这个也涉及的启动应用时出现黑屏/白屏的情况； 

[Android Activity之间跳转出现短暂黑屏的处理方法 \- 简书](https://www.jianshu.com/p/feb14c61088d)