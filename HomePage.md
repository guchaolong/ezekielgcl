
# 站内导航  | [[index-ITNote|IT笔记]]  | [[index-日记|日记]] | [[index-C|永久笔记]] |---| [[项目看板|项目看板]] | [[index-D|落叶寻枝]] | [[index-E|初稿汇聚]] | [[index-F|编辑校对]] |---| [[关键词漫游|找灵感]] | [[index-H|帮助]] |  



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



<div style="background-color:#53a9d7;text-align:center;">我是有底线的</div>