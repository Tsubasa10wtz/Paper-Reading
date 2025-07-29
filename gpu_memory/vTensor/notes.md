# vTensor: Flexible Virtual Tensor Management for Efficient LLM Serving

## 内存灵活性（Memory Flexibility）

内存灵活性指的是 **系统能够根据需要动态地分配、扩展、释放 GPU 内存资源**，而不是事先一次性静态预分配所有资源。

### vLLM 的问题：

- 使用 **静态预分配**内存；
- 一旦为 KV cache 分配内存，其他任务（如激活值、模型副本）就无法使用这部分内存；
- 内存使用率低，碎片严重；
- 多实例部署时冲突大。

### vTensor 的改进：

- 支持 **按需分配**（vAlloc/pAlloc）；
- 可 **动态扩展** KV cache（token 增加时自动扩展）；
- 可 **提前释放**无效数据（lazy 回收）；
- 同一个物理块可以被多个 vTensor 复用（prefix cache）；

### 好处：

- 避免内存浪费；
- 支持更多并发请求或大模型；
- 可与其他任务（如训练、微调、模型并行）共用资源。

------

## 二、计算灵活性（Computation Flexibility）

### 定义：

计算灵活性指的是 **系统可以自由选择和使用最优的计算内核（如 Tensor Core 加速），而不受内存管理机制限制**。

### vLLM 的问题：

- 计算内核与页表管理逻辑**紧耦合**；
- Attention kernel 需要专门为分页设计，不容易替换；
- 只能使用 CUDA Core，无法使用 Tensor Core；
- 新特性（如 prefix cache）难以接入，开发维护成本高。

### vTensor 的改进：

- 将 memory defragmentation 完全 **解耦**出计算逻辑；
- 计算 kernel 接收到的 vTensor 与普通 CUDA tensor 无差异；
- 可以复用已有高效内核（如 FlashAttention）；
- 支持 GPU Tensor Core，加速 GQA、MQA 等高算力需求结构。
