# 题目

<p>job scheduling with adjusted runtime estimates on production supercomputers</p>

# 作者

- wei Tang
- Narayan Desai
- Daniel Buettner
- Zhiling Lan

# 发表于

<p>Journal of parallel and distributed computing, july 2013</p>


# 重点

- We studied the **inaccuracy of user runtime estimates** in large amount of job traces.
- We proposed a set of **runtime adjusting schemes to better the estimation accuracy.**
- We refined our schemes to **avoid impact of too much adjusting **(underestimates).
- We used real job trace to evaluate our schemes and got positive results.

# 摘要

## 实验平台
- from production leadership-class computer
- propose a walltime adjusted schemes producing more accurate estimates
## 实验效果

- 预测的平均准确率提高了35%
- the system performance in terms of average waiting time and weighted average waiting time can be improved by up to 22% and 28%


# 介绍

- 用户预测运行时间是一个非常重要的指标，the resource manager kill jobs when this time expires
- 有三个时间job actual time, user-requested walltime, job walltime of scheduler
- "walltime adjustment" refer to the efford od a system to adjust the user's estimates to create possibly more accurate walltime estimates
- "walltime estimates" refer to the runtime estimates either provided by users or adjusted by the system


# 相关工作

## 用户估计时间的不准确性

<p>用户估计的运行时间和实际的运行有很大的差距，一般用户为了避免任务被杀死，都会过高的估计任务的运行时间</p>

## 用户估计时间在调度上的影响
<p>用的人认为准确的运行时间估计是有用的，有的人认为是没用的， 甚至不准确性还可以提高性能</p>

## 提高用户估计时间准确性的动机
<p>为了更好的backfilling和queue sorting</p>

## 已知的提高用户估计时间的方法
- 移除达到用户预测时间就会Kill job的威胁；给准确估计的任务以奖励
- 使用long uniform distroibution of time 
- 使用 the top of a 95% confidence interval of job runtime
- 使用中间值乘以1.5作为标准差，和遗传算法
- **基于实例的**学习算法
- 同一个用户最后的两个任务的运行时间的均值作为与预测时间
- 在置信区间内使用**adaptive hybrid method**

# studying the inaccuracy

## 使用特征
- job id
- job size
- submission time
- user-requested walltime
- start time
- end time 
- user name
- project name

## 用户估计的准确性

- r = 任务实际运行时间/用户估计时间
- 将r比值超过1的，都设置为1
- 大约只有25%的任务的r值超过了80%,按照季度来看，r值会在50%左右

# walltime adjustment schemes

## 基本方法
1. 我们所预测的不是一个任务的运行时间，而是获知一个用户对于任务运行时间的预测有多大的准确度
2. 要预测准确度的话，我们最重要的就是要找到和当前任务最相关的若干个历史任务
3. the walltime adjustment从三个方面进行定义：similarity, recency, **aggressiveness**
4. aggressiveness指的就是你在确定了用于预测的job任务之后，采用什么mean, max还是其他的metric作为预测
5. 通过定义任务相似性比较特征，时间任务窗口，和选择的评价指标之后，我们就确定了一个scheme
6. four kinds of key type:only by user name, only by project name, by user and project combination, by the combination of user, project and walltime
7. historical time window:12 months, 6 months, 3 months and 1 months
8. the aggressiveness level:max, 95th percentile, 90th per, 85 per, 80 per, median 

# 结论
1. 通常来说，使用更多的keys和更小的时间窗口，会获得更大的准确性
2. selective walltime adjustment scheme, which allows the scheduler to use system-adjusted walltimes only for waiting jobs while using user estimates for running jobs
3. 不需要use queuing policy favoring short jobs or not to use adjusted walltime estimates for running jobs.