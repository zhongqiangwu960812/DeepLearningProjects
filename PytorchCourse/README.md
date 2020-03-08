# PyTorch course

Pytorch官方文档：[https://pytorch.org/docs/stable/torch.html?](https://pytorch.org/docs/stable/torch.html?)

这是B站上的一个课程，感觉老师讲的不错，这里主要是把学习过程中的笔记进行分享。在学习这门课程之前，需要先搭建Pytorch环境：
[Pytorch入门+实战系列一：Windows下的Pytorch环境手把手搭建](https://blog.csdn.net/wuzhongqiang/article/details/104503860)
<br><br>OK, Let's go!

### 1. 第一课
>今天是课程的第一节课，在这一节课中，我们会学习Pytorch的基本理论知识并进行演示，不是面面俱到，只是点到为止（要善于查官方文档）。 然后我们会先用numpy搭建一个简单的两层神经网络进行热身（这里会带你领略前向传播，反向传播的细节计算），之后，我们会用Pytorch一步一步的替代numpy里面的步骤，最后形成一个Pytorch版本的两层神经网络，在这个过程中，你会亲身体会到Pytorch的强大。 完成上面的任务之后，就应该学会搭建简单的神经网络了，那么就小试牛刀一下，搭建一个神经网络并教会他玩一个简单的游戏！<br><br>
笔记链接：[Pytorch入门+实战系列二：Pytorch基础理论和简单的神经网络实现](https://blog.csdn.net/wuzhongqiang/article/details/104506659)

### 2.第二课
> 今天是课程的第二节课，上次已经学习了Pytorch的基本知识，这节课开始就是用Pytorch在各个领域的实战，首先从nlp的词向量开始， 这节课首先会学习词向量的基本概念，然后学习Pytorch的dataset和DataLoader， 学习Pytorch定义模型(Module)和常见的Pytorch操作(bmm,logsigmoid)，学习Pytorch的模型保存和读取。 最后我们用Skip-gram的模型训练一个词向量。这节课主要是通过实战的部分学习Pytorch，这个实战尽可能复现一篇论文中的训练词向量的方法，实现skip-gram模型，并且使用论文中的noice contrastive sampling的目标函数，所以学习之前，也得熟悉一下这篇论文。
[Distributed Representations of Words and Phrases and their Compositionality](http://papers.nips.cc/paper/5021-distributed-representations-of-words-and-phrases-and-their-compositionality.pdf)<br><br>
笔记链接：[Pytorch入门+实战系列三：Pytorch与词向量](https://blog.csdn.net/wuzhongqiang/article/details/104730280)

