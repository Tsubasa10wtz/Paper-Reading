# eLLM: Elastic Memory Management Framework for  Efficient LLM Serving

## 一句话

vLLM将KV Cache（PagedAttention）和其他（例如激活值，用静态内存管理）进行隔离管理--这里的方式指的是有的用PagedAttention，有的用pytorch默认机制。这导致两者无法共享内存资源，造成 GPU 利用率下降（达 20%）。