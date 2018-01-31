## Android 视频播器的选择

视频播放原理：

系统会首先确定视频的格式，然后得到视频的编码，然后对编码进行解码，得到一帧一帧的图像，最后在画布上进行迅速更新，显然需要在独立的线程中完成，这时就需要使用 SurfaceView 了；

[基于ijkPlayer学习视频播放器实现（一） \| 阳春面的博客](https://appkfz.com/2017/08/27/ijkplayer-sutdy-1/)

### MediaPlayer+SurfaceView
 
MediaPlayer 主要用于音频播放的，没有提供图像界面输出，所以使用 SurfaceView 配合 MediaPlayer，将一帧一帧的图像，显示在界面上；

### VideoView

可以直接使用系统封装好的 VideoView 来播放视频；Android 提供了 VideoView 用来播放一些特定格式的视频文件，与 MediaController 结合使用可以对视频播放进行简单控制，不用开发者自己控制播放和暂停，直接调用播放或暂停的API方法即可；

VideoView 的使用 [\[Android基础\] VideoView \- 简书](https://www.jianshu.com/p/2d3b221a2ee7)


### ExoPlayer 
[google/ExoPlayer: An extensible media player for Android](https://github.com/google/ExoPlayer)

ExoPlayer 是一个扩展的媒体播放器，同时支持本地和网络视频播放，相比于 MediaPlayer，ExoPlayer 更加强大；


### ijkplayer

[Bilibili/ijkplayer: Android/iOS video player based on FFmpeg n3\.3, with MediaCodec, VideoToolbox support\.](https://github.com/Bilibili/ijkplayer)

ijkplayer 是 Bilbili 公司开源的播放器实现，整合了 FFMpeg,ExoPlayer等多种实现，提供了类似于 MediaPlayer 的API，是一个更加强大的视频播放器；

[在ubuntu下编译ijkplayer\-android \- CSDN博客](http://blog.csdn.net/u010072711/article/details/51438871)

基于ijkplayer 的Demo [基于ijkplayer\+Rxjava\+Rxandroid\+Retrofit2\.0\+MVP\+Material Design的android万能播放器 \- CSDN博客](http://blog.csdn.net/u010072711/article/details/51728537)

[\[Android\] Android 视频播放总结 – 技术学习小组](http://blog.qiji.tech/archives/7908)

### 开源库播放器参考

#### JiaoZiVideoPlayer
[JiaoZiVideoPlayer/README\-ZH\.md at develop · lipangit/JiaoZiVideoPlayer](https://github.com/lipangit/JiaoZiVideoPlayer/blob/develop/README-ZH.md)

#### GSYVideoPlayer

[Android 实现视频播放器（IJKPlayer） \- 开发者头条](https://toutiao.io/posts/nds5oe/preview)

[CarGuo/GSYVideoPlayer: 视频播放器（IJKplayer）](https://github.com/CarGuo/GSYVideoPlayer)



[\[Android\] Android 视频播放总结 – 技术学习小组](http://blog.qiji.tech/archives/7908)