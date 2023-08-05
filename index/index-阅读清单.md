---
cssClasses: cards, cards-align-bottom, cards-cover,cards-1-1, table-max,cards-cols-8
banner: "![[book2.jpeg]]"
banner_y: 0.72
banner_icon: 📙
tags: index
---

- ## [[HomePage|返回主页]] | [[index-码农笔记|码农笔记]] | [[index-电影清单|电影]] | [[index-日记|日记]]
---

---
 
#  想读/待读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "个人成长/阅读"
where status = "想读" 
sort file.cday asc 

```
---

#  在读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "个人成长/阅读"  
where  status="在读"
sort file.cday asc 

```
---


## 略读

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author"
from "个人成长/阅读"  
where  status="略读"
sort file.cday asc 

```
---

## 今年

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author", ("**=="+(date(today)-date(EndDate)).days+"==**天前读完") as "Past", ("阅读周期==**"+(date(EndDate)-date(BeginDate)).days+"**==天") as "Period"
from "个人成长/阅读"  
where EndDate!=none & date(EndDate).year=date(now).year
sort BeginDate desc
```
---

## 以往

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name, default(split(author," ")[1],author) as "Author", ("**=="+(date(today)-date(EndDate)).days+"==**天前读完") as "Past", ("阅读周期==**"+(date(EndDate)-date(BeginDate)).days+"**==天") as "Period"
from "个人成长/阅读"  
where EndDate!=none & date(EndDate).year<date(now).year
sort BeginDate desc
```
---


-  [[#想读 待读|一键回到顶部]]
