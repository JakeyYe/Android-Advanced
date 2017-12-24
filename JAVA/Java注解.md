# Annotation注解

### Annotation元注解
	Annotation（注解）就是Java提供了一种源程序中的元素关联任何信息或者任何元数据（mete data）的途径和方法。
	Annotation是被动的元数据，永远不会有主动行为。

元注解的作用就是负责注解其他注解，Java 5.0定义了4个标准的meta-annotation类型，它们被用来提供对其他Annotation类型作说明。
	
	4个元注解：
		1，@Target（描述作用目标对象）
		2，@Retention （描述作用生命周期范围）
		3，@Documented （描述是否记录在JavaDoc中）
		4，@Inherited（描述注解是否会被子类继承）
	这些类型和它们支持的类在java.lang.annotation包中可以找到。

	Annotation(注解)就是Java提供了一种元程序中的元素关联任何信息和着任何元数据（metadata）的途径和方法。
	Annotation是一个接口，程序可以通过反射来获取指定程序元素的Annotation对象，然后通过Annotation对象来获取注解里面的元数据。

	注解参数：
	参数成员只能用基本类型byte,short,char,int,long,float,double八种基本数据类型和
	String,Enum,Class,annotations等数据类型，以及这一些类型的数组。

	默认值：
	注解元素必需有确定的值，要么在定义注解的默认值中指定，要么在使用注解时指定，非基本数据类型默认值不能不能为null，所以使用
	空字符串或0作为默认值是一种常见的做法。
[Java注解（Annotation）](http://gityuan.com/2016/01/23/java-annotation/)

[深入理解Java:注解](http://www.cnblogs.com/peida/archive/2013/04/24/3036689.html)

### Annotation注解
	注解又分为两种类型，一种是编译期注解，另一种是运行期注解。编译期注解的核心原理依赖 APT（Annotation Processing Tools）实
	现的，例如著名的ButterKnife，Retrofit等开源库都是基于 APT的。
	编译时Annotation解析的基本原理是，在某些代码元素上（如类型，函数，字段等）添加注解，在编译时编译器会检查
	AbstractProcessor的子类，并且调用该类型的process函数，然后将添加了注解的所有元素都传递到process函数中，使得开发人员可
	以在编译期进行相应的处理，例如，根据注解生成新的Java类，这也就是ButterKnife等开源库的基本原理。

	APT(Annotation Processing Tool)是一种处理注解的工具，它对源代码文件进行检测找出其中的Annotation，使用Annotation进行
	额外的处理。Annotation处理器在处理Annotation时可以根据源文件中的Annotation生成额外的源文件和其他的文件（文件具体内容
	由Annotation处理器的编写者决定），APT还会编译生成的源文件和原来的源文件，将它们一起生成class文件。

[Android APT（编译时代码生成）最佳实践](http://www.tuicool.com/articles/aIfaum6) 要实践一下

### 注解处理器（Annotation Processor）
	注解处理器（Annotation Processor）是javac的一个工具，它用来在编译时扫描和处理注解（Annotation）。可以对自定义注解，
	并注册相应的注解处理器。
	一个注解的注解处理器，以Java代码（或者编译过的字节码）作为输入，生成文件（通常是.java文件）作为输出。
	注解处理器是运行它自己的虚拟机JVM中的，javac启动一个完整的Java虚拟机来运行注解处理器。

### 虚处理器AbstractProcessor
	自定义的每个注解处理器都是需要继承自AbstractProcessor的。

### 通过注解注入依赖
	method.getAnnotation(AnnotationName.class);//获取方法上的注解
	method.getAnnotations();//获取方法上的所有注解
	method.isAnnotationPresent(AnnotationName.class);//判断方法上是否有该类注解

[公共技术之Java注解](http://a.codekk.com/detail/Android/Trinea/%E5%85%AC%E5%85%B1%E6%8A%80%E6%9C%AF%E7%82%B9%E4%B9%8B%20Java%20%E6%B3%A8%E8%A7%A3%20Annotation)