---
status: 1
cssclasses:
  - cards
  - cards-align-bottom
  - cards-cover
  - cards-1-1
  - table-max
  - cards-cols-8
banner: "![[movie.jpeg]]"
banner_y: 0.47039
banner_icon: 📽️
tags:
  - index
---

- ## [[HomePage|返回主页]] | [[index-码农笔记|码农笔记]] | [[index-阅读清单|阅读]] | [[index-日记|日记]] |

---
---

#  想看

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,tags as Tags, director as 导演,rating as 评分
from  "个人成长/电影"
where genre !=none & status="想看" 
sort file.cday asc 

```
---

#  看完

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,tags as Tags, director as 导演,rating as 评分
from "个人成长/电影"
where genre !=none & status="看完" 
sort file.cday asc 

```
---

# 再看

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,tags as Tags, director as 导演,rating as 评分
from "个人成长/电影"
where genre !=none & status="再看" 
sort file.cday asc 

```
---


- [[#想看|回到顶部]]