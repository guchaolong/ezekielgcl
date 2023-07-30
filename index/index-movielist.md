---
status: 1
cssClasses: cards, cards-align-bottom, cards-cover,cards-1-1, table-max,cards-cols-8
banner: "![[movies.jpg]]"
banner_y: 0.53039
banner_icon: 🎥
---

- [u]	[[HomePage|返回主页]] | [[index-ITNote|IT笔记]] | [[index-readlist|阅读清单]] | [[index-日记|日记]] |

---

`button-shuying`  说明：升级版，输入电影名称、新建笔记。默认状态(status) 为”想看“ 。

---

#  想看

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,year as Year, director as 导演,rating as 评分
from  "电影"
where genre !=none & status="想看" 
sort file.cday asc 

```
---

#  看完

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,year as Year, director as 导演,rating as 评分
from "电影"
where genre !=none & status="看完" 
sort file.cday asc 

```
---

# 再看

```dataview
table without id ("![](" + cover + ")") as Cover, file.link as Name,year as Year, director as 导演,rating as 评分
from "电影"
where genre !=none & status="再看" 
sort file.cday asc 

```
---
