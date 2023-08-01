---
cssClasses: cards, cards-align-bottom, cards-cover,cards-1-1, table-max,cards-cols-8
banner: "![[books-g156f242fd_1920.jpg]]"
banner_y: 0.596
banner_icon: 📙
tags: index
---

- [[HomePage|返回主页]]  | [[index-ITNote|IT笔记]]  | [[index-movielist|电影清单]] |[[index-日记|日记]]
---

`button-shuying`  说明：升级版，输入书籍名称或ISBN、新建笔记。默认状态(status) 为”想读“ 。
 
---
 
#  想读/待读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "阅读"
where status = "想读" 
sort file.cday asc 

```
---

#  在读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "阅读"  
where  status="在读"
sort file.cday asc 

```
---
#  读完
## 精读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "阅读"  
where  status="精读"
sort file.cday asc 

```
---

## 再读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "阅读"  
where  status="再读"
sort file.cday asc 

```
---

## 略读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "阅读"  
where  status="略读"
sort file.cday asc 

```
---

## 今年

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author", ("**=="+(date(today)-date(EndDate)).days+"==**天前读完") as "Past", ("阅读周期==**"+(date(EndDate)-date(BeginDate)).days+"**==天") as "Period"
from "阅读"  
where EndDate!=none & date(EndDate).year=date(now).year
sort BeginDate desc
```
---

## 以往

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author", ("**=="+(date(today)-date(EndDate)).days+"==**天前读完") as "Past", ("阅读周期==**"+(date(EndDate)-date(BeginDate)).days+"**==天") as "Period"
from "阅读"  
where EndDate!=none & date(EndDate).year<date(now).year
sort BeginDate desc
```
---


-  [[#想读 待读|一键回到顶部]]