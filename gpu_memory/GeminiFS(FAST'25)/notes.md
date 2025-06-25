# GeminiFS: A Companion File System for GPUs

## 思考
和BaM-GMT的不同点在哪里。

### 为什么需要在BaM上搭建一个文件系统。

BaM最大的问题--没有和application完全解耦，cuda实现application，需要在GPU侧手动注册application需要的所有元数据信息。
如果像GeminiFS一样做一个GPU侧文件系统，就可以直接直接在GPU侧自动注册元数据信息，做到真正的对上层应用透明。


GPU对NVMe发起直接控制失去文件系统功能的本质--文件系统是CPU-centric管理的？