# java防止并发的几种方法

2018\7\19



## 使用synchronized关键字

3种使用方法:

* 修饰类方法,作用于当前实例加锁,进入方法要获取当前实例的锁
* 修饰静态方法,作用于当前实例加锁,进入方法要获取当前实例的锁
* 修饰代码块,指定加锁对象,给指定对象加锁,进入代码块要先获取指定对象的锁(synchronized参数要传入固定的对象才能起到作用)

## 使用原子操作

java 在 JDK atomic包下的提供了原子操作的类,常用的有

* AtomicBoolean
* AtomicInteger
* AtomicIntegerArray
* AtomicIntegerFieldUpdater
* AtomicLong
* AtomicLongArray
* AtomicLongfieldUpdater
* AtomicMarkableReference
* AtomicReference
* AtomicReference
* AtomicReferenceArray
* AtomicReferenceFieldUpdater
* AtomicStampedReference
* DoubleAccumulator
* DoubleAdder
* LongAccumulator
* LongAdder
* Striped64

其中atomicboolean atomicinteger atomicreperence常用的方法及含义

* get() 获取当前值
* set()设置当前值
* getAndSet(V newValue) 获取当前值并设置最新的值
* compareAndSer(V expect,V update)如果expect与当前值相同就设置update为最新值

#### CountDownLatch简介

> 作用:允许一个或多个线程等待其他线程完成操作  jdk1.5以后提供

* 用法

  

```new Thread(new Runnable() {			@Override			public void run() {				System.out.println(1);				c.countDown();				System.out.println(2);				c.countDown();			}		}).start();
CountDownLatch c = new CountDownLatch(2);
new Thread(new Runnable() {
			@Override
			public void run() {
				System.out.println(1);
				c.countDown();
				System.out.println(2);
				c.countDown();
			}
		}).start();

c.await();
System.out.println(3);

```



构造方法传入的int值是用来几部用的,调用一次一次countDown方法步数就减一,当步数为0是,就回走await方法后的代码 



await(long time , TimeUnit unit) 等待时间超过设置时间就不会阻塞.



