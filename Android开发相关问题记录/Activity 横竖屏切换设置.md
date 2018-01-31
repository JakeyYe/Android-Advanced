## Activity 横竖屏切换设置

	//TODO 如果直接在代码中调用这个方法会导致 Activity重启
     setRequestedOrientation(ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE);

要使Activity横竖屏切换不重启，需要在AndroidManifest.xml文件中对应Activity中添加onConfiguration属性，如下所示：

	android:configChanges="keyboardHidden|screenSize|orientation"

并在Activity中覆写onConfigChanges方法（不是并须的）；