## Android OpenGL

	Android中有个专门用于显示OpenGL的3D图View:GLSurfaceView，GLSurfaceView会处理OpenGL初始化过程中比较基本的操作，如配置显示设备，以及在后台线程中渲染工作。

	GLSurfaceView是用于显示3D模型的视图，也就是用来显示3D图形的画布。


### OpenGL(Open Graphics Library)

	OpenGL（开放图形库）是用于渲染2D、3D矢量图形的跨语言、跨平台的应用程序编程接口（API）。

	OpenGL纯粹专注于渲染，而不提供输入、音频以及窗口相关的API。

	矢量图形是计算机图形学中用点、直线或者多边形等基于数学方程的几何图元表示图像。矢量图形与使用像素表示图像的位图不同。

### OpenGL ES(OpenGL for Embedded Systems)
	OpenGL ES是OpenGL三维图形API的子集，针对手机，PDA和游戏主机等嵌入式设备而设计的。
[OpenGL ES \| Android Developers](https://developer.android.com/guide/topics/graphics/opengl.html)

[安卓 OpenGL ES 2\.0 完全入门（一）：基本概念和 hello world \- Piasy的博客 \| Piasy Blog](https://blog.piasy.com/2016/06/07/Open-gl-es-android-2-part-1/)


### OpenCV和OpenGL的区别
	OpenCV主要是提供图像处理和视频处理的基础算法库，还涉及一些机器学习的算法。比如你想实现视频的降噪、运动物体的跟踪、目标（比如人脸）的识别这些都是CV的领域;
	OpenGL则专注在Graphics，3D绘图。
	其实两者的区别就是Computer Vision和Computer Graphics这两个学科之间的区别，
	前者专注于从采集到的视觉图像中获取信息，是用机器来理解图像；后者是用机器绘制合适的视觉图像给人看

	作者：李智辉
	链接：https://www.zhihu.com/question/20212016/answer/14468287
	来源：知乎
	著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

	Opencv是从图像到数据
	OpenGL是从数据到图像

	一个是让机器识别东西的，OpenCV是给电脑做眼睛的
	一个是让机器计算出更好画面的，OpenGL用在游戏渲染方面很多