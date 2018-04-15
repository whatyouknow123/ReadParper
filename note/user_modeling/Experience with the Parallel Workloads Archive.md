# 题目
Experience with the Parallel Workloads Archive

# 作者
- Dror G.Feitelson 
- Dan Tsafrir
- David Krakov

# 发表于
Journal of Parallel and Distributed Computing, 2014

# 摘要
真实的超算数据会遇到各种问题，比如：数据缺失，数据不连续，数据错误等等，如果我们不处理这些问题的话，那么该数据对于问题的研究将会有很大的影响。本文的目的就在于根据已有的经验以及彼此之间的关联来指导数据处理。

# 主要内容

##  介绍
从1999年开始PWA和GWA的点击率逐年增加，人们越来越重视超算数据分析，但是超算数据的质量普遍不是很好。
拥有一个好的数据质量是至关重要的。
本文的主要个贡献在于记录如何处理超算数据（parallel workload archive）

## log format
1.start time and end time 的定义不清
2.uwall time 并不能表示运行时间
3.当jobId的值更大但是它的submit time更小时，是因为管理员更改了它的submit time，让它能够有更高的执行级别
4.job status是一个值得注意的特征

## problems with log data
- 不完整数据
>submit, start and end times 只有少部分数据是缺失的
>cpu time or memory 更经常缺失

- 数据不一致
>（1）少部分的tasksreq不等于taskreq
>（2）nodesreq = nodelist的大小
>（3）当start time小于submit time的时候的做法：none， start = submit, submit = start,(start = submit, end+=submit-start)

- 错误数据

>（1）有些错误数据是因为出错
>（2）有些错误数据是有意为之
>（3）最经常出现的一种错误是资源利用率超过了百分之百

- 环境变化
>因为系统配置等的不同，会引起workload的记录的误差。
一个很重要的改变就是系统容量的明显变化
the scheduler could use different sets of nodes for different queues  during prime time and non-prime time 
下午四点之后更加适合4小时以上的作业， 周五提交的作业经常是超过15个的长作业
环境很可能对我们的数据造成未知的影响

- 非典型行为

>While the large-scale flurries pop out and are obviously behavioral outliers, the identification of small flurries is
more contentious.
job size anda runtime affects performance
user residence pattern is a strange attribute.In most logs, users are observed in the first few weeks, then new user arrivals stabilize at a lower rate.The arriving pattern is normal, but the leaving pattern is abnormal.The different machine has different behaviors.

- end effects
>jobgs with smaller time are not logged in the begining time because the log has not start.The opposite effect happens at the end of the log.

>When performing a simulation using a log, it is important to discard some initial subset of the results in order to
allow for warmup. Also, stop measuring when the last arrival occurs, because after that time the simulated jobs will
encounter less and less competition, leading to unrealistically good results.

- missing Downtime Data
>job data may help in analyzing failure and prodecing reliable data regarding the severity and effect of failure.

## attempting to improve Log data quality

- removing initial low-load intervals
- reconstructing Missing data
- data cleaning by removing flurries
- Enforcing the capacity constraint

## conclusion
