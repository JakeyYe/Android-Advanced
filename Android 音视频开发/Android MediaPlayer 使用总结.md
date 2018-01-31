## Android MediaPlayer 使用总结


MediaPlayer类可用于控制音频/视频文件和流的播放；MediaPlayer 主要用于播放音频，没有提供图像输出界面，所以需要借助其他的组件来显示MediaPlayer播放的图像输出，我们可以使用 SurfaceView 来显示；

MediaPlayer:

- 状态图
- 有效和无效的状态
- 权限
- 注册信息和错误回调


状态图

音频/视频文件和流的播放控制作为状态机进行管理；

[android mediaPlayer的基本使用 \- 简书](https://www.jianshu.com/p/a849b5eb841d)


### 使用ViewView播放视频

Android 提供了这个封装好的控件，可直接用于视频播放；


[Android基础入门教程——9\.2 MediaPlayer播放音频与视频 \- Coder\-Pig的猪栏 \- CSDN博客](http://blog.csdn.net/coder_pig/article/details/49720337)