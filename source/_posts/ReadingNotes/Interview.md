---
title: Java如何面试
date: 2021/1/3 1:01:37
layout: Markdown
permalink: Interview.html
cover: /images/java1/b1.jpg
---
《On Java8》是Java领域最具有影响力和价值的著作之一，与《CoreJava》齐名，我将在阅读本书的同时将一些要点记录下来，并修正我之前的一些错误同时拓宽知识层面，进一步提升编程的知识储备，进一步理解Java语言的由来和基本要素。
<!--more-->
### STAR法则

 situation task action resuit:

> S: 你在怎样的情景、背景下（来龙去脉），担任怎样的角色，在怎样的挑战下,

> T: 你的任务是什么，你应该达到怎样的目的

> A: 你采取了怎样的行动（说，想，做），步骤，计划，僵局

> R: 产生了怎样的结果，（拉新，留活，QPS并发量等，节约资源，）给公司的价值，自己的价值（复盘）。


### 面试细节
细节，数字
闻味观


### 面试问题：秒杀
1.技术面：超卖，少卖

> 单机环境下:



> 多机环境下：   JVM锁，唯一索引

![](/images/notes/InterView/2.png)


QPS（query per second） ：每秒数据查询量
TPS （transaction per second）：每秒事务处理量

QPS优化方案：

1. 异步（最终一致性，不需要及时）， 流量削锋
2. 缓存。（减少DB读取， 减少磁盘IO， 读多， 写少）
3. 数据库优化
4. 多的数据， 分批次返回
5. 减少调用链
