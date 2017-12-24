## 继承
子类可以继承父类中的属性成员和除构造方法以为的成员方法，但不能继承父类的构造方法，继承了但是不一定有访问权限，子类对父类的private成员没有访问权限，对public和protected成员具有访问权限。Java中一个类只有一个父类，但是可以继承多个接口。

## 抽象类
抽象类里面的方法不需要全部声明为抽象方法，构造方法不能是抽象方法。
抽象类可以没有抽象方法。
有抽象方法的类一定要声明为抽象类。
抽象类的访问权限有public和缺省两种。

## 接口
接口中只有全局常量和公有的抽象方法。全部的权限会隐式地声明为public，接口的访问权限只有public。

可以在抽象类中定义方法的默认行为，但是接口的方法不能拥有默认行为。
如果要表示的两类事物在本质上是相同的，则使用继承；如果要表示的两类事物在本质上是不同的，则使用接口。

## try-catch-finally结构
在catch中，如果要捕获的异常类之间没有继承关系，各个catch块之间的顺序则无关紧要，但如果它们之间有继承关系，则应将子类的catch块放在父类的catch块之前，因此，Exception这个异常的根类（最高级别异常类）一定要放在最后一个catch块中。
finally语句块是可选的，无论是否发生异常，finally语句块总会执行，所以一般用来释放资源，关闭文件等操作。

### throw
如果不想在当前方法中抛出异常，可以使用throw语句将异常抛出到调用方法中。
如： throw new ExceptionType(异常信息) 


### throws
为了明确指出一个不捕获某异常，而让调用该方法的其他方法捕获该异常类异常，可以在方法声明的时候，使用throws语句来抛出该类异常。

Error类代表错误，指程序中无法恢复的异常情况。对于所有的错误类型及其子类，都不要求程序进行处理。
Exception类代表异常类，指程序中有可能恢复的异常情况。



## Java最顶层的的根类是Object，它是所有类的祖先类，都是直接或间接继承它的。


## Java内部类：静态内部类，成员内部类，局部内部类，匿名内部类
### 1，内部类可直接访问外部类的私有属性，但是外部类要访问内部类的成员属性和方法则需要通过内部类实例来访问。
	举例：
	public class OuterClass {
    private String name ;
    private int age;

    /**省略getter和setter方法**/
    
    public class InnerClass{
        public InnerClass(){
            name = "chenssy";
            age = 23;
        }
        
        public void display(){
            System.out.println("name：" + getName() +"   ;age：" + getAge());
        }
    }
    
    public static void main(String[] args) {
        OuterClass outerClass = new OuterClass();
        OuterClass.InnerClass innerClass = outerClass.new InnerClass();
        innerClass.display();
    }
	}
	--------------
	Output：
	name：chenssy   ;age：23

### 2，内部类可直接返回外部类的引用
	举例：
	public class OuterClass {
    public void display(){
        System.out.println("OuterClass...");
    }
    
    public class InnerClass{
        public OuterClass getOuterClass(){
            return OuterClass.this;
        }
    }
    
    public static void main(String[] args) {
        OuterClass outerClass = new OuterClass();
        OuterClass.InnerClass innerClass = outerClass.new InnerClass();
        innerClass.getOuterClass().display();
    }
	}
	-------------
		Output:
	OuterClass...

### 3，成员内部类，就是作为外部类的成员，可以直接使用外部类的所有成员和方法，即便是私有的。
### 4，局部内部类，是定义在一个方法或者一个作用域里面的类，它与成员内部类的区别在于局部内部类的访问仅限于方法内或该作用域内。
### 5，静态类是不需要依赖外围类的，而非静态类是需要依赖外围类创建而创建的，静态内部类只能访问外部类的静态成员变量，具有一定的局限性。。

#### 参考 [Java提高篇之内部类](https://www.cnblogs.com/chenssy/p/3388487.html)