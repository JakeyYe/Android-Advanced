# Android四种异步处理消息机制

*参考 `https://developer.android.com/guide/components/processes-and-threads.html?hl=zh-cn#IPC `*

### `View.postXXX()` View的post类型方法是View的异步通信的方法。

`View.post() , View.postDelayed() , View.postInvalidate()`

表示的方法作用都是`Causes the Runnable to be added to the message queue`

将该线程加到主线程的消息队列中。

其原理是把Runnable回调函数，post到主线程的消息队列里去，并将其包装成一个android有效的message对象，供位于主线程中的handler来处理，从而实现的主线程中更新这一view。

### Android  Handler异步消息处理机制

Android的异步消息机制，即是：Handler+Message+MessageQuene+Looper等的关系，这里面的关系简单来说就是主线程，不同于普通线程，它是一个消息循环线程，它内部有个looper，在循环维持一个MessageQuene，里面是按FIFO的原理管理着Message队列，并从Handler（在主线程中创建，并绑定到主线程，也就是说是普通创建方式，并没有加于looper）接收发送过来的消息，同时从队列尾部一个个把消息拿出来，供与其绑定的handler来处理，这里handler自己发送消息，绕了一大圈后，还是自己来处理，所以说是异步的，而handler同样是在主线程中来处理UI的。

Handler负责发送和处理消息

Looper负责管理MessageQueue,负责放进和取出Message到MessageQueue中

Message 表示消息对象

MessageQueue 是个队列，先进先出，负责存放多个Message对象.

####Handler的两种使用方式

	一， 定义一个Handler类，用于处理接受到的Message。
	Handler handler = new Handler() {
    public void handleMessage(Message msg) {
        // 要做的事情
        super.handleMessage(msg);
    }
	};
	2. 新建一个实现Runnable接口的线程类，如下：
	public class MyThread implements Runnable {
	@Override
	public void run() {
		// TODO Auto-generated method stub
		while (true) {
			try {
				Thread.sleep(10000);// 线程暂停10秒，单位毫秒
				Message message = new Message();
				message.what = 1;
				handler.sendMessage(message);// 发送消息
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
	  }
	}
	3. 在需要启动线程的地方加入下面语句：
	new Thread(new MyThread()).start();



	二， 采用Handler的postDelayed(Runnable, long)方法
	这个实现比较简单一些。
	1. 定义一个Handler类
	Handler handler=new Handler();
	Runnable runnable=new Runnable() {
    @Override
    public void run() {
        // TODO Auto-generated method stub
        //要做的事情
        handler.postDelayed(this, 2000);
     }
	};
	2. 启动
	handler.postDelayed(runnable, 2000);//每两秒执行一次runnable. 
	3. 停止
	handler.removeCallbacks(runnable); 

### 使用`AsyncTask`进行异步操作

`AsyncTask` 允许对用户界面执行异步操作。它会先阻塞工作线程中的操作，然后在 UI 线程中发布结果，而无需您亲自处理线程和/或处理程序。

要使用它，必须创建 `AsyncTask` 子类并实现 `doInBackground()` 回调方法，该方法将在后台线程池中运行。要更新 UI，必须实现 `onPostExecute()` 以传递 `doInBackground()` 返回的结果并在 UI 线程中运行，这样，您即可安全更新 UI。稍后，您可以通过从 UI 线程调用 `execute()` 来运行任务。

下面简要概述了 AsyncTask 的工作方法，但要全面了解如何使用此类，您应阅读 `AsyncTask` 参考文档：

- 可以使用泛型指定参数类型、进度值和任务最终值
- 方法 `doInBackground()` 会在工作线程上自动执行
- `onPreExecute()`、`onPostExecute()` 和 `onProgressUpdate()` 均在 UI 线程中调用
- `doInBackground()` 返回的值将发送到 `onPostExecute()`
- 您可以随时在 `doInBackground()` 中调用`publishProgress()`，以在 UI 线程中执行 `onProgressUpdate()`
- 您可以随时取消任何线程中的任务


### Activity.runOnUiThread(Runnable)

这也是Android提供的一中异步更新UI组件的方法。在UI线程上运行指定的操作，如果当前线程是UI线程，则立即执行动作。如果当前线程不是UI线程，则将操作发布到UI线程的事件队列。

## 以上其他三种方法实质上都是用Handler实现的，只不过都将Handler封装了一下。

类似总结：`http://www.jianshu.com/p/8e756803211f`






