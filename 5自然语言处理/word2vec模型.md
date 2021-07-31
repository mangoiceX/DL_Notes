#### word2vec模型

##### word2vec中的skip-gram算法

![image-20210731111001426](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210731111001426.png)

选择上下文词$c$,$e_c$是它的词向量表示，$\theta_t$​表示预测词的参数。计算整个词汇表上的softmax。然后与目标进行交叉熵损失计算。

##### word2vec的负采样

skip-gram在整个词汇表计算softmax，效率低。有些优化方法使用分层softmax的方法，利用二叉树计算。

![image-20210731111501965](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210731111501965.png)

将上下文词和目标词直接组成一个分类正例，然后从词汇表中随机抽取k-1个词组成分类反例。

原来每个样例训练V个分类器（假设词汇表有V个词），现在每个样例只需训练k个分类器即可。

##### Glove算法

设$X_{i,j}$表示单词i在单词j的上下文出现的次数。当定义的上下文具有对称性时，$X_{i,j}=X_{j,i}$.

优化目标：

![image-20210731112147210](C:\Users\xmh\AppData\Roaming\Typora\typora-user-images\image-20210731112147210.png)

前面的$f(X_{i,j})$表示一个加权项，当$X_{i,j}=0$时，$f(X_{i,j})$​=0。i表示上下文词，j表示目标词。



