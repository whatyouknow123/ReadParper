# 题目

<p>data mining method for anomaly detection in the supercomputer task flow</p>

# 作者
- vadim voevodin
- vladimir voevodin

# 摘要

<p>利用数据挖掘技术，提出了一个在task flow中进行异常检测的方法。使用System monitoring 来获取数据，用随机森林算法来分析数据</p>

# 介绍

1. 有异常行为的application可以被视作s sign of extremely low performance

2. different launched of the same software package, which would help detect and analyze typical application behavior patterns.[1]--->是不是对于考察不同版本的效果是有用的

3. 因为无法精确的定义什么是异常，所以我们需要使用数据挖掘技术

4. 本文的方法能够识别异常任务并且告知人们

 

# 背景：

1. 选择的特征：
	- cpu user load

	- number of flops

	- memory usage:number of L1/L3 cache misses, memory load/store instructions per second

	- infiniband usage:number of bytes/packets sent and receivesd per second

	- system load(loadavg)
	- 根据经验，对于每一个任务只取他的中间值，和觉绝对值(最大值减去最小值)

2.  如何一个application的一个或者多个动态特征和多数application的标准值有出入的话，那么它就会被称为异常。

3. 我们对特别有效的application和特别无效的application都很感兴趣，前者可以提高效率，并且帮助我们重新定义异常，后者的话取消他的使用也可以帮助我们提高效率

4. 识别application anomaly的两种方式：

	- 将动态特征值和threshlos进行对比。

	- 找到和其他application明显不同的值。

 

# 方法：

## 选择最优的识别算法

1. K-means和自动化异常检测技术(LOF,LOCI)，经过测试时不适用的

2. 采用的时有监督的学习算法：LDA, Decision Tree和随机森林。因为用的是监督学习算法，所以预先让专家对部分数据打了标签。然后让7折交叉验证来证明正确性，发现随机森林的效果是最好的。

## 最优化选择的方法准确性

1. changing the integral characteristics。比如可以用算数平均值代替中间值，但是实际上效果不好。

2. identifying the most important characteristics。可以发现所有的特征都很重要，移除任何一个都会使精度下降

3. adding derivative characteristics。加入了五个额外的特征，使得精度提高到了0.85

 

# 结论

1. prompt anomaly detection in a supercomputer task flows

2. random forest algorithm is the most suitable in our situation

3. 加入额外的特征会使精度提高