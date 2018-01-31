## android-apt和annotationProcessor
	
	1，android-apt是一个Gradle插件，协助Android Studio处理annotation processors；
	2，annotationProcessor和android-apt的功能是一样的；
	3，APT(Annotation Processing Tool)是一种处理注释（注解）的工具，它对源代码文件进行检测找出其中的Annotation，根据注解自动生成代码；
	4，annotationProcessor是APT工具中的一种，它是Goolge开发的内置框架，不需要引入，可以直接在build.gradle文件中使用（需要设置Android Gradle插件为2.2以上）；

####JavaPoet
	JavaPoet是一个用来生成.java源文件的Java API。当做如注解或者数据库模式，协议格式等工作时，生成源文件就比较有用处。JavaPoet生成的源代码而不是字节码，所以可以通过阅读源码确保正确。

[JavaPoet的基本使用 \- crazy\_jack \- CSDN博客](http://blog.csdn.net/crazy1235/article/details/51876192)


#### APT处理要素：
	注解处理器（AbstractProcessor）+代码处理（JavaPoet）+处理器注册（AutoService）；
	APT（Annotation Processing Tool）是一种处理注解的工具,它对源代码文件进行检测找出其中的Annotation,根据注解自动生成代码。让APT发挥作用的最后一步是引入注解处理器（继承自
	AbstractProcessor的类），可以使用两个框架android-apt和annotationProcessor,这两个框架的作用相同，只需要使用一个即可，android-apt是一位开发者开源的框架，要使用需要引入该库，
	而annotationProcessor是Google官方提供的框架，升级Android Gradle插件到2.2以上就可以直接使用。


##### 注意点
	//第一个参数就是生成Java文件所在的位置，若为空则默认路径为ModuleName/build/generated/source/apt/degug/
	JavaFile javaFile=JavaFile.builder("",helloWorld)
                .build();

	使用annotationProcessor要将Android Gradle plugin设置为2.2.0以上,如这样设置classpath 'com.android.tools.build:gradle:2.3.0'
	
	AutoService主要的作用是注解processor类（继承自AbstractProcessor），并对其生成META-INF的配置信息。

	

[你必须知道的APT、annotationProcessor、android\-apt、Provided、自定义注解 \- 薛瑄的博客 \- CSDN博客](http://blog.csdn.net/xx326664162/article/details/68490059)

[Android编译期代码生成之apt实践入门 \- alighters](http://alighters.com/blog/2016/05/10/apt-code-generate/)