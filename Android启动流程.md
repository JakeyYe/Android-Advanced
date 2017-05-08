#Android应用程序从Launcher启动流程如下所示：

 	/***************************************************************** 
  	* Launcher通过Binder告诉ActivityManagerService， 
 	 * 它将要启动一个新的Activity； 
  	****************************************************************/  
 	Launcher.startActivitySafely->    
 	Launcher.startActivity->    
  	//要求在新的Task中启动此Activity    
  	//intent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK)    
  	Activity.startActivity->    
  	Activity.startActivityForResult->    
  	Instrumentation.execStartActivity->    
   	// ActivityManagerNative.getDefault()返回AMS Proxy接口    
  	 ActivityManagerNative.getDefault().startActivity->    
  	 ActivityManagerProxy.startActivity->    
     
    ActivityManagerService.startActivity-> (AMS)    
    ActivityManagerService.startActivityAsUser->     
     
     ActivityStackSupervisor.startActivityMayWait->    
     ActivityStackSupervisor.resolveActivity(获取ActivityInfo)    
       //aInfo.name为main Activity,如：com.my.test.MainActivity    
       //aInfo.applicationInfo.packageName为包名，如com.my.test    
     ActivityStackSupervisor.startActivityLocked->    
       //ProcessRecord callerApp; 调用者即Launcher信息    
       //ActivityRecord sourceRecord; Launcher Activity相关信息    
       //ActivityRecord r=new ActivityRecord(...)，将要创建的Activity相关信息      
     ActivityStackSupervisor.startActivityUncheckedLocked->    
      //Activity启动方式：ActivityInfo.LAUNCH_MULTIPLE/LAUNCH_SINGLE_INSTANCE/    
      //             ActivityInfo.LAUNCH_SINGLE_TASK/LAUNCH_SINGLE_TOP)    
      // 创建一个新的task,即TaskRecord,并保存在ActivityRecord.task中    
      //r.setTask(new TaskRecord(mService.mCurTask, r.info, intent), null, true)    
      // 把新创建的Activity放在栈顶          
      ActivityStack.resumeTopActivityLocked-> 
	  ActivityStack.resumeTopActivityInnerLocked()->
      //又回调ActivityStackSupervisor类方法了   
      ActivityStackSupervisor.startSpecificActivityLocked()->
	  ActivityStackSupervisor.realStartActivityLocked()    
   
      /***************************************************************** 
       * AMS通过Binder通知Launcher进入Paused状态 
       ****************************************************************/  
       ApplicationThreadProxy.schedulePauseActivity->     
       //private class ApplicationThread extends ApplicationThreadNative    
       ApplicationThread.schedulePauseActivity->    
     
        ActivityThread.queueOrSendMessage->    
      
        // 调用Activity.onUserLeaveHint    
        // 调用Activity.onPause    
        // 通知activity manager我进入了pause状态    
        ActivityThread.handlePauseActivity->    
   
        /***************************************************************** 
         * Launcher通过Binder告诉AMS，它已经进入Paused状态 
         ****************************************************************/  
        ActivityManagerProxy.activityPaused->    
        ActivityManagerService.activityPaused->    
        ActivityStack.activityPaused->(把Activity状态修改为PAUSED)    
        ActivityStack.completePauseLocked->    
       
        // 参数为代表Launcher这个Activity的ActivityRecord    
        // 使用栈顶的Activity进入RESUME状态    
        ActivityStack.resumeTopActivityLokced->    
          //topRunningActivityLocked将刚创建的放于栈顶的activity取回来    
          // 即在ActivityStack.startActivityUncheckedLocked中创建的    
   
        /***************************************************************** 
         * AMS创建一个新的进程，用来启动一个ActivityThread实例， 
         * 即将要启动的Activity就是在这个ActivityThread实例中运行 
         ****************************************************************/  
        ActivityStack.startSpecificActivityLocked->    
     
         // 创建对应的ProcessRecord    
         ActivityManagerService.startProcessLocked->    
             
          // 启动一个新的进程    
          // 新的进程会导入android.app.ActivityThread类，并且执行它的main函数,    
          // 即实例化ActivityThread, 每个应用有且仅有一个ActivityThread实例    
          Process.start("android.app.ActivityThread",...)->    
   
          // 通过zygote机制创建一个新的进程    
          Process.startViaZygote->    
       
          // 这个函数在进程中创建一个ActivityThread实例，然后调用    
          // 它的attach函数，接着就进入消息循环    
          ActivityThread.main->    
   
          /***************************************************************** 
           * ActivityThread通过Binder将一个ApplicationThread类的Binder对象 
           * 传递给AMS，以便AMS通过此Binder对象来控制Activity整个生命周期 
           ****************************************************************/  
          ActivityThread.attach->    
          IActivityManager.attachApplication(mAppThread)->    
          ActivityManagerProxy.attachApplication->    
          ActivityManagerService.attachApplication->    
     
          // 把在ActivityManagerService.startProcessLocked中创建的ProcessRecord取出来    
          ActivityManagerService.attachApplicationLocked->    
   
          /***************************************************************** 
           * AMS通过Binder通知ActivityThread一切准备OK,它可以真正启动新的Activity了 
           ****************************************************************/              
          // 真正启动Activity    
          ActivityStack.realStartActivityLocked->    
          ApplicationThreadProxy.scheduleLaunchActivity->    
          ApplicationThread.scheduleLaunchActivity->    
          ActivityThread.handleLaunchActivity->    
            // 加载新的Activity类，并执行它的onCreate    
            ActivityThread.performLaunchActivity    
             /*1) Instrumentation.newActivity: 加载新类，即创建Activity对象；  
               2) ActivityClientRecord.packageInfo.makeApplication：创建Application对象；  
                  <LoadedApk.makeApplication>  
               3) Activity.attach(Context context, ActivityThread aThread,  
                     Instrumentation instr, IBinder token, int ident,  
                     Application application, Intent intent, ActivityInfo info,  
                     CharSequence title, Activity parent, String id,  
                     NonConfigurationInstances lastNonConfigurationInstances,  
                     Configuration config)：把Application attach到Activity, 即把Activtiy  
                                            相关信息设置到新创建的Activity中  
               4) Instrumentation.callActivityOnCreate：调用onCreate；*/    
       
            // 使用Activity进入RESUMED状态，并调用onResume    
            ActivityThread.handleResumeActivity    