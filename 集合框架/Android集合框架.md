## Android集合框架
	Object.hashCode()方法对于一个类的两个实例返回的是不同的哈希值
### WeakHashMap(WeakReference)
- 基于哈希表的Map结构的实现
- 线程不安全
- 内部映射无序
- 允许值为null的key和value
- 当WeakHashMap中的键不再有其他的强引用时，此键表示的键值对会被GC回收

[java\_集合体系之WeakHashMap详解、源码及示例——11 \- CSDN博客](http://blog.csdn.net/crave_shy/article/details/17611009)


### Java集合框架
1，HashMap

	HashMap内部是使用一个默认容量为16的数组来存储数据，而数组中的每一个数据却又是一个链表的头结点，更准确的来说，HashMap内部存储结构是使用哈希表的拉链结构（数组+链表）；HashMap中处理hash冲突的
	方法是链地址法（将同一个数组位置的值组成一个链表）；HashMap有两个重要元素：初始容量和加载因子

	  HashMap是不同步的，键和值都可以为空，而且键值对条目顺序是无序的；
	  HashMap是一种基于哈希表（hash table）实现的map,哈希表（也称关联数组）是一种通用的数据结构，其概念是：key经过hash函数作用后得到一个槽（bucket或slots）的索引
	（index），槽中保存着我们想要取得的值。

[Java HashMap 源码解析 \| Keep Writing Codes](http://liujiacai.net/blog/2015/09/03/java-hashmap/)

[Java 集合系列11之 Hashtable详细介绍\(源码解析\)和使用示例 \- 如果天空不死 \- 博客园](http://www.cnblogs.com/skywang12345/p/3310887.html)

2,ArrayList,LinkedList,HashMap

[Android 常用数据结构解析](http://deeporiginalx.com/news-share/?nid=24738124&source=7)

### Android特有的数据结构
1,SparseArray

	SparseArray是映射Integer->Object类型的，也就是<Integer,Object>格式的HashMap，就像这样：SparseArray<Object>，而且在指数级别数量的增长上来说和HashMap
	相比，性能方面SparseArray更好；它避免了对key的自动装箱（int转为Integer类型），故效率更高；还有就是内部查找使用的是二分查找算法，所以快；它内部对数据还采取了压缩的方式来表示稀疏数组的数据，
	从而节约内存空间，从源码中可以看出key和value分别是用数组表示的；SparseArray存储的元素都是按元素的key值从小到大排列好的（二分查找算法需要先排好序）；使用的数据量不大，最好在千级以内；

	HashMap<Integer, Object> map = new HashMap<>();
	用SparseArray代替:
	SparseArray<Object> array = new SparseArray<>();

[Android内存优化（使用SparseArray和ArrayMap代替HashMap） \- 【博客地址永久迁移到】：http://zhengxiaoyong\.me \- CSDN博客](http://blog.csdn.net/u010687392/article/details/47809295)

2,ArrayMap

	ArrayMap是一个<key,value>映射的数据结构，它设计上更多的是考虑内存的优化，内部使用两个数组进行数据存储，一个数据记录key的hash值，另外一个数组记录value值，它和SparseArray一样，也会对二分法
	进行从小到大排序，内部也是使用二分查找算法；使用的数据量不大，最好在千级以内；

	ArrayMap<Key, Value> arrayMap = new ArrayMap<>();


	SparseArray和ArrayMap都差不多，使用哪个呢？ 
	假设数据量都在千级以内的情况下：

	1、如果key的类型已经确定为int类型，那么使用SparseArray，因为它避免了自动装箱的过程，如果key为long类型，它还提供了一个LongSparseArray来确保key为long类型时的使用

	2、如果key类型为其它的类型，则使用ArrayMap
3,Pair

	Pair是一个容器，作用是轻便地对两个对象组成的元素进行传递，这个对象提供了一个合理的equal()方法，如果两个对象first和second值相等则返回true；
	Pair(F first,S second),一个Pair容器里面有2个元素，他们是成组存在的；
	Pair里面两个元素都是final的；
	Pair的equals是值比较，而不是地址比较；

[Android 表示一对“组元素”的Pair类 \- 简书](http://www.jianshu.com/p/cbec7786d8f1)
