# Android进程和线程

##1, 进程和线程

### 默认情况下，同一应用的所有组件在相同的进程和线程（称为“主”线程）中运行，也可以安排同一应用的其他组件在单独的进程中运行，并为任何进程创建额外的线程。

### `android:process`属性可以使组件运行在新创建的进程里。

##2, 进程生命周期

### 前台进程

### 可见进程

### 服务进程

### 后台进程

### 空进程

###          Android系统会根据以上进程类型的重要程度，在内存情况紧张的时候销毁某个进程。

##3, 线程

### 应用启动时会创建一个名为“主线程（UI线程）”的执行线程，词线程非常重要，因为它负责将事件分配给相应的用户界面小组件，其中包括绘图事件。此外，它也是应用与Android UI工具包组件（android.widget和android.view包中的组件）进行交互的线程，因此它也被称为“UI线程”。

### 运行在同一进程的所有组件均在UI组件中实例化，并且对每个组件的系统调用均由该线程进程分派。

### Android UI工具包并非线程安全工具包，因此，不能通过工作线程来操作UI，而只能通过UI线程操作用户界面，因此，Android的单线程模式必须遵守两条规则：

  1)，不要阻塞UI线程

  2)，不要在UI线程之外访问Android UI工具包中的组件

###Android提供了几种途径来从其他线程访问UI线程的方法：

  1).`Activity.runOnUiThread(Runnable)`

  2).`View.post(Runnable)`

  3).`View.postDelayed(Runnable,long)`

##4, 进程间通信

###Android 利用远程过程调用 (RPC) 提供了一种进程间通信 (IPC) 机制，通过这种机制，由 Activity 或其他应用组件调用的方法将（在其他进程中）远程执行，而所有结果将返回给调用方

  ​
###参考  [官方文档](https://developer.android.com/guide/components/processes-and-threads.html?hl=zh-cn#Processes)
  ​