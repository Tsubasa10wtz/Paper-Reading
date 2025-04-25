# GMT: GPU Orchestrated Memory Tiering for the Big  Data Era

## 一句话介绍这篇文章

GPU控制GPU、CPU、SSD三级的数据通路，设计了一种数据放置方法（可以类比Blaze这篇文章）。

## 我们需要关注哪些问题

1、怎么实现GPU控制数据通路，我们后面可能要做。

GMT生命周期都在GPU中控制，

RAPIDS cuDF是什么

2、GPU怎么获得数据访问trace？

GMT-random，自设计baseline，说明智能决策是有用的