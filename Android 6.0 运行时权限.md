# Android使用权限

	运行时权限获取分三个步骤：
	1，需要使用该权限时，检测权限是否已被授予，若未授予则进行第二步，已授予则直接结束；
	2，未授予，则申请权限，若是第一次申请权限，则直接申请，否则要额外调用一个方法说明申请权限的作用；
	3，检测申请权限的回调结果，根据结果（同意/拒绝权限申请）再做出不同动作。

#### [Android 6.0运行时权限](http://blog.csdn.net/lmj623565791/article/details/50709663)

## **如果使用原生代码自己申请权限的话，要注意在Activity与Fragment中申请权限调用的方法是不同的**
[Android 6\.0 运行时权限处理 \| 阳春面的博客](https://appkfz.com/2015/11/04/android-6-permission/)

### 每款Android应用都在访问受限的沙盒中运行。如果应用需要使用其沙盒外的资源或信息，则必需请求相应的权限。可以在清单文件中列出相应的权限，声明应用需要此权限。
###根据权限的敏感度，系统可能会自动授予权限，或者需要由设备用户对权限请求进行许可。例如，如果应用请求打开手电筒的权限，系统将自动授予，但如果是需要读取用户联系人，系统会要求用户授权。用户需要在安装应用时（运行Android 5.1,API 22或更低版本的设备）或者运行应用（运行Android 6.0,API 23或更高版本的设备）时授予权限，具体取决于平台设备。

- 如果设备运行的时 Android 6.0 （API 23）或更高版本，并且应用的targetSdkVersion是 23或更高版本，则应用在运行时向用户请求权限。用户可随时调用权限，因此应用在每次运行均需要检查自身是否具有所需的权限（**每次使用权限都要申请权限**）。
- 如果设备运行的是 Android 5.1（API 22）或更低版本，并且应用的targetSdkVersion是 22 或更低版本，则系统会在用户安装应用时询问用户是否授予权限。如果将新权限添加到更新的应用版本，系统会在应用更新安装时询问用户是否授予权限。**用户一旦安装应用，他们撤销权限的唯一方式是卸载应用**。

### 系统在开发者声明权限之后的行为取决于权限的敏感度。如果权限不影响用户隐私权，系统会自动授权（**但还是要在清单文件中声明**）。如果权限涉及到对用户敏感信息的访问，系统将要求用户批准。----来自[声明权限](https://developer.android.google.cn/training/permissions/declaring.html?hl=zh-cn)

## 这两种权限分为[正常权限和威胁权限](https://developer.android.google.cn/guide/topics/security/permissions.html?hl=zh-cn#normal-dangerous)。

## 所有危险的Android系统权限都属于权限组，同一个权限组中的所有权限只需申请其中的一个，如果申请成功，同一个权限组的其他权限系统会自动授予，不会再询问。

## 需要根据权限的敏感程度和软件安装的Android系统版本，对系统权限做出不同操作。
##[使用系统权限](https://developer.android.google.cn/training/permissions/index.html?hl=zh-cn)

## [权限的最佳做法](https://developer.android.google.cn/training/permissions/best-practices.html?hl=zh-cn)


#### RxPermission的使用解析

	RxPermission rxPermission=new RxPermission();
	rxPermission.request();

	rxPermission.requestEach();//两个方法请求动态请求权限

[tbruyelle/RxPermissions: Android runtime permissions powered by RxJava](https://github.com/tbruyelle/RxPermissions)

[使用RxPermissions（基于RxJava2） \- 程序园](http://www.voidcn.com/article/p-yzmdneib-bbb.html)