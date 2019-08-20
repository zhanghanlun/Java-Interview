# 1、synchronized关键字
## 1.1 作用范围

 - 修饰普通方法，作用于当前对象，进入同步代码前要获取当前对象实例的锁。
 - 修饰静态方法，作用于当前类对象，进入同步代码前要获取当前类对象的锁。
 - 修饰代码块，指定加锁对象，对给定对象加锁，进入同步代码前要获得给定对象的锁。

## 1.2 具体使用（单例模式，联合volatile）
```java
public class Singleton {
    private static volatile Singleton singleton;
    /**
     * 双重检查锁，volatile修饰禁止指令重排
     * @return
     */
    public Singleton getInstance(){
        if (singleton == null){
            synchronized (this){
                if (singleton == null){
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}
```
## 1.3 synchronized底层原理

 - synchronized同步语句块使用的是monitorenter和monitorexit指令
 - synchronized同步方法使用的是ACC_SYNCHRONIZED标识

## 1.4 synchronized和ReenTrantLock的区别

 1. 都是可重入锁
 2. synchronized依赖于JVM，而ReenTrantLock依赖于api
 3. ReenTrantLock比synchronized更高级，可以实现公平锁

# 2、多线程
## 2.1、实现线程的三种方式

 1. 实现Runnable接口，重写run方法，无返回值
 2. 实现Callable接口，重写call方法，可以有返回值
 3. 继承Thread类，重写run方法

 ## 2.2、线程池
 **ThreadPoolExecutor**
 三种类型ThreadPoolExecutor如下：
 1、FixedPoolExecutor ——固定线程数量的线程池
 2、SingleThreadExecutor—— 只有一个线程的线程池
 3、CachedThreadPool—— 根据实际情况调整线程数量的线程池
 4、ScheduledThreadPool——可以定时执行

 