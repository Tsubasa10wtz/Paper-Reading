# Fast Vector Query Processing for Large Datasets Beyond GPU Memory  with Reordered Pipelining

提出RUMMY，在处据规模超出GPU内存容量的情况下加速大规模向量查询

## Details

As CUDA unified memory is unaware of vector queries, this solution would incur massive GPU memory page faults, leading to low performance.
UVM不行的本质不知道上层应用是向量查询。

Dynamic Kernel Padding with Cluster Balancing的目的是为了让GPU的SM的计算性能跑满不浪费，Grouping是为了解决计算和传输的overlapping。

## Points

Vector databases [16–20] can provide persistence and long-term memory for LLMs.
实际上是把RAG升华了？不是为了检索知识，也是为了给大模型提供持久化记忆。

