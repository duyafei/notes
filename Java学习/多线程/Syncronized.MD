### Syncronized加锁
    通过CAS的方式修改markword中的锁状态

### Syncronized锁升级
    偏向锁 -> 轻量锁 -> 重量锁

#### 偏向锁：
- 如果竞争线程只有一个线程的时候、那么这个锁偏向这个线程、直接上锁，在线程栈中创建一个lock record，并将mardword拷贝到lock record，同时锁中的markword中的指针也会指向当前持有锁线程的lock record
- 偏向锁有4秒的延迟，如果要看到效果在代码里加上sleep(4100)或者通过jvm参数-XX:BiasedLockingStartupDelay=0将延迟设置成0

#### 轻量级锁
- 当多个线程存在竞争关系时，则升级成轻量级锁， 通过自旋+CAS的方式来抢锁

#### 重量级锁
- mordword里面记录的不在是lock record的指针，而是指向c++对象ObjectMonior
- 当轻量级锁自旋次数或者超过cpu设置的大小时，则升级为重量级锁
- 将所有线程放在EntryList队列中阻塞，等持有线程执行完成后，唤醒所有线程去抢占锁
