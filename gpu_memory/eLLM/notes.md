# eLLM: Elastic Memory Management Framework for  Efficient LLM Serving

## Conclusion

vLLM将KV Cache（PagedAttention）和其他（例如激活值，用静态内存管理）进行隔离管理--这里的方式指的是KV Cache用PagedAttention，有的用pytorch默认机制。这导致两者无法共享内存资源，造成 GPU 利用率下降（达 20%）。

weights全部驻留在HBM中（在线推理）

## Content

文中提出，LLM Serving System中需要管理的就是weight, activation, and KV cache这三类（针对推理）。

观察：
1、不同input length下weight, activation, and KV cache的比例不同
2、不同阶段（prefill，decode）下weight, activation, and KV cache的比例不同
3、不同模型架构下weight, activation, and KV cache的比例不同（例如因为KV Cache压缩）

eLLM和vLLM一样，是不会在memory oversubscription的情况下用统一内存（DRAM和SSD）来拓展GPU memory的。
