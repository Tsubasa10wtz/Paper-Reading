# NetLLM: Adapting Large Language Models for Networking

## 问题

传统的深度学习解决网络的预测和优化问题不能做到“one model for all tasks”，但是大模型可以凭借预训练和处理网络问题中多模态数据的能力来更有效的学习特定领域的知识。

注意：本文主要关注的点是解决优化网络问题带来的庞大工程量？

（可能怎么去提大模型应用到网络预测和优化的问题？）






## 解决方案


## 精读
### 1 Introduction
#### 1.1 The Main Roadmap so far（学习行文）
攻击的是深度学习需要手动调节参数以适应不同的网络负载的点，所以先从传统的手动控制规则的算法讲起。

然后讲深度神经网络虽然一定程度上解决了手动控制算法的弊端（工程量），但是存在弊端：

1、工程开销：为不同任务匹配不同模型。

2、普遍性：强调的是适应性。不能适应各种不同的情况（网络波动），本质原因是没有在特殊的数据分布/环境上进行训练。

#### 1.2 New Opportunities and Challenges

想法自然：因为有已经延伸到其他领域，是否可以同样用到网络优化领域。

can we embrace the era of LLMs and adapt LLMs to solve various networking tasks efficiently and effectively?

然后提出三个挑战，很常规：

1、输入数据的格式差异大

2、生成速度慢（针对推理）

3、适应成本高（针对微调）

`感觉如果我们来做也是相同的挑战？`


#### 本文提到的三个和网络相关的用例
（可能阐述为什么使用大模型可能改进这三个用例，有什么特别的点）

