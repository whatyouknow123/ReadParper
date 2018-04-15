# 题目
Session-Based, Estimation-less, and Information-less Runtime Prediction Algorithms for parallel and grid job scheduling 

# 作者
- David Talby
- Dan TsaFrir
- Zviki Goldberg
- Dror G.Feitelson

# 发表于

# 摘要
##### 提出三种预测方式分别针对三种不同的情况。
- user sessions:利用整个历史任务和用户的估计时间
- estimation-less:仅利用整个历史任务
- information-less:既没有历史任务也没有估计时间

#具体过程

## session-based prediction 
1.  the  Recent  User History  Predictor  is  successful,  but  also  suggests  that basing a predictor directly on sessions may be even better.因为同一个session内部的任务具有更大的相似性。
2.  按照session将历史任务进行划分（in  the  same  session  if  the 
think  time between  them (the  time  between  the  termination  of  the  first  one  and the  arrival  of  the  next)  is  smaller  than  twenty  minutes. ） 
3. 定义了一个相似列表。这个列表定义了比较对象。
4. 在距离最近的session里面按照相似列表找到相似的任务，以他们的均值作为估计值。如果当前的session找不到的话，就到它附近的session去找。
## estimation-less
和session-based prediction的方法，大同小异。区别在于：（1）因为没有用户估计值，因此对于首次出现的任务，预测它的值为1秒。（2）如果任务错过了deadlines,那么就将它的预测值的结果乘以10。（3）不在相似列表中使用用户估计值这个属性。
## information-less
