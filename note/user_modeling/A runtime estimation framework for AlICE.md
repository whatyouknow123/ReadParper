# 题目
A runtime estimation framework for AlICE

# 作者
- Sarunya Pumma
- Wu-chun Feng
- Phond PhunChongHarn
- Sylvain Chapeland 
- Tiranee Achalakul

# 发表于
Future Generation Computer Systems Volume 72, July 2017, Pages 65-77

# 摘要
利用application profiles来预测高性能应用的运行时间。在ALICE和Amazon EC2 cloud上测试过，准确率不错。

# 具体过程
##runtime estimation framework
##### profile sampling
1. 从文件中提取十二个特征
![](pictures/twelve_character.png)
2. 对训练数据和测试数据分别执行profile sampling。
3. profile sampling algorithm
![](pictures/profile_sampling.png)

##### workload classification model
###### construction of the workload classification model
1. 利用前人的工作对收集来的profile数据进行打标签。它的可能类别如下
![](pictures/possible_lable.png)
2. 采集了255个profile数据，利用提取到的mica metrics特征构建一棵决策树，这样就可以知道文件的类别。
3. 训练出的决策树的十折交叉验证的结果是96.89%
###### workload classification 
从输入的workload中提取metic特征，然后利用之前构造好的决策树就知道文件的类别。
![](pictures/decision_tree_algorithm.png)

##### runtime estimation model
###### construction of the runtime estimation model 
1. 它的输入是：metrics, input size(根据类别预先定义)
2. 它的输出是：runtime 
3. 定义的关系模式是：参数不超过11个，他们之间的关系形式可能有五种：logarithmic, natural logarithmic, power, square and linear functions;可能的符号有两种：+和-
所以总的搜索空间是 12^11*5^11*2^10
4. 所采用的搜索方式是ABC（人工群峰算法），总共有3600只蜜蜂，每种1200只，限制迭代的次数是10000次。每次数据运行五次选择R平方值最高的表达式。准确率达到了90%以上。

####### runtime estimation 
根据以上的模型构建方法，对每个类别每种形式（general-purpose, compute-optimized, memory-optimized）找到一个最好的运行时间预测表达式，然后我们只需要根据分类的结果，采用相应的模型就可以知道预测的运行时间

##### validation of framework
1. valida of the profile sampling 

	利用z-score验证抽样数据和全部数据之间的相似性
2. valida of the classfication model

	利用十折交叉验证	
3. valida of the estimation model

	- the prediction error percentage(EP)
	- the mean absolute error percentage(Mean)
	- the weighted absolute error percentage(WAEP)
	![](pictures/three_valida.png)

#总结
##局限性
1. 适用的范围比较小，类别限定在了dwarf list中，不具有普适性
2. 估计模型的表达式的选择有待讨论。为什么有选择文章中定义的五种关系形式。
## 优点
1. 先将profile使用决策树进行分类，然后根据分类的结果，在限定的搜索空间范围内，利用ABC算法找到最优的表达式
2. 采用给定表达式的方式将搜索的空间限制在给定的范围之内，将回归预测问题转化为搜索问题。

## 思考
1. 既然它将结果转化为一个搜索的问题，那么是不是可以考虑别的搜索算法
2. 可以作为一个baseline，但是怎么找到超算数据中的类别是个问题，因为好像并没有这个标签数据。task_name算不算是一种类别呢？