## SurfaceView解析
	
`SurfaceView`的大概原理就是在现有的`View`的位置上创建一个新的`Window`，内容的显示和渲染都在新的Window中，这使得`SurfaceView`的绘制和刷新可以在单独的线程中进行，从而大大提高效率；但是，由于`SurfaceView`的内容没有显示在View中而是显示在新建的`Window`中，使得`SurfaceView`的显示不受`View`的属性控制，不能进行平移，缩放等变换，也不能放在其他`RecyclerView`或`ScrollView`中，一些`View`的特性也无法使用。

### TextureView
TextureView是在4.0（API 14）引入的，与SurfaceView相比，它不会创建新的窗口来显示内容，它是将内容流直接投放到View中，并且可以和其他普通View一样进行移动，旋转，缩放，动画等变化，TextureView必须在硬件加速的窗口中使用。