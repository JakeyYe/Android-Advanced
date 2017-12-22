## ButterKnife相关问题记录

问题1：

在xml文件中使用<include>直接复用布局，如果在<include>中声明了id属性的话，使用ButterKnife将不能获取复用布局中的控件，去掉才可以；（其实这不算是ButterKnife的bug,而是<include>标签导致的，如果在<include>标签处声明了id的话，那么复用布局中根View设置的id就会无效，所以会导致空指针异常）

[Bind view in include crash · Issue \#396 · JakeWharton/butterknife](https://github.com/JakeWharton/butterknife/issues/396)