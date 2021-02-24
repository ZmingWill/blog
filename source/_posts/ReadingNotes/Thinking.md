---
title: 关于并发编程的一些思考
date: 2021/2/22 1:01:37
layout: Markdown
permalink: Thinking.html
cover: /images/java1/b1.jpg
---

<!--more-->

#### 关于并发编程思考

并发编程是程序员修炼功底之一，那么我们应该关注那些方面？

** 主要有三个核心问题：分工，同步，互斥**

1. 分工是指如何将任务拆分成多线程执行

举个例子，假如现在有一个公司的CEO，他的任务便是管理好公司，但就管理公司而言，需要做的任务就比较多了；我们将管理公司看成一个很大的任务，但细看这个很大的任务包括：人力招聘和管理，产品设计和研发，推广和销售，公司税务等等，如果单凭CEO一个人来完成这些任务，管理好这个公司不知道得到猴年马月。

![](https://imgconvert.csdnimg.cn/aHR0cDovL3AzLnBzdGF0cC5jb20vbGFyZ2UvcGdjLWltYWdlLzE4YzczNTEzOGFhNTRhNGNhYzM2YTY2ZjQ3OThmNDA4?x-oss-process=image/format,png)

我们要做的是把工作细分，将人员招聘和管理的任务交给人力资源部门去完成，将产品的设计交给设计部门去完成，将产品的开发交给开发部门去完成，将运营和推广交给运营和市场部门去完成，将公司税务交给财务部门去完成，而CEO的任务便是统筹并协调各部门，完成计划和规划公司未来。这样很多任务在极大程度上是并发进行的，大大缩短了任务耗费的时间。

![](https://imgconvert.csdnimg.cn/aHR0cDovL3AxLnBzdGF0cC5jb20vbGFyZ2UvcGdjLWltYWdlLzA2NjhlZDAzNmY0ZDRiYjRhYmIzMWQxYjViNjUxYWY2?x-oss-process=image/format,png)


2. 同步是指线程之间如何协调

当将工作细分给每个人，接下来就是如何同步每个人的任务了

假设小明是一位前端开发人员，他渲染业务的数据等先等小刚的接口完成，而小刚写接口又要等小李的服务开发完成，所以任务之间存在依赖关系，前面的任务完成后，才能进行后面的任务。

![](https://imgconvert.csdnimg.cn/aHR0cDovL3AzLnBzdGF0cC5jb20vbGFyZ2UvcGdjLWltYWdlLzFiNTY5MmE0ZmNmYjRkNDY5MjBjM2Y2ZWUxYmJkODE2?x-oss-process=image/format,png)

当然，对于实际工作中，这种任务的同步，大多数靠的是人与人之间的沟通，小李的服务写完了，告诉小光，小光则马上进行接口开发，等小光的接口开发完成后，又告诉了小明，小明马上调用接口将返回的数据渲染在页面上。

对于这种同步机制映射到并发编程领域，就是一个线程的任务执行完毕后，通知其他后续线程执行任务。

在Java的SDK中，提供了一些实现线程之间同步的工具类，比如说：CountDownLatch、 CyclicBarrier 等。

3. 而互斥是如何保证同一时刻只允许一个线程访问同一资源

当多个岔路口的车辆需要汇入一条道路，这条道路一次只允许一辆车辆通过，此时车辆就需要排队依次进入路口。

Java中提供的synchronized、Lock、ThreadLocal、final关键字等都可以解决互斥的问题。

- 锁机制

synchronized 锁机制

先看下面例子：






##### 分工和同步关注的是性能问题，而互斥关注的是安全问题

 - 并发编程旨在最大限度的利用计算机的资源，提高程序执行的性能，这需要线程之间的分工和同步来实现，在保证性能的同时，又需要保证线程的安全，这就又需要保证线程之间的互斥性。而并发编程的难点问题，往往又是由可见性、原子性和有序性问题导致的。所以，我们在学习并发编程时，一定要先弄懂线程之间的分工、同步和互斥。

#### 并发编程需要掌握的核心技能知识图

![](https://imgconvert.csdnimg.cn/aHR0cDovL3AzLnBzdGF0cC5jb20vbGFyZ2UvcGdjLWltYWdlLzU2YzVkNzQ0YjVlODRkZDRiNTFlMWFkMDk0NmY2OTY2?x-oss-process=image/format,png)


参考自：<https://blog.csdn.net/GYHYCX/article/details/106225369>
