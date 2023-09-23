
参考

[可能在ob会用一辈子的dataview代码](https://mp.weixin.qq.com/s/U58eLjVc4_78NFSzgLJb2A)

# 所有标签

```dataviewjs
// 生成所有的标签且以 | 分割，修改时只需要修改 join(" | ") 里面的内容。
dv.paragraph(
  dv.pages("").file.tags.distinct().map(t => {return `[${t}](${t})`}).array().join(" | ")
)
```
