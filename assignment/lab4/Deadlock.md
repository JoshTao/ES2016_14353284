#Lab4 DOL死锁报告
<br/>
>**实验截图**

<br/>
![pic.jpg](https://github.com/JoshTao/Picture/blob/master/lab4/pic.JPG)

>**死锁发生的四个条件**

1.互斥条件：同一个资源同一时间内只能被一个进程使用；

2.占有且等待：一个进程在持有一个资源的同时，被正在请求的另一个资源阻塞；

3.资源不可剥夺：对于进程已经获取的资源，在其使用完之前不能被其它进程剥夺；

4.循环等待：多个进程间存在资源循环等待的情况；

>**对死锁的解释**

这一次实验我们可以看到，首先主线程生成了一个子线程t，然后子线程开始跑run函数，而主线程在延迟count之后跑a.methodA(b).随着循环的进行会有这么一种情况发生：子线程t运行b.methodB(a).因为关键字synchronized的原因，b这时候毫无疑问被子线程t占用。当主线程运行到a.methodA(b)的时候，占用了a。接下来子线程t运行的b.methodB(a)会调用a.last()，但是因为主线程的原因没办法调用a，子线程t被阻塞。而主线程同理运行的a.methodA(b)在调用b.last()也被阻塞，因此死锁就发生了。



