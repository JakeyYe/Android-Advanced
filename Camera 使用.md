## Camera使用	


[Android Camera 相机开发详解 \- 简书](http://www.jianshu.com/p/7dd2191b4537)


#### ColorMatrix
Android中可以通过颜色矩阵（ColorMatrix）方面的操作颜色，颜色矩阵是一个5*4矩阵，可以用来修改图片的RGBA各分量的值，从而达到滤镜的效果。适合做静态图片的滤镜效果。

### 注意点：
- 为Camera重新设置预览分辨率时，如果Camera已经开启预览了，要先停止预览，配置完预览分辨率后，再重新开启预览。这样重新设置的配置才会生效。

- HSL和HSV都是在一种将RGB色彩模型中的点在圆柱坐标系中的表示法。
