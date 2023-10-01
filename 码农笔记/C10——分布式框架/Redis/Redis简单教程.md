# Redis 简介
Redis是一款==内存高速缓存==数据库。Redis全称为：**Remote Dictionary Server**（远程数据服务），使用==C语言==编写，Redis是一个key-value存储系统（==键值存储==系统），支持丰富的数据类型，如：String、list、set、zset、hash。

Redis是一种支持key-value等多种数据结构的存储系统。可用于缓存，事件发布或订阅，高速队列等场景。支持网络，提供字符串，哈希，列表，队列，集合结构直接存取，基于内存，可持久化

Redis 是目前最热门的 NoSQL 数据库之一

早期互联网公司大多是使用 Mysql 这种传统的==关系型数据库==存储数据，随着互联网的快速发展，应用系统的访问量越来越大，数据库的性能瓶颈越来越明显，主要是由于磁盘 IO 所导致，磁盘 IO 的读写操作速度与内存相比是非常慢的，如果能把数据存储在内存中，是不是就可以大大提高它的性能了呢，于是就有了Redis 这种基于内存的数据存储系统

## 支持的数据类型
Redis支持多种数据结构，包括 5 种==基础==数据类型，和 5 种==高级==数据类型
* 字符串 String
* 列表 List
* 集合 Set
* 有序集合 SortedSet 
* 哈希 Hash

* 消息队列 Stream 
* 地理空间 Geospatial 
* HyperLogLog
* 位图 Bitmap
* 位域 Bitfield

## Redis 的优势
* 性能极高
* 数据类型丰富，单键值对最大支持512M大小的数据
* 简单易用，支持所有主流编程语言
* 支持数据持久化、主从复制、哨兵模式等高可用特性


## Redis的3 种使用方式：
* CLI (Command Line Interface)：
  命令行，redis-cli
* API (Application Programming Interface)：
  就是 Java 这些编程语言通过代码的方式来使用 Redis
* GUI (Graphical User Interface)：
  通过图形用户界面，比如 RedisInsight

RedisInsight：
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/202310011718563.png)



# 常用命令
Redis命令行大全：
[[RedisCheatSheet-ByGeekHour.pdf]]

## String

`set k1`

`get k1
`
`exists k1`  k1是否存在

`keys *`   查看所有key

`del k1`   删除k1

`fulshall`   删除所有key

`ttl k1 `  查看k1的过期时间，返回-1 表示没有设置过期时间,返回 -2 表示已经过期

`expire k1 10`  设置k1 的过期时间为 10s

`setex k2 6 guchao`   设置 k2值为 guchao,过期时间为 6s

`setnx name long`   只有当 name 不存在时才设置为 long,如果存在了，则不做任何操作

如果设置 value 为中，get 的时候会显示成 16 进制
如果要看中文，则 `quit` 退出客户端，再执行`redis-cli --raw`  --raw 表示以原始的形式显示内容


## List

