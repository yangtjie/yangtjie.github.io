---
layout: post
title:  "The Art of Java Concurrency Programming"
date: 2016-12-21 22:23:00 +0800
categories: java
---

##### 第1章 并发编程的挑战

###### 1.1 上下文切换

1. 多线程一定快吗

2.  测试上下文切换次数和时长

3.  如何减少上下文切换

4.  减少上下文切换实战


###### 1.2 死锁

###### 1.3 资源限制的挑战

###### 1.4 本章小结

##### 第2章 Java并发机制的底层实现原理

###### 2.1 volatile的应用

###### 2.2 synchronized的实现原理与应用

1. Java对象头
2. 锁的升级与对比

###### 2.3 原子操作的实现原理

###### 2.4 本章小结

##### 第3章 Java内存模型

##### 3.1 Java内存模型的基础

1. 并发编程模型的两个关键问题
2. Java内存模型的抽象结构
3. 从源代码到指令序列的重排序
4. 并发编程模型的分类
5. happens-before简介

###### 3.2 重排序

1. 数据依赖性
2. as-if-serial语义
3. 程序顺序规则
4. 重排序对多线程的影响

###### 3.3 顺序一致性

1. 数据竞争与顺序一致性
2. 顺序一致性内存模型
3. 同步程序的顺序一致性效果
4. 未同步程序的执行特性

###### 3.4 volatile的内存语义

1. volatile的特性
2. volatile写-读建立的happens-before关系
3. volatile写-读的内存语义
4. volatile内存语义的实现
5. JSR-133为什么要增强volatile的内存语义

###### 3.5 锁的内存语义

1. 锁的释放-获取建立的happens-before关系
2. 锁的释放和获取的内存语义
3. 锁内存语义的实现
4. concurrent包的实现

###### 3.6 final域的内存语义

1. final域的重排序规则
2. 写final域的重排序规则
3. 读final域的重排序规则
4. final域为引用类型
5. 为什么final引用不能从构造函数内“溢出”
6. final语义在处理器中的实现
7. JSR-133为什么要增强f?inal的语义

###### 3.7 happens-before

1. JMM的设计
2. happens-before的定义
3. happens-before规则

###### 3.8 双重检查锁定与延迟初始化

1. 双重检查锁定的由来
2. 问题的根源
3. 基于volatile的解决方案
4. 基于类初始化的解决方案

###### 3.9 Java内存模型综述

1. 处理器的内存模型
2. 各种内存模型之间的关系
3. JMM的内存可见性保证
4. JSR-133对旧内存模型的修补

###### 3.10 本章小结

##### 第4章 Java并发编程基础

###### 4.1 线程简介

1. 什么是线程
2. 为什么要使用多线程
3. 线程优先级
4. 线程的状态
5. Daemon线程

###### 4.2 启动和终止线程

1. 构造线程
2. 启动线程
3. 理解中断
4. 过期的suspend()、resume()和stop()
5. 安全地终止线程

###### 4.3 线程间通信

1. volatile和synchronized关键字
2. 等待/通知机制
3. 等待/通知的经典范式
4. 管道输入/输出流
5. Thread.join()的使用
6. ThreadLocal的使用

###### 4.4 线程应用实例

1. 等待超时模式
2. 一个简单的数据库连接池示例
3. 线程池技术及其示例
4. 一个基于线程池技术的简单Web服务器

###### 4.5 本章小结

##### 第5章 Java中的锁

###### 5.1 Lock接口

###### 5.2 队列同步器

1. 队列同步器的接口与示例
2. 队列同步器的实现分析

###### 5.3 重入锁

###### 5.4 读写锁

1. 读写锁的接口与示例
2. 读写锁的实现分析

###### 5.5 LockSupport工具

###### 5.6 Condition接口

1. Condition接口与示例
2. Condition的实现分析

###### 5.7 本章小结

##### 第6章 Java并发容器和框架

###### 6.1 ConcurrentHashMap的实现原理与使用

1. 为什么要使用ConcurrentHashMap
2. ConcurrentHashMap的结构
3. ConcurrentHashMap的初始化
4. 定位Segment
5. ConcurrentHashMap的操作

###### 6.2 ConcurrentLinkedQueue

1. ConcurrentLinkedQueue的结构
2. 入队列
3. 出队列

###### 6.3 Java中的阻塞队列

1. 什么是阻塞队列
2. Java里的阻塞队列
3. 阻塞队列的实现原理

###### 6.4 Fork/Join框架

1. 什么是Fork/Join框架
2. 工作窃取算法
3. Fork/Join框架的设计
4. 使用Fork/Join框架
5. Fork/Join框架的异常处理
6. Fork/Join框架的实现原理

###### 6.5 本章小结

##### 第7章 Java中的13个原子操作类

###### 7.1 原子更新基本类型类

###### 7.2 原子更新数组

###### 7.3 原子更新引用类型

7.4 原子更新字段类

###### 7.5 本章小结

##### 第8章 Java中的并发工具类

###### 8.1 等待多线程完成的CountDownLatch

###### 8.2 同步屏障CyclicBarrier

1. CyclicBarrier简介
2. CyclicBarrier的应用场景
3. CyclicBarrier和CountDownLatch的区别

###### 8.3 控制并发线程数的Semaphore

###### 8.4 线程间交换数据的Exchanger

###### 8.5 本章小结

##### 第9章 Java中的线程池

###### 9.1 线程池的实现原理

###### 9.2 线程池的使用

1. 线程池的创建
2. 向线程池提交任务
3. 关闭线程池
4. 合理地配置线程池
5. 线程池的监控

###### 9.3 本章小结

##### 第10章 Executor框架

###### 10.1 Executor框架简介

1. Executor框架的两级调度模型
2. Executor框架的结构与成员

###### 10.2 ThreadPoolExecutor详解

1. FixedThreadPool详解
2. SingleThreadExecutor详解
3. CachedThreadPool详解

###### 10.3 ScheduledThreadPoolExecutor详解

1. ScheduledThreadPoolExecutor的运行机制
2. ScheduledThreadPoolExecutor的实现

###### 10.4 FutureTask详解

1. FutureTask简介
2. FutureTask的使用
3. FutureTask的实现

###### 10.5 本章小结

##### 第11章 Java并发编程实践

###### 11.1 生产者和消费者模式

1. 生产者消费者模式实战
2. 多生产者和多消费者场景
3. 线程池与生产消费者模式

###### 11.2 线上问题定位

###### 11.3 性能测试

###### 11.4 异步任务池

###### 11.5 本章小结 
