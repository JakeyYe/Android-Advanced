## Java集合
[Collection是最基本的集合接口](http://www.jianshu.com/p/6227cfbc2a89)

### Java中有序和无序的概念：
	有序：是指存储顺序和添加顺序相同，并且可以通过下标访问，List就是这样。
	无序：刚好相反，指的是存储顺序与添加顺序无关，没有下标，当然也就不可以通过下标访问，Set就是这样的。

### List接口：List是有序的，且允许重复元素，能控制插入元素的位置
  LinkedList:双向链表实现的有序集合，非同步，允许null元素。链表，快速插入删除。
  ArrayList: 动态数组实现的可变大小的数组集合，非同步，允许null元素。数组，随机访问元素。
  Vector:类似与ArrayList,但是Vector是同步的。
  Stack:是继承自Vector,实现一个先进后出的堆栈。

### Set接口：Set是一种不包含重复元素的Collection，而且是无序的，Set最多允许有一个null元素

  HashSet：是基于HashMap实现的，HashSet底层采用HashMap来保存所有元素，不保证顺序，允许null元素。
  
  LinkedHashSet:是继承自HashSet的，是由哈希表和链表来实现的，元素顺序就是插入顺序。

  TreeSet：基于TreeMap的NavigableSet实现的，会对元素进行排序，是基于TreeMap实现的。






##Map接口：键值对存储的数据结构

  Hashtable:实现了一个key-value映射的哈希表，不允许null，同步的
  
  HashMap:与Hashtable类似，不同之处是HashMap是非同步的，并且允许null

  WeakHashMap：是一种改进的HashMap,它对key实现“弱引用”，如果一个key不再被外界所引用，那么该key可以被GC回收了。

  TreeMap：HashMap中所有元素都将保持着某种固定的顺序。在Map中插入，删除和定位元素，HashMap是最好的选择，但如果要按自然顺序或自定义顺序遍历，那么TreeMap会更好。

###[HashMap博客介绍1](http://www.cnblogs.com/chenssy/p/3521565.html)
###[HashMap博客介绍1](http://yikun.github.io/2015/04/01/Java-HashMap%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86%E5%8F%8A%E5%AE%9E%E7%8E%B0/)