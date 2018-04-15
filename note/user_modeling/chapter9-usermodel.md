# Case Studies in workload modeling

we can create workload modeling in many different areas

## human user behavior

it will describe the pattern of how users generate new work when they interact with computer system.

### sessions and job arrivals
----
the basic character:

![image](workload_modeling/pic_1.png)

the session starts and ends depend on following:

![image](workload_modeling/pic_2.png)

from this we can extrat the following character:

- the start time of weekday or weekend;the start time at moring, noon and night
- when the user ended the previous session()
- how long the session has been going on 

response time is a much better predictor of subsequent user behavior than slowdown(8.4)

the probability of a session break as a function of the last job’s
response time.

![image](workload_modeling/pic_3.png)


### interactivity and think times
----
three levels of arrivals:

![image](workload_modeling/pic_4.png)

the third level is closed form, the user may abort the individual jobs and even the whole job if the system is congested.

user think time was correlated with response time.

we need two distribution.one is the short gaps within sequences of events.This work has already done by[616].the other is actual think times.

modeling batch jobs,also need two distribution.one is the intersubmittal gaps within a batch.the other is the distribution of think time that occur between batches.


### daily activity cycle
----

high levels og activity during normal working hours, possibly with a small dip for lunch.Actity in the evening is much lower, and it reaches a minimum in the pre-moring hours, around 4 or 5 AM.

<font color="red"> 
someone has proposed a model for the arrival rate of job s at a workstation.
section 6.5.1 hava also proposed a simple method.
</font>

### patience
----

most people only tolerance a few seconds delay.

### mobility
----

the movement of users affect the characteristics of the workload they generate,because they may roam from one system to another during an ongoing activity.

suggest a user mobility model that can generate synthetic tracks that mimic the real ones.

![image](workload_modeling/pic_5.png)

### runtime estimates

the relation between user runtime estimate and the real runtime:

![image](workload_modeling/pic_6.png)

it actually provides rather good estimates that do not reflect reality.
there is no correlation between runtime and accurancy.

a model has been proposed to generaye synthetic runtime estimates that mimiv those chosen by real users.
# my thoughts
1. 可以通过对用户建模，估计在一段时间内会有多少用户提交数据。进行超算负载预测（这个时间段可以是一天，也可以是一个星期）

2. how user react to the system performance has been modeled
