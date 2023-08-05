

参考
[可能在ob会用一辈子的dataview代码](https://mp.weixin.qq.com/s/U58eLjVc4_78NFSzgLJb2A)

# 所有标签

```dataviewjs
// 生成所有的标签且以 | 分割，修改时只需要修改 join(" | ") 里面的内容。
dv.paragraph(
  dv.pages("").file.tags.distinct().map(t => {return `[${t}](${t})`}).array().join(" | ")
)
```



# 根据一个字段 汇总
```dataview  
Table without id file.link   
where contains(file.name,"Java")  
Sort file.size desc
```

# 根据两个字段搜索 汇总
```dataview  
Table without id file.link as 含A和B字段的文件  
where contains(file.name,"A") or contains(file.name,"B")  
Sort file.size desc
```

# 使用Obsidian的天数
```dataviewjs  
const 截取文件日期 = dv.pages("").file.sort(t => t.cday)[0]  
const 计算时间差 = parseInt([new Date() - 截取文件日期.ctime] / (60*60*24*1000))  
dv.paragraph("---");  
dv.header(6,"🖊️已使用Obsidian "+计算时间差+"  天")  
dv.paragraph("---");
```

# 码字统计.某标签(Java)近一个月码的总字数
```dataviewjs  
//统计近一个月内，指定标签的所有文字总和.  
const 来源路径 = '""'//要统计的路径  
function Time_MonthStamp(timeString, dur){  
  const time = new Date(timeString);  
  return new Date(time.getFullYear(), time.getMonth()+dur, 0,0,0,0);  
}  
  
function appearTime(v){  
 return v.year+"/"+v.month+"/"+v.day  
}  
const time = new Date()  
const startTimeStamp = Date.parse(Time_MonthStamp(time,0))  
const pages = dv.pages(来源路径)  
var arr = []  
for (let apage of pages){  
 let mtime = Date.parse(Time_MonthStamp(apage.file.mtime,0))  
 //dv.paragraph(mtime)  
 if (mtime == startTimeStamp){  
  arr.push(apage)  
 }  
}  
arr = arr.filter(function(k){  
 for(let tag of k.file.tags){  
  if(tag=='#Java'){return 1}//标签可自定义修改  
 }  
 return 0  
})  
var zishu = {}  
var total = 0  
for(let apage of arr){  
 var content = await dv.io.load(apage.file.path)  
 var num = content.replace(/\s+/g,'').length  
 num = parseInt(num/3.5)//统计时空格已去除.但因一字节等于一字母.一符号.一换行符.而一汉字是两个字节，所以字节与实际字数存在一定比例.可根据编写英文和中文写作调整比例.  
 zishu[apage.file.path] = num  
 total += num  
}  
dv.paragraph('总字数为预估数: '+total)  
dv.table(["文件名","大约字数","修改时间"],arr.map(k => [k.file.link,zishu[k.file.path],appearTime(k.file.mtime)]))
```

# Calendar月度编辑量视图

```dataview  
Calendar  
file.mday
```
# 生成根据文件修改时间
```dataview  
list "修改" + file.mtime  
From "码农笔记"  
LIMIT 10
```


# 倒计时
```dataviewjs  
const 倒计时日期="2023/8/15"// 自定义修改其中的时间  
const 字体大小="1"//1最大反之6最小，只能1到6  
const 倒计时日期转换 = new Date(倒计时日期);  
const 今天日期 = new Date();  
const 倒计时减去今天日期 = 倒计时日期转换.getTime() - 今天日期.getTime();  
dv.header(字体大小,"🗓️距离"+倒计时日期+"还有"+parseInt(倒计时减去今天日期 / (60*60*24*1000)) + "天");
```



```dataviewjs
const 倒计时日期="2023/8/15"// 自定义修改其中的时间const 字体大小="1"//1最大反之6最小，只能1到6const 倒计时日期转换 = new Date(倒计时日期);const 今天日期 = new Date();const 倒计时减去今天日期 = 倒计时日期转换.getTime() - 今天日期.getTime();dv.header(字体大小,"🗓️距离"+倒计时日期+"还有"+parseInt(倒计时减去今天日期 / (60*60*24*1000)) + "天");
```
# 当前文件创造和修改时间
```dataview  
list  
"创建时间 "+file.cday+" ,最后修改时间 "+file.mday  
where file.name = this.file.name
```

# 人生时间窗口
```dataviewjs  
//可根据个人要计算的时间，做变量删增调整，计算板块与输出，删除增加要同时进行  
const 自己出生日期 = "1991/1/1"  
const 爸爸出生日期= "1964/1/1"  
const 妈妈出生日期= "1968/1/1"  
const 孩子出生日期= "2021/1/1"  
const 孩子上学日期= "2025/1/1"  
const 考研日期= "2025/1/1"  
const 工程结束日期= "2024/1/1"  
const 工程总天数= 1095  
const 自己所在的城市名字= "XX城市"  
const 到这个城市的时间= "2020/1/1"  
const 预计退休时间= "2061/1/1"  
const 预计变成天使的时间= "2091/1/1"  
//------------------------------------------------------<计算板块>  
//----------------固定的年月周时间  
const 今年已过 =parseInt((new Date().getTime()-new Date(new Date().getFullYear()+"/1/1").getTime())/(60*60*24*1000));  
const 本月剩 =parseInt((new Date().getTime() - (new Date((new Date().getFullYear()),(new Date ().getMonth()+1),1)).getTime())/(60*60*24*1000));  
//---------------个人计算的时间  
const 自己到人世间 =parseInt((new Date(自己出生日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 爸爸岁数 =parseInt((new Date(爸爸出生日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 妈妈岁数 =parseInt((new Date(妈妈出生日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 孩子天数 = parseInt((new Date(孩子出生日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 女儿离上学还有 =parseInt( (new Date(孩子出生日期).getTime() - new Date(孩子上学日期).getTime())/(60*60*24*1000));  
//-------------考研和工作项目计算  
const 离考研还有 =parseInt((new Date(考研日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 工程项目还有 =parseInt((new Date(工程结束日期).getTime() - new Date().getTime())/(60*60*24*1000));  
const 到这个城市已经 =parseInt((new Date(到这个城市的时间).getTime() - new Date().getTime())/(60*60*24*1000));  
//--------------退休和变成天使时间的计算  
const 距离退休 =parseInt((new Date(预计退休时间).getTime() - new Date().getTime())/(60*60*24*1000));  
const 估计还能活 =parseInt((new Date(预计变成天使的时间).getTime() - new Date().getTime())/(60*60*24*1000));  
//----------  
//----------  
//----------  
//------------------------------------------------------<下面输出板块>  
dv.paragraph("---");  
dv.header(2,"🕰️人生的时间窗口");  
dv.header(6,"📅今年已过"+今年已过+ "天"+",距明年"+parseInt(365-今年已过)+"天"+",年进度"+((今年已过/365)*100).toFixed(1)+"%");  
dv.header(6,"📅本月剩"+本月剩+"天,"+"现第"+parseInt(今年已过/7)+"周"+",剩"+parseInt((365-今年已过)/7)+"周");  
dv.paragraph("---");  
dv.header(6,"👨‍🦱自己到人世间"+自己到人世间 + "天"+parseInt(自己到人世间/365)+"年");  
dv.header(6,"👨‍🦳爸爸岁数"+爸爸岁数 + "天"+parseInt(爸爸岁数/365)+"年");  
dv.header(6,"👩‍🦰妈妈岁数"+妈妈岁数 + "天"+parseInt(妈妈岁数/365)+"年");  
dv.header(6,"👦孩子天数"+孩子天数 + "天"+",离上学还有"+女儿离上学还有+"天")  
dv.paragraph("---");  
dv.header(6,"🏙️到"+自己所在的城市名字+"已经"+到这个城市已经 + "天"+"约"+parseInt(到这个城市已经/365)+"年");  
dv.header(6,"👷‍♂️工程项目还有"+工程项目还有 + "天"+",工程项目已过"+parseInt(工程总天数-工程项目还有)+ "天");  
dv.paragraph("---");  
dv.header(6,"💯离考研还有"+离考研还有 + "天"+"约"+parseInt(离考研还有/365)+"年");  
dv.paragraph("---");  
dv.header(6,"🃏距离退休"+距离退休 + "天"+"约"+parseInt(距离退休/365)+"年");  
dv.header(6,"😇变成天使预计还有" +估计还能活+"天"+"约"+parseInt(估计还能活/365)+"年");  
dv.paragraph("---");
```