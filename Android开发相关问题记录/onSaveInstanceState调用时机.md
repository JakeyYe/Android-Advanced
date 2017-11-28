## onSaveInstanceState相关问题记录

#### onSaveInstanceState调用时机

onSaveInstaceState()方法是**当Activity被系统主动kill掉时**，才调用，而不是每次都调用，比如Activity主动结束自己时就不会调用该方法；

如果onSaveInstanceState()方法被调用，则会在onStop()方法之前被调用，不保证是在onPause()方法之前或之后调用；

如果调用了onSaveInstanceStae()方法来保存Activity中的信息，那就会调用方法来恢复这些信息，可以在onCreate(Bundle savedInstanceState)方法来恢复，也可以在onRestoreInstaceState(Bundle saveInstanceState)方法来恢复，该方法会在onStart()方法和onPostCreate()方法之间被调用，onCreate()和onRestoreInstanceState()两个方法都可以用户恢复状态，所以**只需要在其中一个方法进行恢复操作即可**；

可以看看[Android源码解析（二十四）\-\->onSaveInstanceState执行时机 \- CSDN博客](http://blog.csdn.net/qq_23547831/article/details/51464535)


#### onCreate,onStart,onResume三个方法的区别

- onCreate Activity创建就应该创建的
- onStart Activity可见就应该创建的
- onResume Activity与用户交互时应该创建的

#### onPostCreate,onPostResume两个方法

#### Can not perform this action after onSaveInstanceState异常总结

在onSaveInstanceState方法保存Activity状态之后，onRestoreInstanceState方法恢复状态之前，这段时间里程序就不能操作window，否则将抛出该异常；

[解决Can not perform this action after onSaveInstanceState异常总结 \- CSDN博客](http://blog.csdn.net/Rflyee/article/details/74723891)
