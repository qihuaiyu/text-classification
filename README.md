# 新闻上的文本分类：机器学习大乱斗

完整文档转到知乎专栏： https://zhuanlan.zhihu.com/p/26729228

### 目标

1. 从头开始实践中文短文本分类，记录一下实验流程与遇到的坑
2. 运用多种机器学习（深度学习 + 传统机器学习）方法比较短文本分类处理过程与结果差别

### 工具

深度学习：keras

传统机器学习：sklearn

参与比较的机器学习方法

1. CNN 、 CNN + word2vec
2. LSTM 、 LSTM + word2vec
3. MLP（多层感知机）
4. 朴素贝叶斯
5. KNN
6. SVM
7. SVM + word2vec 、SVM + doc2vec
第 1-3 组属于深度学习方法，第 4-6 组属于传统机器学习方法，第 7 组算是种深度与传统合作的方法，画风清奇，拿来试试看看效果


### 数据集

搜狗实验室 搜狐新闻数据 下载地址：http://www.sogou.com/labs/resource/cs.php


### 先上结果

![](https://git.oschina.net/uploads/images/2017/0724/105517_0327b8f1_1452419.png "")


### 实验结论

1. 引入预训练的 word2vec 模型会给训练带来好处，具体来说：（1）间接引入外部训练数据，防止过拟合；（2）减少需要训练的参数个数，提高训练效率
2. LSTM 需要训练的参数个数远小于 CNN，但训练时间大于 CNN。CNN 在分类问题的表现上一直很好，无论是图像还是文本；而想让 LSTM 优势得到发挥，首先让训练数据量得到保证
3. 将单词在 word2vec 中的词向量加和求平均获得整个句子的语义向量的方法看似 naive 有时真挺奏效，当然仅限于短句子，长度 100 以内应该可以
4. 机器学习方法万千，具体选择用什么样的方法还是要取决于数据集的规模以及问题本身的复杂度，对于复杂程度一般的问题，看似简单的方法有可能是坠吼地

