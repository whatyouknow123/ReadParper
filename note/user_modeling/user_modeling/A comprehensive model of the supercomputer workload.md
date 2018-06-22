# 题目
<p> A comprehensive model of the supercomputer workload


# 作者
- W.Cime
- F.Berman

# 发表于
<p> Proceedings of the Fourth Annual IEEE International Workshop on Workload Characterization. WWC-4 (Cat. No.01EX538)

# 摘要
<p> 为requested time 和 the possibility of job cancellation建模，同时，提升了为arrival instant和partition size建模的方法。

#过程

## 介绍

<p>这篇文章主要是为requested time和the possibility of job cancellation 建模。同时这个模型对新任务到来预测也有效，因为它是一个seasonal workday cycle.


# 超算系统的用途

<p> 超算中心的workload是由一系列的Jobs组成的。这些job数据记录了job的提交时间，cpu数目，请求的运行时间，实际的运行时间【<font color='red'>科大的数据requested time这一项基本没什么人写</font>】

## 数据来源

<p> ANL
<p> CTC
<p> KTH
<p> SDSC

## 到达时间

<p> 作者先是整个workload按照24划分，得到了每个小时的任务运行数量。然后用一个公式计算job rate
<p><font color="red">不太明白求这个job rate有什么意义</font>

## 获取异常点

<p>目标是获知哪些提交方式不正常的days。
<p>异常检测的方式是：先对一天找到一个它的多项式分布，然后对于这个分布进行聚类。我们认定那些属于单个簇的day属于异常的day
<font color="green">这个从方法上来说，有改进的空间，但是发现那些异常的天数有什么用呢？思考</font>

## 对提交时间建模

<p> 对于所有workload在24小时内的任务量的分布进行多项式近似

## 取消任务

<p> 可以用一个对数函数逼近一个以 cancelation time为横轴，以probability为纵轴的cancelation分布

## Partition Size

<p> 用户选的Partition size一般是二次幂的，原因并不是用户觉得这样是最好的，很大的原因是历史原因遗留下来的习惯和系统中默认设置。

## 运行时间和期望时间

<p> 运行时间占期望时间的比例值a,和运行时间更加相关。
<p> <font color='red'>如果将任务按照运行时间分成几个bucket的话，那么平均比例值会随着运行时间的增加而增加</font>
<p> 原因是执行时间越长的任务越可能是成功的任务

## Accuracy

<p> 用了一个gamma分布去逼近准确率与CDF的分布

## requested time 

<p>也是用了一个函数来逼近requested time 和CDF

# 总结

<p> 这篇文章最有用的地方，在于异常检测这个点。假设我要预测一个用户一天的提交量，那么我是不是可以先用聚类去除掉那些异常的天数，然后在预测。

































































