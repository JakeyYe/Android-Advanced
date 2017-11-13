## HashMap


#### HashMap的底层原理
HashMap是一个用来存储键值对的集合，每一个键值对也叫Entry，这些键值对（Entry）分散存储在一个数组中，这个数组就是HashMap的主干，通过一个哈希函数来确定Entry在数组中的位置，还有就是当数组位置冲突时，会在数组后创建一条链表，存储冲突元素，也称为链地址法解决冲突，当有冲突的元素进来时就插入链表头节点上（是因为HashMap的发明者认为，后插入的Entry被查找的可能性较大）；HashMap可以存储键值对为空的元素，为空的元素存储在数组首位上；

#### HashMap默认的初始长度是多少？为什么这么规定？

HashMap的默认初始长度为16，并且每次自动扩展或是手动初始化时，长度必须时2的幂；之所以选择16，是为了服务于从key映射到index的Hash算法；从key映射到HashMap数组的对应位置，会用到一个Hash函数，HashMap使用位运算作为高效的Hash函数，有如下的公式：index=HashCode(key)&(Length-1)(Length是HashMap的长度，HashCode(key)是获取这个key的hash code)


#### 当链表过长时，Java8引入红黑树来解决效率问题；


#### 高并发时，链表可能会产生环形链路，大致是因为扩容时，transfer()函数引起的链表元素next节点形成环路，get时容易引起死锁，并发访问还是用ConcurrentHashMap;