# MOONCAKE: Trading More Storage for Less Computation A KVCache-centric Architecture for Serving LLM Chatbot

```
请求到来 →
→ 查找是否已有Prefix缓存（KVCache） →
   如果有：
     - 从本地或远程DRAM中加载缓存 → 拷贝到GPU显存 → 解码
   如果没有：
     - Prefill阶段重新计算 → 生成新的KVCache → 存入缓存池