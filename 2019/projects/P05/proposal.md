---
layout: page
mathjax: true
permalink: /2019/projects/p05/proposal/
---

> 注意: 上方的内容不要删除

## 项目题目 
基于树模型的网易云音乐评论情感分析

### 成员
* 田也 312018028
* 商瑞红 3220180732
* 王若琳 3120181040
* 王孟岚 3120181037

### 问题描述

#### 1、问题背景分析

&ensp;&ensp;随着计算机和互联网技术的迅猛发展,网络己经成为人们获取信息的不可或缺的重要来源。自互联网进入时代以来,网民越来越习惯将网络作为自己表达观点、想法、态度的平台,而不只是被动的接受网站所发布的信息。由于大量的用户参与到信息的产生,网络信息的内容形式也变得越来越多样化,大量的具有个人观点性的内容充斥着网络。而这些观点对于电子商务、网络信息安全、网络舆情等方面具有非常重要的意义，因此情感分析（SA）的技术应运而生。

&ensp;&ensp;情感分析又称为倾向性分析和意见挖掘，它是对带有情感色彩的主观性文本进行分析、处理、归纳和推理的过程，其中情感分析还可以细分为情感极性（倾向）分析，情感程度分析，主客观分析等。

#### 2、问题描述
2.1 数据准备

&ensp;&ensp;现有方法大致可分为基于情感字典和基于机器学习的方法，这两种方法都或多或少有些不足。考虑到基于词典方法中，词与词之间独立缺乏相关性以及权重难以设定的不足，以及基于机器学习方法会碰到数据需求量大和数据不平衡的问题，我们提出基于树模型的无监督情感分类系统。

&ensp;&ensp;系统分为多个模块，其中音乐评论爬取模块为情感分析提供原始资源，每条音乐评论以字符串形式存在，多个音乐评论组合成列表。

2.2 模型建立

算法 FP-growth

输入：事务数据库D和最小支持度阈值minσ。

输出：D所对应的FP-tree。

方法：FP-tree构造

1.	扫描事务库D，获得D中所包含的全部频繁项集1F，及它们各自的支持度。对1F中的频繁项按其支持度降序排序得到L。

2.	创建FP-tree的根结点T，以“null”标记。再次扫描事务库。

3.	对于D中每个事务，将其中的频繁项选出并按L中的次序排序。设排序后的频繁项表为[p|P]，其中p是第一个频繁项，而P是剩余的频繁项。

4.	调用insert_tree([p|P],T)。insert_tree([p|P],T)过程执行情况如下：

5.	如果T有子女N使N.item_name=p.item_name，则N 的计数增加1；

6.	否则创建一个新结点N，将其计数设置为1，链接到它的父结点T，并且通过node_link将其链接到具有相同item_name的结点。

7.	如果P非空，递归地调用insert_tree(P，N)。

8.	结束

2.3 预期的结果

&ensp;&ensp;我们设计的系统分别在自行爬取的音乐数据集和网上已有数据集进行实验，并根据不同的分类方法对其进行分类准确性计算，分类发放主要有：SVM, Navie bayes，线性回归，语义词典结合以及我们设计的分类方法。实验表明所提出的方法准确率最接近机器学习的方法，如果结合情感词典后，相信准确率还会有提升。

### 项目评估

+ 该方法比传统的基于语义词典的方法在准确率上有较大的提升；

+ 方法考虑到了词语与词语之间的关联性，权重可靠，相比与机器学习的方法，我们的方法更为显性；

+ 机器学习方法需要大量的平衡的标签数据，比较大的计算资源，速度较慢，我们的方法实现速度快，方法简单。

### 项目分工

* 田也 312018028 &ensp; 数据获取、系统设计实现 文档编写
* 商瑞红 3220180732 &ensp; 算法设计与实现 
* 王若琳 3120181040 &ensp; 预测结果分析 文档编写
* 王孟岚 3120181037 &ensp; 数据分析、数据处理

