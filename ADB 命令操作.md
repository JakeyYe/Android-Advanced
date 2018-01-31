#ADB命令操作记录
---
###`ADB(Android Debug Bridge)`-Android调试桥工具位于`SDK`目录下的`platform-tools`文件夹下，它是一个非常强大的命令行工具，通过它可以与连接的`android`设备进行交互。


	adb命令：（直接在当前/xxx/User/下输入下面命令）

	adb version:查看adb的版本

	adb devices：获取模拟器或设备列表

	adb -s devicename shell :指定特定的设备devicename来进行adb shell操作，输入后就可以使用shell命令了。

	adb shell screenrecord /sdcard/demo.mp4 :录屏操作（输入命令后就开始录屏，按ctrl+c停止录屏，否则，到三分钟或--time-limit设置的时间限制时，录屏将自动停止）。

	adb shell screencap /sdcard/screen.png :截图操作


深入了解参考 [官方文档](https://developer.android.com/studio/command-line/adb.html#IntentSpec,)