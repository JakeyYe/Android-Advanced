	
##[Android打包那些事](http://www.jayfeng.com/2015/11/07/Android%E6%89%93%E5%8C%85%E7%9A%84%E9%82%A3%E4%BA%9B%E4%BA%8B/)

##[详解build.gradle](http://ask.android-studio.org/?/article/40)

##[安卓集成发布详解（二）](http://frank-zhu.github.io/android/2015/06/15/android-release_app_build_gradle/)
	apply plugin: 'com.android.application'//表示此Module是一个可运行的应用程序，可以直接run
	apply plugin: 'com.google.gms.google-services'
	//apply plugin:'com.android.library'//则表示此Module是Android依赖库的一个工程，不可直接run
	//apply plugin: 'java' //这表示此module是一个java项目，在此module中只能使用java的api

	android {
    compileSdkVersion 23
    buildToolsVersion "23.0.3"

    defaultConfig {
        applicationId "cn.rongcloud.im"
        minSdkVersion 14
        targetSdkVersion 23
        versionCode 2017041917
        versionName "2.8.10 Dev"

        //开启MultiDex
        multiDexEnabled true
		//设置所有渠道包只包括这两种指令集
        ndk {
            abiFilters "armeabi-v7a", "x86"
        }
    }

	//设置签名信息
    signingConfigs {
		//签名信息文件一，可以有多个，在buildTyes中任意调用一个
        config {
            storeFile file("rong.key")
            storePassword "Amigo123"
            keyAlias "RongCloud"
            keyPassword "Amigo123"
        }
    }
	//配置相关文件位置
    sourceSets {
        main {
            jni.srcDirs = []
			////将jniLibs下的文件/子文件目录 定义到与'src'同级的'libs'目录下
            jniLibs.srcDirs = ['libs']
        }
    }
	//配置APK包的相关属性
    packagingOptions {
		//The list of excluded paths.排除路径列表
        exclude 'AndroidManifest.xml'
    }

	//配置构建类型
    buildTypes {
        release {
			 // 不显示Log
            buildConfigField "boolean", "LOG_DEBUG", "false"
            //混淆
            minifyEnabled true
            //Zipalign优化
            zipAlignEnabled true

            // 移除无用的resource文件
            shrinkResources true
          	
			//指定签名类型文件为signingredientsConfig.config文件
            signingConfig signingConfigs.config //for release
			////前一部分代表系统默认的android程序的混淆文件，该文件已经包含了基本的混淆声明,后一个代表自定义混淆文件
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        debug {
            minifyEnabled false
            signingConfig signingConfigs.config //for release
        }
    }

	//设置Lint属性
    lintOptions {
        checkReleaseBuilds false

        abortOnError false
    }
    dexOptions {
        javaMaxHeapSize "4g"
    }
	}

	dependencies {
	//编译的文件树
    compile fileTree(include: ['*.jar'], dir: 'libs')
	//主Module依赖的库
    compile 'com.android.support:appcompat-v7:21.0.3'
    compile 'com.android.support:support-v4:21.0.3'
    //主Module依赖的library
    compile project(':Recognizer')
    //直接添加依赖
    compile 'com.android.support:multidex:1.0.1'
    //单个添加依赖的.jar文件
    compile files('libs/MiPush_SDK_Client_3_1_2.jar')
    
	//主Module引用的aar文件
    compile(name: 'HMS-SDK-2.4.0.300', ext: 'aar')
	}