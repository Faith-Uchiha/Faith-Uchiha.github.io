---
title: Python入门
date: 2017-11-08 11:50:11
update: 2017-11-08 11:50:11
categories: 机器学习
tags: Python基础

---

### 目标：完成语法基础

以下内容基于Python3.5.2文档

1.字符串：用' '或者“ ”，但是**输出一定是' '**显示的。p.s:如果字符串中有' 或“ ，要用转义\

```
>>> '"Yes," he said.'
'"Yes," he said.'
>>> "\"Yes,\" he said." 	# 中间的'与首尾相同，所以才需要\ 
'"Yes," he said.'
>>> '"Isn\'t," she said.'    # 这里的\会原样输出是因为在子字符串内
'"Isn\'t," she said.'
```

注意，如果直接>>>输入字符串，转义字符\n、\t等不能直接输出，用print就可以

```
>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print(), \n is included in the output
'First line.\nSecond line.'
>>> print(s)  # with print(), \n produces a new line
First line.
Second line.
```

Python**没有字符类型**，字符就是长度为1的字符串

下标