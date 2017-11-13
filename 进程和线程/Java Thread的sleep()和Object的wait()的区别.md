## Java Thread的sleep()和Object的wait()的区别

sleep()方法是Thread类里的方法，主要意义是让当前线程停止执行，让出cpu给其他的线程，但是不会释放对象锁资源以及监控的状态，当指定的事件到了之后又会自动恢复运行状态；

wait()方法是Object类里面的，主要的意义就是让持有当前Object对象监视器的线程A放弃该对象的锁，进入等待此对象的等待锁定池，只有针对此对象调用notify方法后线程A才能进入对象锁定池准备获取对象锁进入运行状态(若有单个线程处于wait状态，调用notify()方法，只会随机让一个线程进入对象锁定池)；

[Java Thread 的 sleep\(\) 和 wait\(\) 的区别 \- 灰色飘零 \- 博客园](http://www.cnblogs.com/renhui/p/6069353.html)