---
cssClasses: cards, cards-align-bottom, cards-cover,cards-1-1, table-max,cards-cols-8
# banner: "![[sunset-ge28cf669b_1920.jpg]]"
banner: "![[cat.jpeg]]"
banner_x: 0.02235
banner_y: 0.784
banner_icon: 🌴
tags: index
---





# 站内导航 | [[index-码农笔记|码农笔记]] | [[index-阅读清单|阅读]] | [[index-电影清单|电影]] | [[index-日记|日记]] |

---

## 标签云
```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: WordCloud

#-----------------#
#- chart data    -#
#-----------------#
data: | 
  dataviewjs: 
  return (() => {
    const tags = this.app.metadataCache.getTags();
   
    let dataArray = [];
    Object.keys(tags).forEach(key => dataArray.push ({tag: key.replace("#",""),count: tags[key]}));
    return dataArray;
   })();


#-----------------#
#- chart options -#
#-----------------#
options:
  wordField: "tag"
  weightField: "count"
  colorField: "tag"
  enableSearchInteraction:
    field: "tag"
    operator: "tag"
style:
  backgroundColor: "translucent"

#-----------------------------------------------#
#--- 可选择多彩颜色(colorField) 或单色 (color) ---#
#---  colorField: "tag" ---#
#---  color: "#bb5548" ---#
#-----------------------------------------------#

  wordStyle:
    rotation: 0
```


# 所有标签

```dataviewjs
// 生成所有的标签且以 | 分割，修改时只需要修改 join(" | ") 里面的内容。
dv.paragraph(
  dv.pages("").file.tags.distinct().map(t => {return `[${t}](${t})`}).array().join(" ")
)
```


## 文件创建时间-日历视图



```dataview


calendar file.ctime


```


## 笔记排行榜
```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Bar

#-----------------#
#- chart data    -#
#-----------------#
data: | 
  dataviewjs:
  return dv.pages()
           .groupBy(p => p.file.folder)
           .sort(p => p.rows.length)
           .map(p => ({folder: p.key || "ROOT", count: p.rows.length}) )
           .array()
           .reverse();

#-----------------#
#- chart options -#
#-----------------#
options:
  xField: "count"
  yField: "folder"
  padding: auto
  height: 400
  color: "#ff2d51"
  enableSearchInteraction:
    field: "folder"
    operator: "path"
  meta:
    count:
      alias: "数量"

```


## 柱状图
```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Column

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
  return dv.pages()
           .groupBy(p => p.file.folder)
           .map(p => ({folder: p.key || "ROOT", count: p.rows.length}))
           .array();

#-----------------#
#- chart options -#
#-----------------#
options:
  xField: "folder"
  yField: "count"
  padding: auto
  color: "#801dae"
  enableSearchInteraction:
    field: "folder"
    operator: "path"
  columnStyle:
    fillOpacity: 1
    lineWidth: 0.9
    strokeOpacity: 1.7
    shadowColor: "grey"
    shadowBlur: 5
    shadowOffsetX: 5
    shadowOffsetY: 5
  
  meta:
    count:
      alias: "文件数量" 
```


## 饼状图-文件数量

```chartsview
#-----------------#
#- chart type    -#
#-----------------#
type: Pie

#-----------------#
#- chart data    -#
#-----------------#
data: |
  dataviewjs:
  return dv.pages()
           .groupBy(p => p.file.folder)
           .map(p => ({folder: p.key || "ROOT", count: p.rows.length}))
           .array();

#-----------------#
#- chart options -#
#-----------------#
options:
  angleField: "count"
  colorField: "folder"
  radius: 1
  label:
    type: "spider"
    content: "{percentage}\n{name}"
  legend:
    layout: "horizontal"
    position: "bottom"
```



-  [[#站内导航 index-码农笔记 码农笔记 index-阅读清单 阅读 index-电影清单 电影 index-日记 日记|回到顶部]]


<div style="background-color:#53a9d7;text-align:center;">我是有底线的</div>