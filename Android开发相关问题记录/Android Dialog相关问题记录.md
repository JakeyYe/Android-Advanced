## Android Dialog 相关问题记录

Dialog和软键盘的遮挡问题，

注意：设置这个属性会导致Dialog和软键盘之间会有遮挡效果，所以不能设置该属性，或者将值设置为false;

	android:windowTranslucentStatus="true"//该属性设置的是将布局内容绘制到状态栏（StatusBar）上；