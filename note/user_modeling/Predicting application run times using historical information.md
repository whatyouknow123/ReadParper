# 论文题目：
predicting application run times using historical information 

# 作者
- Warren Smith
- Ian Foster
- and Valerie Taylor

# 发表于
workshop on job scheduling strategies for parallel processing 1998


# 摘要
根据相似的并行应用以往的运行时间来预测当前并行应用的执行时间。最重要的内容就是如何使用搜索技术定义相似性，执行预测和使用搜索技术来识别好的历史的样例。

# 效果
比其他学者的效果好百分之14到60；均方误差在平均程序执行时间的百分之40到百分之59。遗传搜索的算法会比贪心搜索的效果好。

# 具体过程
## 测试的系统
- argonne national laboratory
- the cornell theory center
- san diego supercomputer
## 可能用到的特征
- type
- queue
- class
- user
- loadleveler script
- excutable
- arguments
- network adaptor
- numbers of nodes
- maximun run time
- submission time
- start time
- run time

## 预测方法
### 定义相似性
按照属性将数据进行类别划分（比如可以根据队列名和用户名，对数据进行划分），我们可以定义一些类别，如果两个job能够落入同一个类别那么说明他们是相似的，如果任何一个类别都不包含他们两个说明他们是不相似的。

### 产生预测
1. 输入是属性划分类别和一系列的workload数据。
2. 基础算法
![](pictures/algorithm_1.png)
3. 预测方法
	- 在同一个category里用平均值作为估计
	- 用LR方法，将node number作为参数，进行估计
	- 如果一个实例，它属于不同的category，那么就选择具有smallest confidence interval作为预测的运行时间
### template definition and search 
使用搜索技术为特定的workload找到最好的templates。
1. 贪心搜索：如果有ｎ个属性，那么它就会获得具有最小均方误差的ｉ个属性组成的集合；这里的ｉ的大小是从１到ｎ
2. 遗传搜索：这个不懂是怎么实现的。

# 总结
它的主要改进在于对templates的选择，使用了贪心和遗传搜索算法，并且后者的效果会比前者的好。
我们可以将预测问题看做是一个聚类问题，然后用同一个类别中的，所有实例的运行时间的均值或者LR回归值看做是它的预测结果。
现在的上海超算中心的数据和有的特征很符合要求，可以考虑实现这个方法，看看效果，作为一个baseline