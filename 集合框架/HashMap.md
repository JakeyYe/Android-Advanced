## HashMap


#### HashMap的底层原理
HashMap是一个用来存储键值对的集合，每一个键值对也叫Entry，这些键值对（Entry）分散存储在一个数组中，这个数组就是HashMap的主干，通过一个哈希函数来确定Entry在数组中的位置，还有就是当数组位置冲突时，会在数组后创建一条链表，存储冲突元素，也称为链地址法解决冲突，当有冲突的元素进来时就插入链表头节点上（是因为HashMap的发明者认为，后插入的Entry被查找的可能性较大）；HashMap可以存储键值对为空的元素，为空的元素存储在数组首位上；

#### HashMap默认的初始长度是多少？为什么这么规定？

HashMap的默认初始长度为16，并且每次自动扩展或是手动初始化时，长度必须时2的幂；之所以选择16，是为了服务于从key映射到index的Hash算法；从key映射到HashMap数组的对应位置，会用到一个Hash函数，HashMap使用位运算作为高效的Hash函数，有如下的公式：index=HashCode(key)&(Length-1)(Length是HashMap的长度，HashCode(key)是获取这个key的hash code)


#### 当链表过长时，Java8引入红黑树来解决效率问题；


#### 高并发时，链表可能会产生环形链路，是因为扩容后ReHash时，transfer()函数引起的链表元素next节点形成环路（当两个线程都进行扩容时可能发生这种情况），get时容易引起死锁，并发访问还是用ConcurrentHashMap;

#### 扩容，ReHash

1)Capacity HashMap的当前长度，HashMap的长度是2的幂
2）LoadFactor HashMap的负载因子，默认值是0.75f
当HashMap.size > = Capacity*LoadFactor时就会Resize,这时就会扩展它的长度，扩展为原来数组容量的两倍；
扩容的完整操作是：
1）扩容：创建一个新的Entry空数组，长度为原数组的2倍；
2）ReHash:遍历原数组，把所有的Entry重新Hash到新数组中取，因为容量扩大之后，Hash的规则也随之改变；


#### HashMap不是线程安全的，在并发操作插入元素的时候，有可能出现带环形链表，让下一次读操作出现死循环；使用Collections.synchronizedMap,Hashtable,CurrentHashMap这个三个同步HashMap,Collections.synchronizedMap和Hashtable,无论是读操作还是写操作，都会给整个集合加锁，导致会阻塞同一时间的其他操作；CurrentHashMap的优势是采用了“锁分段技术”，每一个Segment就好比一个自治区，读写操作高度自治，Segment之间互不影响；