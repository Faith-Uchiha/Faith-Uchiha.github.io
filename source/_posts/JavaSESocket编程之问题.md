---
title: JavaSESocket编程之问题
date: 2017-09-16 10:31:24
update: 2017-09-16 12:17:25
categories: Java问题汇总
tags:
---

# 问题1

从标准输入流（即控制台输入）读取字符，**不能使用ReadUTF()方法**，否则会读取不进来。

<!-- more -->

# 问题2

使用BufferedReader类的readLine()方法读取System.in的输入之后，

再用WriteUTF()发送给Server，**server用ReadUTF()读的话，会抛异常**。

# 解决办法

### 对于问题1
改用BufferedReader的ReadLine()

### 对于问题2
尚未解决。**个人猜测：**因为**编码**不一样，WriteUTF/ReadUTF是要求Unicode编码，而**中文操作系统**，从标准输入流输入的应该是**GBK编码**

待以后深入学习Java能够看Java源码的时候再来解决。

------------
问题2解决：真正的原因并不是编码的问题，即使client端改为PrintWriter类的println方法，server端改为BufferedReader类的readLine()方法，还是会有异常！

而是**没有调用flush()方法！！！**。缓冲区没满，不调用flush()，输出流是不会输出的。所以才会抛出异常。



**重要：** flush()方法何时使用：涉及到**缓冲区**的类，都应该使用。

建议除了FileOutputStream和FileWriter类，**BufferedWriter**、DataOutputStream、PrintWriter、ObjectOutputstream等输出流**都应该写flush()**。

File\*\*\*输出流是以二进制的形式写入的，所以flush()调用也无效果，可用可不用。  **FileOutputStream()没有重写flush()，所以没效果**






