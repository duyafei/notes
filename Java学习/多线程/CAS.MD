### 什么是CAS锁机制
    CAS锁是为了解决多线程使用锁造成性能损耗的算法、保证了原子性、这个原子性是由CPU来完成的

### CAS原理
    通过三个操作数 （内存值地址 E） （预期原值 N） （新值 V）
    如果E等于N、则将V覆盖E
    如果E不等于N、说明E已经被修改、放弃之前所有操作、重新执行以上操作直到E等于N
    通过汇编指令实现、保证了原子性： lock cmpxchg 
    CAS基于乐观锁思想来设计的、不会引起阻塞、 同时也带来了指针安全问题

### ABA问题
    如果线程t1正在修改共享值A还未被修改完成、线程t2在修改成B后、然后又修改成A、线程t1没有发现任何变化、但是在线程t2已经改变了。

    解决方案：
    使用版本号、每次变量更新的时候把版本号+1
    问题：
    不能保证多个共享变量的原子操作

    使用AtomicReference类来保证对象之间的原子性
