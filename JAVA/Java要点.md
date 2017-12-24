### 一，关系运算符（==）对于String这种非基本类型的对象，判断的是对象的地址而不是值，基本数据类型判断的是值。而Object基类提供的equal()方法也是比较内存地址的（看源代码），我们很大程度比较对象需要的就是比较对象的值是否相等，所以非基本数据类型一般都会覆写equal()方法（基本数据类型不是类所以也没有方法），使其比较的是值而不是地址，比如String的equal方法。对象可以用==来判断地址，用equals()方法判断对象值是否相同，而对于基本数据类型是通过==来判断的是对象的内容。注意直接通过赋值的String类型变量，对象池。

### 二，java.lang.Error和java.lang.Exception继承java.lang.Trowable,RuntimeException和其他的Exception等继承Exception.
	扩展：错误和异常的区别(Error vs Exception) 

	1) java.lang.Error: Throwable的子类，用于标记严重错误。合理的应用程序不应该去try/catch这种错误。绝大多数的错误都是非正常的，就根本不该出现的。
	java.lang.Exception: Throwable的子类，用于指示一种合理的程序想去catch的条件。即它仅仅是一种程序运行条件，而非严重错误，并且鼓励用户程序去catch它。
	2)  Error和RuntimeException 及其子类都是未检查的异常（unchecked exceptions），而所有其他的Exception类都是检查了的异常（checked exceptions）.
	checked exceptions: 通常是从一个可以恢复的程序中抛出来的，并且最好能够从这种异常中使用程序恢复。比如FileNotFoundException, ParseException等。

	  已检查异常:编译器会在编译阶段就进行检查，必须要使用try…catch（或者throws）否则编译不通过。
	  未检查异常unchecked exceptions: 通常是如果一切正常的话本不该发生的异常，但是的确发生了。发生在运行期，具有不确定性，
	主要是由于程序的逻辑问题所引起的，这部分异常是不需要捕获的，但是也可以捕获，这样方便后面查找问题，比如Android的UncaughtExceptionHandler。

	比如ArrayIndexOutOfBoundException, ClassCastException等。从语言本身的角度讲，程序不该去catch这类异常，虽然能够从诸如RuntimeException这样的

	异常中catch并恢复，但是并不鼓励终端程序员这么做，因为完全没要必要。因为这类错误本身就是bug，应该被修复，出现此类错误时程序就应该立即停止执行。 

	因此，面对Errors和unchecked exceptions应该让程序自动终止执行，程序员不该做诸如try/catch这样的事情，而是应该查明原因，修改代码逻辑。

### RuntimeException：RuntimeException体系包括错误的类型转换、数组越界访问和试图访问空指针等等。处理RuntimeException的原则是：如果出现 RuntimeException，那么一定是程序员的错误。例如，可以通过检查数组下标和数组边界来避免数组越界访问异常。其他（IOException等等）checked异常一般是外部错误，例如试图从文件尾后读取数据等，这并不是程序本身的错误，而是在应用环境中出现的外部错误。 


### 小知识点，constructor就是构造方法，关系型数据库Oracle,MySql

### 三，Thread类的start()和run()方法的区别：
	start()方法是用来启动一个线程的，当调用start方法后，系统才会开启一个新的线程，然后调用run()方法

	来执行任务，而单独调用run()方法就跟调用普通方法是一样的，已经失去了线程的特性，因此启动一个线程一定要用start()而不是run().


### 四，Java异常处理：
	在Java中所有捕获范围小的异常要在捕获异常范围大的异常之前，否则在编译时就会出现错误提示。
	
	当有多个catch语句时，catch语句在次序上有先后之分,子类的异常类要在父类的异常类之前，比如Exception就应该放在最后。
	从最前面的catch语句块依次先后进行异常类型匹配，如果在前面的子异常匹配成功，后面的父异常就不会再匹配了。


### 小知识点
- Java的字符类型采用的是Unicode编码，Java的各种数据类型占用固定长度，与具体的软硬件平台无关。

- Java的IO操作有面向字节（Byte）和面向字符（character)两种方式。
- Java的代码行语句必须放到方法中或静态代码块中。类里面只能有方法体和域变量，这是语法问题，Java规定的。

- java是强类型语言，编译器会检查有无赋值。类成员变量可以不赋值是因为如果你没赋值，那么当类初始化时会由系统自动赋值 。
 但是在其他地方就不行，一定要先初始化或赋值，才可以使用，比如在main函数里，不然编译是不会通过的。

- Java public类中静态代码块会先于main主方法执行。


- Java一个类的类方法就是指静态方法，而实例方法是指该类中的除了静态方法的其他方法，也就是非静态方法。（专有名称啊）

### getClass()方法返回的是运行期的类名,而instanceof 是直接判断前者是不是后者—类的对象或子类对象。

	Baseclass baseclass1=new  Extendclass();  
   	Baseclass baseclass2=new  Baseclass();  
   	System.out.println(baseclass1.getClass().getSimpleName());//实际运行的是继承类Extendclass   
  	System.out.println(baseclass2.getClass().getSimpleName());//实际运行的是Baseclass   

    输出：
	Extendclass
	baseclass

2017/3/14 15:55:50 