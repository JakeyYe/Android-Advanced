## `Android` 布局优化之` ViewStub,include,merge` 使用


[Android布局优化之ViewStub、include、merge使用与源码分析 \- CSDN博客](http://blog.csdn.net/bboyfeiyu/article/details/45869393)

- include：为了解决重复定义相同布局的问题,使用include引入相同布局，而不必每次到写一次；

- ViewStub：延时加载，ViewStub就是一个宽高都为0的一个View，它默认时不可见的，这样在就可以优化布局；

- merge ：删减多余的层级，merge原理就是在解析XML的时候，如果是 `<merge/>` 标签，那么直接将其中的子元素添加到merge标签的parent中，这样就不会引入额外的层级了；


### <include>标签的一些注意事项：

- 引用该标签，关于id设置要注意；
- 该标签如果要设置一些其他属性的话，要先添加layout_width和layout_height这两个属性；


