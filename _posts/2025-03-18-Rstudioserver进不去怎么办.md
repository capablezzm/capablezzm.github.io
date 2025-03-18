---
layout: post
title: "Rstudioserver进不去怎么办？"
date: 2025-03-18
categories: R
tags: [心得, 学习, Linux, R]
toc:  true
---

# 简介
R studioserver有一个缺点，就是其环境变量是保存在Linux的内存里，如果上一次退出的时候不清理，则下一次使用的时候很可能无法登录。

![image.png](https://cdn.jsdelivr.net/gh/capablezzm/capablezzm.github.io@main/images/2025/3/1742277624276.png)

如果出现了一直转圈的情况，那么可以通过以下的方法来清理内存。

# 第一步：删除R studioserve的缓存
```
rm -rf /home/user/.local/share/rstudio/sessions
```

其中，user是你自己的用户名。

# 第二步：查找自己的进程

```
ps -u user
```

![1742277876746.png](https://cdn.jsdelivr.net/gh/capablezzm/capablezzm.github.io@main/images/2025/3/1742277881957.png)

可以看到图上的ression进程号为13265

# 第三步：Kill掉rsession的进程

```
kill-9 13265
```

杀掉之后，重启r studio server网页即可正常使用
