# 中文情感分类项目
> 这个情感分类项目是研一上学期选的数据挖掘项目。 此次情感分类项目的任务是给定训练集（句子和情感标签），根据所学知识训练出一个模型，然后给定测试集，测试集的每一个样例是一句话，根据模型推断所属的情感。 <br>
> 与一般的情感分类的不同之处： 
>> * 这不是一个二分类的任务，是一个6分类的任务。
>> * 这不是一个简单的单分类任务，而也是一个多分类任务，即一句话可能对应多个标签

## [1. EmotionClassificationBasedML](https://github.com/zhongqiangwu960812/DeepLearningProjects/tree/master/EmotionClassification/EmotionClassificationBasedML)
> 任务分析：
>> 基于上面的要求，这次首先用机器学习的模型进行尝试，做一个基于机器学习的情感分类。参考了一个GitHub（Weibo-Sentiment-analysis-master）任务分为下面几部分进行：
>>> * 首先是数据预处理这块，训练集是句子，需要进行对每一个样例的句子进行切分，也就是分词处理，然后需要提取特征，转成词向量的形式
>>> * 标签部分，标签都是带有中括号的字符串类型，需要先转成列表，然后对里面多个标签的，给它拆分开，并且要转成数字
>>> * 数据预处理完之后，就可以建立模型，由于是多分类问题，此处建立多项式贝叶斯模型进行分类。

## [2. EmotionClassiBasedDL](https://github.com/zhongqiangwu960812/DeepLearningProjects/tree/master/EmotionClassification/EmotionClassificationBasedDL)
> 任务分析：
>> 基于上面的要求，这次用深度学习的模型进行尝试，做一个基于深度学习的情感分类。因为机器学习的模型的效果比较差，可能对于词向量来说，获取无法体现出句子先后的逻辑特征，所以这里采用目前最先进的自然语言处理模型-BERT，参考github(BERT_Chinese_Classification-master)，采用谷歌提供的训练好的BERT模型的接口，然后fine-tune。关于BERT的原理，可以参考GitHub(BERT_tutorial)。B站上也有视频讲的挺好的。<br>
任务分为下面几部分进行：
>> * 关于BERT接口的使用，见下面的描述。这里关键是要进行数据集的准备，因为接口中的数据集要求的格式是.txt或者是.csv， 并且需要经过一些处理，所以这里主要是数据集的准备。
>> * 关于数据集准备，训练集和测试集都需要是.txt文件，所以进行处理，并且由于目前测试集还没出来，所以在总的数据集里面分出10%作为测试集。
>> * 划分完数据集之后，剩下的就交给BERT了，采用的环境是谷歌的colaboratory，GPU模式。
>> * 预测完之后，结果是通过softmax预测的每个类的概率，所以，还需要转成最后提交形式的结果，这块也需要自己处理，由于可能是一个样本对应了多个标签，所以进行最终结果选择的时候，要根据概率进行筛选，如果相差不大的，就可以都写上。
>
>PS： 发现.txt之后的数据集效果并不是很好，所以改成了.tsv数据集，参考的一篇[博客](https://blog.csdn.net/xavier_muse/article/details/95729133)，新写了一个processor

## 3. ReferencesGitHub
* [https://github.com/joliph/Classify-Text](https://github.com/joliph/Classify-Text)
* [https://github.com/lgz583/Weibo-Sentiment-analysis](https://github.com/lgz583/Weibo-Sentiment-analysis)
* [https://github.com/aespresso/a_journey_into_math_of_ml/tree/master/04_transformer_tutorial_2nd_part](https://github.com/aespresso/a_journey_into_math_of_ml/tree/master/04_transformer_tutorial_2nd_part) 这个很好，来源于B站的一个视频，讲BERT原理的
* [ BERT的微调模型](https://github.com/google-research/bert)
