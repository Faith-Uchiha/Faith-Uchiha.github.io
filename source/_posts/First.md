---
title: First
date: 2017-08-16 21:58:18
update: 2017-08-18 18:38:45
tags: 
  - 随笔 
  - 初次尝试
categories: 初入博客
---

这是我建博客后尝试写的一个.md测试

# 遇到的坑

## 1.yilia主题的所有文章按钮

总算是所有东西都弄好了，弄“所有文章”的显示的时候，竟然报错

**ERROR plugin load failed hexo-generator-json-content**

<!-- more -->
后来才发现，原来是因为我的node.js的版本太低了

原来我用的是yilia主题，后来发现categories和tags怎么都搞不好。

最后就换了next主题

## 2.next主题添加站内搜索

hexo-generator-searchdb这个也安装了：

```
$ npm install hexo-generator-searchdb --save
```

站点配置文件也改了：

```
search:
  path: search.xml
  field: post
  format: html
  limit: 10000
```

一直无法搜索，原来还少了最后一步：主题配置文件

```
local_search:
  enable: true
```

## 3.Markdown语法问题

使用“\`\`\`” 这个字符的时候，
最好第一个“\`\`\`”之后，（这里的\`是用转义字符“\”打的）回车再写文本

不然很容易和下一个要引用的段穿在一起

还有\#后面要空格才能接文本