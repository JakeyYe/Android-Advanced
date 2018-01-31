## Android GestureDetector 手势监听

在View类中有个View.onTouchListener内部接口，通过重写它的onTouch(View v,MotionEvent event)方法，我们可以处理一些简单的Touch事件，但是这个方法并不能识别手势，如果需要处理一些复杂的手势，用这个接口就会很麻烦（因为我们需要自己根据用户触摸的轨迹去判断使什么手势），刚好 Android 为我们提供了 GestureDetector 类，通过它，我们可以轻松的进行复杂手势识别；

[Android:捕捉触摸屏手势详解 \- 泡在网上的日子](http://www.jcodecraeer.com/a/anzhuokaifa/androidkaifa/2012/1023/453.html)