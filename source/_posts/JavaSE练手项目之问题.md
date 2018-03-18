---
title: JavaSE练手项目之问题
date: 2017-09-28 23:02:19
update: 2017-09-28 23:02:19
categories: Java问题汇总
tags:
---

今天在使用 java.util.Random类产生随机数的时候，遇到一个问题。

以下是出问题的代码

<!-- more -->

```
if(mis_step==0)
{
	mis_step = r.nextInt(5);
	this.fire();
}
mis_step --;	
```
mis_step在对象new出来之后，成员变量已经用r.next(5)初始化。

在Debug中运行发现：Wacth窗中观察，mis_step会在**运行一段时间之后变为负数，过了一会儿又变回了正数**。

解决：变为负数的原因是，**nextInt(Bound) 返回的值是0~Bound-1的Int类型数**

很有可能在if的 **mis_step = r.nextInt(5)**这个赋值语句中得到0值，随后mis_step --就会变为负数，然后就死掉，不会再有重新复制的机会，**炮弹再也不会发出**。

看到变回正数的原因是：其实看到的是下一个Tank的mis_step了，而不是自身自动回复。

所以,为了避免出现负数，一般的**用法都是 r.nextInt(Bound)+XX**