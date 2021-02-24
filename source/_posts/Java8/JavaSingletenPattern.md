---
title: Java设计模式之单例模式
date: 2020/7/24 20:33:43
layout: JavaSingletenPattern
permalink:  JavaSingletenPattern.html
cover:  http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
单例模式（SingletenPattern）是Java中最简单的设计模式之一。这种类型的设计模式属于创建型模式，它提供了一种创建对象的最佳方法，本文我将通过资料以及自己的理解详细梳理对单例模式的运用和理解。
<!--more-->

---

## Java设计模式之单例模式
#### 1、单例模式是什么？
-    单例模式顾名思义就是在整个运行时域，一个类只有一个实例对象;
#### 为什么需要单例模式？
-    因为有的类的实例对象创建和销毁对资源来说消耗不大，比如说String，而有的类比较庞大和复杂，如果频繁的创建和销毁对象，并且这些在对象完全是可以复用的情况下，那么将会造成一些不必要的性能浪费；

##### 举个栗子
-    现在我要写一个访问数据库的demo，而创建数据库链接对象是一个耗资源的操作，并且数据库链接完全是可以复用的，那么我就可以将这个对象设计成单例的，这样我只需要创建一次并且重复使用这个对象就行了，而不需要每次都去访数据库去创建一个链接对象，如果那样做将会是一个非常恐怖的事情。

#### 那么在Java中，是如何实现单例模式呢？
-    单例模式有很多种写法，有些人不以为然，觉得这样没有意义，完全就是一个茴香豆有几种写法一样的问题，自己呢只要会一种就够了，但是对于复杂的编程环境，只掌握一种是无法解决所有实际的业务的，在我看来，每种写法都是处于不同的思考方式，而且设计的十分巧妙，其中的思想是值得细品和借鉴的。

---

#### 在单例模式中，需要考虑三点：

> 1.是不是线程安全？

> 2.是不是懒加载？

> 3.能不能通过反射破坏？

##### 再举个栗子

    public class Singleton{
        //让构造函数私有, 这样该类就不会被实例化
        private Singleton(){}
        //初始化对象为null
        private static Singleton instance = null;
        //获取唯一可用的对象
        public static Singleton getInstance(){
            if (instance == null){
                instance = new Singleton();
            }
            return instance;
        }



*   在这里我写了一个名叫Singleton的类，来表示我们需要构造的这个单例，首先我们将构造器设置为private，那么其他类就没有办法通过new来构造这个Singleton对象实例了；而其他类中需要使用Singleton对象的话，只能通过调用getInstance方法，在getInstance方法中，首先判断instance是否被构造过，如果构造过就直接使用，如果没有就当场构造。


#### 懒加载
*   首先我们可以看到，实例对象是第1次被调用的时候才真正被构建的，而不是程序的启动它就构建好了等你调用的，这种滞后构建的方式就叫做懒加载。

##### 懒加载的好处是什么？
*   因为有些对象构建开销是比较大的，假如这个对象在项目启动时就构建，万一从来没有调用个，那么就比较浪费了；只有真正需要使用了再去构建，这是更加合理的。就像去吃自助餐，盘子就这么大，不管想不想吃都往盘子里装，到最后不想吃的一大堆，想吃的反而装不下了。


#### 线程安全
1. 我们再来看看上面那个栗子：


    public class Singleton{
        //让构造函数为private, 这样该类就不会被实例化
        private Singleton(){}
        //初始化对象为null
        private static Singleton instance = null;
        //获取唯一可用的对象
        public static Singleton getInstance(){
       //当在执行instance == null时，可能多个线程同时进入，容易被实例化多次。
            if (instance == null){
                instance = new Singleton();
               }
            return instance;
        }

 **不难看出这个例子不是线程安全的，当在执行instance == null时，可能多个线程同时进入，容易被实例化多次。**


 2. 那该如何使其线程安全呢，这时可以想到加上synchronized就好了，可以将代码改造成下面这个样子：


     public class Singleton{
       private Singleton(){}
       private static Singleton instance = null;
       //获取唯一可用的对象
       public static synchronized Singleton getInstance(){
           if (instance == null){
               instance = new Singleton();
              }
           return instance;
       }

**这种方法大多数情况下是不可取的，这样虽然能保证在同一时刻只有一个线程能够进入getInstance方法，但这也引入了新的问题；其实我们只想要对象在创建的时候同步线程，而这样的话，每次在获取对象时都需要进行同步操作，对性能的影响非常大，**

***通过对以上的思考，我发现，线程安全问题出现在了构建对象的阶段，那么我们只要在编译期构建对象，在运行时调用，就不用考虑线程安全的问题了。***

3. 于是，我们这样写：


    public class Singleton{
      private static Singleton instance = new Singleton();
      private Singleton(){}
      //获取唯一可用的对象
      public static Singleton getInstance(){
          return instance;
      }
    }

**可以看出这样是能保证线程安全的，但这种写法不是懒加载**

那么有没有既是懒加载有实现线程安全的写法呢？

**我们可以回到第二种写法，来看看是到底是哪里出了问题：形成低效的原因在于getInstance()上加了synchronized,所以导致每个进入该方法的线程首先得获取锁，那么只要在构建对象的时候同步，而可以直接使用对象时就没必要同步了。**

4. 像这样：


    public class Singleton{
      private static Singleton singleton;
      private Singleton(){}
      public static  Singleton getInstance(){
          if (singleton == null){
              synchronized(Singleton.class){
              singleton = new Singleton();
              }
          }
          return singleton;
          }
       }

**现在getInstance是不需要竞争锁的，所有线程都可以直接进入，此时进入第二步判断，如果实例对象还没有创建，那么多个线程开始争抢锁，抢到锁的线程开始创建实例对象，实例对象创建之后，所有的线程在执行第二步时都可以直接跳过，返回实例化对象进行调用，这就解决了最开始的低效问题**

***但这时我们会发现，虽然只有一个线程能够抢到锁，但可能会有其他线程已经进入if代码块，此时正在等待，一定线程a执行完，线程b就会立马抢到锁，然后进行对象创建，这样对象就会被创建多次，这个问题也不难，我们再加一个判空操作就能解决***


5. 如下：



    public class Singleton{
      private static Singleton singleton;
      private Singleton(){}
      public static  Singleton getInstance(){
          if (singleton == null){
              synchronized(Singleton.class){
                if(singleton == null){}
              singleton = new Singleton();
                 }
              }
          }
          return singleton;
          }
       }

**我们假设两个线程同时进入getInstance方法，这边a首先获取锁然后创建了singleton实例对象，当它构建完成后交还锁，这时候吧线程也会立即获取锁，在获得锁之后它也会进行一个判空，但singleton实例对象a线程创建，b线程会直接跳过if代码块，返回singleton实例，这样就会造成线程不安全的问题了**

* 这种对对象进行两次判空的操作叫做双检锁


















我们创建一个SingleObject类。SingleObjectl类有它的私有构造函数和本身的一个静态实例。
SingleObject类提供了一个静态方法，供外界获取它的静态实例。SingletonPattemDemo,我们演示类使用SingleObject类来获取SingleObject对象。

首先创建一个Singleton类

    public class SingleObject{

    //创建SingleObject 的一个对象
         private static SingleObject instance = new SingleObject();

    //让构造函数为private, 这样该类就不会被实例化
    private SingleObject(){}

    //获取唯一可用的对象
    public static SingleObject getInstance(){
        return instance;
    }

    public void showMessage(){
        System.out.println("Hello World!");
      }
    }
