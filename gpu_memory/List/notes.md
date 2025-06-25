## Paper list for gpu memory management

### Purpose
这个文档的目的是整理一些关于这个领域粗读的paper列表，可能和部分精读的论文重合。

### Background
常见方法

1.multi-GPU parallelism 

2.data offloading to the host memory

3.intermediate result recomputation

4.memory compression and quantization

### List

#### A Framework for Memory Oversubscription Management in Graphics Processing Units(ASPLOS’19)
...

#### DeepUM: Tensor Migration and Prefetching in Unified Memory(ASPLOS ’23)

用户态（Pytorch）和内核态协同，通过对page fault建模（类似之前的markov预取的方法），预测DNN任务中的访问关联（访问模式）。用访问模式建模执行预取、替换。来优化UVM（*在UVM+Pytorch上做优化，并非像GMT一样绕过UVM*）



#### Enabling Large Dynamic Neural Network Training with Learning-based Memory Management(HPCA'24)

DyNN Training虽然动态选择模块激活，但是本质上访问模式还是几种简单访问模式的组合（insight）。所以可以通过Learning for Learning的的方式预测并进行预取。



#### Understanding Oversubscribed Memory Management for Deep Learning Training(EuroMLSys'25)

PCA+UVM可以得到很好的效果，可以缓解oversubscription的问题

#### BaM

#### GMT

#### G10(MICRO'23)
关注到forward和backward特性，可以估计知道所有张量的inactivate时间






