---
title: 悲观锁和乐观锁
categories: db
tags:
---

#悲观锁和乐观锁
在数据库操作的时候，如果对于同一条记录进行并发访问，就需要考虑锁机制。会有如下几种情况

- 无锁：直接更新数据，这个时候无法预料并发的结果。不过有的业务场景中即使数据被覆盖也没有关系，那么可以使用这种机制
- 悲观锁：在进行操作之前进行加锁，加锁成功后再进行操作，如果失败则返回错误或等待。由于每次写入操作都需要进行加锁，所以系统开销比较大，一般适用于读多写少的场景。
- 乐观锁：对每行记录加入一个版本号或者时间戳，每次写入之前先读取，当要写入的时候再核对之前读取的版本号是否合现在系统记录中的版本号一致。如果不一致则只能返回失败，让业务方处理。个人比较推荐这种方式作为日常开发中常用的并发控制。因为，一般应用对于每一行的并发可能性很小，大多数请求不会出现乐观锁需要回滚的情况，所以总体来看收益还是大于代价的。
-----
[参考文章](http://www.hollischuang.com/archives/934)