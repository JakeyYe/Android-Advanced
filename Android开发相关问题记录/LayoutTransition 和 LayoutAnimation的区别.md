## LayoutTransition 和 LayoutAnimation的区别

[Android属性动画Property Animation系列三之LayoutTransition（布局容器动画） \- CSDN博客](https://blog.csdn.net/feiduclear_up/article/details/45919613)

LayoutTransition,布局管理器过渡动画，是API Level 11才出现的，LayoutTransition的动画效果，只有当ViewGroup中有View添加、删除、隐藏的时候才会展示动画效果，也就是ViewGroup中单个child的动画效果；

LayoutAnimation在API Level 1中就有了，LayoutAnimation是对于ViewGroup父控件中所有的child view的操作，也就是说它是用来控制ViewGroup中所有的child view的显示动画，也就是同时作用于父布局中的所有子View，多用于ListView中，设置Item出现的动画效果；