# 题目

<p>crowdsourced data management:overview and challenges</p>

# 作者

- GuoLiang li
- Yudian Zheng
- Ju Fan
- Jiannan Wang
- Reynold Cheng

# 质量控制

## characterize a worker's quality
1. model each worker as a single value that the worker will answer tasks correctly.
2. for each user, it will introduce the confidence interval into the probability.
3. model each worker's quality as a confusion matrix, who represents the worker's ability in answering different labels.
4. model the diverse skills of a worker, captures the worker's answering abilities for different domains.

## infer worker's quality

1. adopt qualification test
2. use golden task, which mix tasks with ground truth into tasks assigned to workers.
3. compute each worker's quality in a unsupervised

