## Android 6.0 运行时权限问题深究

运行时权限是在每次需要权限时就会弹出窗口询问是否授予？？？还是在一次程序运行的过程中第一次授予权限后，后面再需要该权限就不需要再授予权限了，没授予权限，就一直弹窗询问用户是否授予权限？

可是在 Android 原生系统测试中，发现也并不是每次都弹窗提示用户授予权限。

注意：使用系统 API 23 的 Android 原生系统手机测试发现，运行时权限也不是真的“运行时”申请权限，不是在每次需要该权限就弹窗询问用户是否授予权限，而是在第一次授予该权限后，后面再需要该权限就直接使用了，系统只需要再运行时让用户授予一次权限即可；国产手机系统还是有点奇怪的，拒绝一次权限申请后，就不会再提示权限申请了（应该是默认选中了“不再显示”的按钮），直接是拒绝权限状态，所以判断用户是否选中了“不再显示”这点要注意测试；

### Android 6.0 运行时权限申请的一些优雅操作：

使用运行时权限开源库 AndPermission
[用法 · GitBook](http://www.yanzhenjie.com/AndPermission/cn/usage.html)

1. 在第一次申请权限前，可以**弹框**提示用户为什么需要这个权限，用户同意后再去真正申请权限，被拒绝后，直接提示用户没有权限，无法进行下一步操作；若真正申请权限被拒绝后，再次申请前**弹框**告诉用户使用该权限的原因，防止用户直接拒绝权限并且选中“不再提示”按钮；
2. 当用户选中“不再提示”按钮时，再次申请权限，就弹出一个弹框，并给一个跳转到应用权限设置界面选项，方便用户重新赋予应用权限；

[目前最流行的运行时权限请求框架PermissionsDispatcher、RxPermissions和easypermissions的使用和对比 \- Android开发社区 \| CTOLib码库](https://www.ctolib.com/topics-119432.html)