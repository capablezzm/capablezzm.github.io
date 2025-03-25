---
layout: post
title: "zotero一键替换eng为en，以适应毕业论文的格式"
date: 2025-03-18
categories: python
tags: [心得, 学习, Linux, python]
toc:  true
---


# 简介
zotero的网页插件在导入文献时非常好用，但有的时候，部分参考格式无法识别eng和en，导致出现中文的etal和等混乱，这时候我们可以使用其开发者工具进行修改。

# 1.选中文献，打开开发者工具


按照下面的顺序，打开zotero内的开发者工具


![屏幕截图 2025-03-18 141351.png](https://cdn.jsdelivr.net/gh/capablezzm/capablezzm.github.io@main/images/2025/3/1742278482697.png)

# 2.输入下面的JavaScript代码

```JavaScript

zoteroPane = Zotero.getActiveZoteroPane();
items = zoteroPane.getSelectedItems();
var rn=0; //计数替换条目个数
var lan="en"; //替换的语言
for (item of items) {
var la = item.getField("language");
if (la=="")  //如果为空则替换
 {item.setField("language", lan);
rn+=1;
 await item.saveTx();
}
if (la=="English")  //如果为English则替换
 {item.setField("language", lan);
rn+=1;
 await item.saveTx();
}
if (la=="en-US")  //如果为en-US则替换
 {item.setField("language", lan);
rn+=1;
 await item.saveTx();
}
if (la=="eng")  //如果为eng则替换
 {item.setField("language", lan);
rn+=1;
 await item.saveTx();
}
}
return rn+"个条目语言被替换为"+lan+"。"


```


如此一来，可以实现eng与en之间的批量互换。