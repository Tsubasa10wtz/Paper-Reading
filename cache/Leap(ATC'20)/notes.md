# Effectively Prefetching Remote Memory with Leap

## 解决的问题

RDMA读取带来的延迟（不是RDMA本身带来的，而是一套完整的关键路径）


## 有疑问的点

2.2节的slower memory指的是什么？

2.3节中Prefetch Cache Eviction小节，Unnecessary pages waiting for eviction in-memory leads to extra scanning time. This extra wait-time due to lazy cache eviction policy adds to the overall latency, especially in a high memory pressure scenario. 这个有多少实际收益，怎么量化。

