---
layout: post
title: Hash索引
subtitle: 
author: ezekielgcl
date: 2023-08-20
aliases: 
tags: Mysql
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: 2023-08-20
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[code6.jpeg]]"
banner_y: 0.40239
banner_icon: 📚
---


Hash索引其实用的不多，最主要是因为最常见的存储引擎InnoDB不支持<mark style="background: #FF5582A6;">显示地创建</mark>Hash索引，只支持<mark style="background: #FF5582A6;">自适应Hash索引</mark>。虽然可以使用sql语句在InnoDB显示声明Hash索引，但是其实是不生效的

在存储引擎中，Memory引擎支持Hash索引。Hash索引其实有点像Java中的HashMap底层的数据结构，他也有很多的槽，存的也是<mark style="background: #FF5582A6;">键值对</mark>，<mark style="background: #FF5582A6;">键值为索引列</mark>，<mark style="background: #FF5582A6;">值为这条数据的行指针</mark>，通过行指针就可以找到数据。假设现在`user`表用Memory存储引擎，对name字段建立Hash索引，表中插入三条数据
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230820053804.png)

Hash索引会对索引列name的值进行Hash计算，然后找到对应的槽下面，如下图所示
![image.png](https://raw.githubusercontent.com/guchaolong/articleImgs/master/20230820053847.png)
当遇到name字段的Hash值相同时，也就是Hash冲突，就会形成一个链表，比如有name=张三有两条数据，就会形成一个链表。之后如果要查name=李四的数据，只需要对李四进行Hash计算，找到对应的槽，遍历链表，取出name=李四对应的行指针，然后<mark style="background: #D2B3FFA6;">根据行指针去查找对应的数据</mark>

**Hash索引优缺点**
- hash索引只能用于<mark style="background: #FF5582A6;">等值</mark>比较，所以查询效率非常高
- 不支持范围查询，也不支持排序，因为索引列的分布是无序的