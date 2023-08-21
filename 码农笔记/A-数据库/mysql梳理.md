---
layout: post
title: mysql梳理
subtitle: 
author: ezekielgcl
date: 2023-08-21
aliases: 
tags: 
keyword: 码农笔记
catalog: true
category: 码农笔记
status: 
link: 
BeginDate: 2023-08-21
EndDate: 
header-img: img/post-bg-re-vs-ng2.jpg
banner: "![[code6.jpeg]]"
banner_y: 0.40239
banner_icon: 📚
---



where、group by、having、order by、limit这些关键字一起使用时，先后顺序有明确的限制，语法如 下：
```sql
select 列 from 表名

where [查询条件] 
group by [分组表达式] 
having [分组过滤条件] 
order by [排序条件] 
limit [offset,] count;
```
写法上面必须按照上面的顺序来写。



笛卡尔积
简单点理解：有两个集合A和B，笛卡尔积表示A集合中的元素和B集合中的元素任意相互关联 产生的所有可能的结果

假如A中有m个元素，B中有n个元素，A、B笛卡尔积产生的结果有m*n个结果，相当于循环遍历两个集 合中的元素，任意组合。

过程：拿A集合中的第1行，去匹配集合B中所有的行，然后再拿集合A中的第2行，去匹配集合B 中所有的行，最后结果数量为m*n。
