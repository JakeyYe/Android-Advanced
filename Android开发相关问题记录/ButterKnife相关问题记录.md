## ButterKnife相关问题记录

问题1：

在`xml`文件中使用`<include>`直接复用布局，如果在`<include>`中声明了id属性的话，使用`ButterKnife`将不能获取**复用布局中的控件**，去掉才可以；（其实这不算`是ButterKnife`的`bug`,而是`<include>`标签导致的，如果在`<include>`标签处声明了id的话，那么复用布局中`根View`设置的`id`就会无效，该`id`就会被动态切换为`<include>`标签中设置的`id`,所以调用原`id`会导致空指针异常）

[Bind view in include crash · Issue \#396 · JakeWharton/butterknife](https://github.com/JakeWharton/butterknife/issues/396)