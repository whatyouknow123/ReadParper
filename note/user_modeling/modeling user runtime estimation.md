# 题目
Modeling User Runtime Estimates

# 作者
- Dan Tsafrir
- Yoav Etsion
- Dror G.Feitelson

# 发表于
11th Workshop on Job Scheduling Strategies for Parallel Processing (JSSPP), pp. 1-35, Jun 2005.

# 摘要
本文根据logs中的特征和用户估计中显著的固有属性来构建模型。我们发现用户的行为在不同的workload traces上是相似的。如果仅给本模型提供maximal allowed estimate value和使用该值的jobs的百分比，那么产生的结果将会非常的类似原始分布。

# 效果
in comparison to previous models, simulations that utilize our model are better in reproducing scheduling behavior similar to that observed when using real estimates.

# 介绍
1. killed jobs 和<90secjobs的分布是很不规律的，ok jobs大致会呈现uniform-like histogram
2. 

# 总结
1.本模型的目的在于模拟用户的估计运行时间而不是在于获取正确的运行时间

