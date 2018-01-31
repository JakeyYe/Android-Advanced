## Android样式开发标签记录   

#### set这些标签，收集完整(记录于Android进阶中的Android样式开发单独文件)

[Android样式开发（小钢）](https://keeganlee.me/post/android/20150830)

#### RippleDrawable涟漪背景效果的Drawable

[Android L限制Ripple水波纹范围大小 \- CSDN博客](http://blog.csdn.net/kong92917/article/details/54291124)

#### style和theme的使用
 style属性设置范围小点，主要针对于控件View的，theme属性设置范围大点，主要针对Activity，Window的；

 View控件使用style是不需要加前缀的,不需要加命名空间前缀，<TextView id="@+id/tv" style="@style/tvStyle"/>

 而theme的使用是要加命名空间的，如 android：theme="@style/AppTheme"/>


#### 主题Theme，主要的主题属性：

android：windowBackground,这是Window的background；

android：windowNoTitle,去掉Window的Toolbar布局？？？

android：windowIsTranslucent，设置Window是否时半透明窗口；