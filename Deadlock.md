
## Lab4:死锁

###1. 实验流程
  
 1 写Deadlock.java

 2 javac Deadlock.java	

 3 linux 系统Windows系统（把下面这段到记事本里，然后保存为.bat，然将批处理文件放在java程序（Deadlock.class）目录下，双击运行，观察结果）

###2. 实验结果
原始count=20000;死锁的位置（都是随机的）

死锁停在40次

<img src="https://raw.githubusercontent.com/xiangyeye/image/master/deadlock1.png" width = "150" alt="configure" />


改count=10000;死锁的位置（都是随机的）

死锁停在12次，随机的，每次执行的结果都不一样

<img src="https://raw.githubusercontent.com/xiangyeye/image/c0dced69016fc1aad4f957e9b14bc6e889133daf/deadlock2.png" width = "150" alt="configure" />


   
###3. 产生死锁的四个必要条件
1）互斥条件：一个资源每次只能被一个进程使用。

2）请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放。

3）不剥夺条件:进程已获得的资源，在末使用完之前，不能强行剥夺。

4）循环等待条件:若干进程之间形成一种头尾相接的循环等待资源关系


###4. 对本次实验程序产生死锁的解释
本次产生死锁的原因是：
首先我们这里有一个主函数的时间轴，当t.start(),之后，线程t就被插入到调度队列里，当调度到他的时候，就跑run()里面的代码，执行b.methoadB(a)，输出Inside B.last.
但是我们有设置一个count，当等待count的时间后，就会执行a.methoadA（b)，输出Inside A.last.我们经过循环运行了很多次，当经过count个时间后，恰好调度到t.start()，b.methoadB(a)和a.methoadA（b)就冲突了，产生死锁。

###5. 实验感想

本次实验也是比较简单的，毕竟对于死锁这一块之前操作系统课上就有学到过，而且我们只要把代码抄上去运行，分析死锁产生的原因，这就相当于把以前学到知识再做一次复习吧。我们这次实验，要清楚的是一个资源只能一次只能被一个线程占用(A占用)，当有其他线程（B线程）来请求这个被占用的资源的之后，如果当前占用资源的线程（A线程）不释放，那么那个等待的线程（B线程）就要等着，要是这时候被阻塞的线程（B线程）拿着A要请求的资源，那么他们随都不肯先放手，那么就产生死锁了。
