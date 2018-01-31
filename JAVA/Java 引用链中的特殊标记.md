## Java 引用链中的特殊标记

[Java 内部类、成员类、局部类、匿名类等 \- CSDN博客](http://blog.csdn.net/a327369238/article/details/52780442)

Java 引用链 **this$0  Main$1.class  Other$Inner.class**

### this$0 this$1 this$2 

这些是内部类所自动保留的一个指向外部类的引用；

[java中this$0的含义及用法 \- fit for java \- ITeye博客](http://nrg19840409.iteye.com/blog/1216036)

this$0 特指该内部类所在的外部类的引用，就是内部类所自动保留的一个指向所在外部类的引用，每一个内部类都有一个指向所在最近的外部类的一个引用，只不过该引用不需要手动添加，编译器会复杂添加；

或者说： 在非static（静态）的inner class（内部类）里面都会有一个this$0的字段来保存它的父对象，在Java中，非静态（匿名）内部类会默认隐性引用外部类对象，而静态类则不会引用外部类对象；

匿名内部类（Anonymous Inner Class）的两种实现方式：

1. 继承一个类，重写其方法；
2. 实现一个接口，实现其方法；


一个匿名内部类一定是在 **new** 的后面，用其隐含实现一个接口或实现一个类；匿名类最常见的使用方式就是接口回调模式的使用，通过默认实习那一个接口创建一个匿名类，然后**new**这个匿名类作为事件回调接口对象；


### Other$Inner.class

	public class Other{
	  class Inner{
	     public Inner{}
	  }
	}

外部类和内部类的关系，$后面的类是$前面的类的内部类；

### Other$1.class

	public Interface Test{
		public void test();
	}
	
	public class Outer{
	   public Test test1=new Test(){	
			public void test(){
			   System.out.println("test1");
			}
	   }
	 
	}

是Other类中的一个接口匿名类，对于接口和抽象类是不能实例化的，我们说不出这个类的名，就叫它匿名类；

Other$1.class,表示Other类成员中匿名内部类别，1这个是编号，它表示位于方法中的第一个匿名内部类，匿名类没有名称，所以只有编号；

[class$1,class$2,class$innerclass中的$的含义 \- CSDN博客](http://blog.csdn.net/moonsheep_liu/article/details/41673369)

