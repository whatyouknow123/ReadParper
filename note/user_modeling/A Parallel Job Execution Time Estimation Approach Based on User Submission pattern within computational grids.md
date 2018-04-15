# 题目
a parallel job execution time estimation apprach based on user submission pattern within computational grids

# 作者
- Feng Liang
- Yunzhen Liu
- Hai Liu
- Shilong Ma
- Bettina Schnor

# 发表于
International Journal of Parallel programing

# 摘要
文章通过对用户行为进行聚类能够得到比任务相似性比较更高的准确率， 同时揭示了用户提交模式

# 效果
和state-of-art算法相比，准确率提高了5.6%，同时计算量减少了3.8%

# 具体内容
## 简介
##### 主要贡献
1. 提出了用户提交模式：使用了经验分布函数和层次聚类技术
2. 基于用户的聚类提出了一种全新的估计方式来提供整体的估计性能

##### 相关工作
1. 可以考虑将user estimation作为一个特征。但是我们不是直接的利用这个特征，而是用user utility function来定义job的价值。
2. 输入特征
	- job id
	- job submission time
	- user id
	- group id
	- waittime
	- runtime
	- nproc
	- usedcputime
	- usedmemory
	- reqnprocs
	- reqtime
	- status
	- queueid
	- user estimation 
	- executable program id
3. 用户分类算法
![](pictures/user_classifition_algorithm.png)

4.基于用户聚类的时间预测算法
![](pictures/prediction_algorithm.png)

	smooth算法是一个加权函数，它让距离当前时间越近的job的权重越大

##### 评估指标
1. 准确率： 如果预测值大于准确值，就要准确值除以预测值；反之，则相反
2. predictedRatio:算法运行n次，有意义的预测值的个数除以总的运行次数
3. 平均误差： n次运行的平均误差
4. 平均时间： n次运行所花费的平均时间

# 总结
1. 摆脱以往直接从特征预测时间的传统方式，先对用户进行层次聚类，然后基于聚类结果对于job运行时间进行预测。
2. First, a user submission pattern-based user group-
ing mechanism using the ECDF distribution and the hierarchical clustering approach is proposed to conduct the user grouping. Then an improved estimation mechanism with the time complexityO(1) is proposed, which covers the resource - job execution time correlations by using the common available attributes from the grid workload traces and respects the job “freshness” by adopting the exponential smoothing method. The experiments show that compared to state-of-art algorithms, UBCETE can not only improve the overall estimation accuracy, but also reduces the time consumed.