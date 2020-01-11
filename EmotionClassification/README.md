# 中文情感分类项目
> 这个情感分类项目是研一上学期选的数据挖掘项目。 此次情感分类项目的任务是给定训练集（句子和情感标签），根据所学知识训练出一个模型，然后给定测试集，测试集的每一个样例是一句话，根据模型推断所属的情感。 <br>
> 与一般的情感分类的不同之处： 
>> * 这不是一个二分类的任务，是一个6分类的任务。
>> * 这不是一个简单的单分类任务，而也是一个多分类任务，即一句话可能对应多个标签

## [1. EmotionClassificationBasedNaiveBayes](https://github.com/zhongqiangwu960812/DeepLearningProjects/tree/master/EmotionClassification/EmotionClassificationBasedML)
> 任务分析：
>> 基于上面的要求，这次首先用机器学习的模型进行尝试，做一个基于机器学习的情感分类。参考了一个GitHub（Weibo-Sentiment-analysis-master）任务分为下面几部分进行：
>>> * 首先是数据预处理这块，训练集是句子，需要进行对每一个样例的句子进行切分，也就是分词处理，然后需要提取特征，转成词向量的形式
>>> * 标签部分，标签都是带有中括号的字符串类型，需要先转成列表，然后对里面多个标签的，给它拆分开，并且要转成数字
>>> * 数据预处理完之后，就可以建立模型，由于是多分类问题，此处建立多项式贝叶斯模型进行分类。

## [2. EmotionClassiBasedBERT](https://github.com/zhongqiangwu960812/DeepLearningProjects/tree/master/EmotionClassification/EmotionClassificationBasedDL)
> 任务分析：
>> 基于上面的要求，这次用深度学习的模型进行尝试，做一个基于深度学习的情感分类。因为机器学习的模型的效果比较差，可能对于词向量来说，获取无法体现出句子先后的逻辑特征，所以这里采用目前最先进的自然语言处理模型-BERT，参考github(BERT_Chinese_Classification-master)，采用谷歌提供的训练好的BERT模型的接口，然后fine-tune。关于BERT的原理，可以参考GitHub(BERT_tutorial)。B站上也有视频讲的挺好的。<br>
任务分为下面几部分进行：
>> * 关于BERT接口的使用，见下面的描述。这里关键是要进行数据集的准备，因为接口中的数据集要求的格式是.txt或者是.csv， 并且需要经过一些处理，所以这里主要是数据集的准备。
>> * 关于数据集准备，训练集和测试集都需要是.txt文件，所以进行处理，并且由于目前测试集还没出来，所以在总的数据集里面分出10%作为测试集。
>> * 划分完数据集之后，剩下的就交给BERT了，采用的环境是谷歌的colaboratory，GPU模式。
>> * 预测完之后，结果是通过softmax预测的每个类的概率，所以，还需要转成最后提交形式的结果，这块也需要自己处理，由于可能是一个样本对应了多个标签，所以进行最终结果选择的时候，要根据概率进行筛选，如果相差不大的，就可以都写上。
>
>PS： 发现.txt之后的数据集效果并不是很好，所以改成了.tsv数据集，参考的一篇[博客](https://blog.csdn.net/xavier_muse/article/details/95729133)，新写了一个processor

## [3. EmotioinClassificationBasedLSTM](https://github.com/zhongqiangwu960812/DeepLearningProjects/tree/master/EmotionClassification/EmotionClassificationBasedLSTM)
> 任务分析
>> 基于上面的要求，这次又尝试了新的一种模型，采用了
word2Vector+LSTM. 由于BERT是以字为单位的，并且如果数据集太小的话，对于BERT来说，很容易产生过拟合现象，所以尝试了word2Vector进行构建词嵌入矩阵，因为对于单个词来说，可能并不好把我相关性，这个词嵌入矩阵是以句子为单位的。 然后建立LSTM模型进行的训练和测试，这里最后一层是softmax输出的各个类的概率。
## 4. ReferencesGitHub
* [https://github.com/joliph/Classify-Text](https://github.com/joliph/Classify-Text)
* [https://github.com/lgz583/Weibo-Sentiment-analysis](https://github.com/lgz583/Weibo-Sentiment-analysis)
* [https://github.com/aespresso/a_journey_into_math_of_ml/tree/master/04_transformer_tutorial_2nd_part](https://github.com/aespresso/a_journey_into_math_of_ml/tree/master/04_transformer_tutorial_2nd_part) 这个很好，来源于B站的一个视频，讲BERT原理的
* [LSTM中文文本进行情感多分类](https://github.com/DLLXW/MultiClassify_LSTM_ForChinese)
* [ BERT的微调模型](https://github.com/google-research/bert)

## 5. 结果描述
> 基于上面的三种模型，对测试集进行测试，LSTM的表现较好一些，BERT的表现，可能由于数据量比较少的原因，效果次之，普通贝叶斯模型的效果比较差。但是具体查看分类的结果，即使LSTM的表现好，但是和人判断的也是相差很大，分析了一下数据集，这些数据不是全中文或者全英文的，而是中英日多种语言，并且各种符号，流行词等，导致即使人为分类都很难判别究竟是哪种情感。 所以对于这个任务来说，还有很大的研究和提升空间。最终提交结果的准确率，即使LSTM，才只能30%。
所以这里可以作为一个研究的话题，即情感分类，但是不是普通的只有中文或者英文，而是一个样本包含多种语言，并且各种网络流行词，表情符号等，并且可能对应多标签的这种情感分类，依然是一个很大的挑战。
## 6. 训练环境
> 上面模型的训练环境，朴素贝叶斯这个不需要什么很特别的环境，只需要普通的anaconda，然后有jupyter就可以。 但是BERT这个，普通的环境不行，TensorFlow至少1.11.0以上。 并且训练过程复杂，很容易出现显存溢出，我目前都不知道怎么解决，当时用的colaboratory， 运气好，顺利跑出了结果。 而LSTM这个，没有什么大要求，需要TensorFlow，word2vec等。 
