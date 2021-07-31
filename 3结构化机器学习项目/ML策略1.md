#### ML策略1

##### 正交化

##### 单一数字评价指标

通过定义优化和满足目标。

在满足“满足目标”的前提下，选择“优化目标”最好的算法。

性能

性能上限：贝叶斯最优错误率。

![image-20210728140325664](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728140325664.png)

当性能接近或超越人类水平时，更加关注模型的方差。（训练集和开发集的表现差异）

反之，更加关注模型的偏差。

训练误差与贝叶斯误差的差值为可避免误差。（除非过拟合，否则训练误差大于贝叶斯误差）

不同的场景专注于不同的策略，使用避免偏差策略还是避免方差策略。

在训练时考虑人类水平表现，来避免工作着力点。

##### 误差分析

手工分析错误样例，找到性能瓶颈。

深度学习算法对随机误差很健壮。

![image-20210728153624629](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728153624629.png)





##### 快速开发

![image-20210728155301538](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728155301538.png)

#####  数据不匹配

dev和test set必须同分布，但是train和dev/test分布可以不同（如训练来自网页高清图，测试来自手机图）。

如20w网络高清图，1w的手机模糊图。

方法1：随机抽取。这样的话，三者同分布，但是dev/test和目标的分布相差甚远（目标是手机应用）

方法2：dev/test全部使用手机模糊图，剩余的放入训练集。

![image-20210728162148655](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728162148655.png)

当train和dev/test不来自同一个分布，并且train和dev的误差相差很大，那么可能是模型的方差较大，也可能是数据不匹配（分布不同）的原因。

为了确定是那种问题，可以设计一个training-dev set，它和train set同分布。在training-dev set上进行测试，如果误差和在train相差不大，那么说明是数据不匹配的问题。否则表示有可能是模型的方差较大。

![image-20210728162758797](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728162758797.png)

![image-20210728163406335](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728163406335.png)

##### 定位数据不匹配

当你了解开发集错误的性质时，就会了解开发集和训练集的差别。

![image-20210728164059694](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210728164059694.png)

人工数据合成：避免对合成部分过拟合。

