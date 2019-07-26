一个 Redis 集群包含 16384 个哈希槽（hash slot）， 每个键都属于这 16384 个哈希槽的其中一个， 集群使用公式 CRC16(key) % 16384 来计算键 key 属于哪个槽， 其中 CRC16(key) 语句用于计算键 key 的 CRC16 校验和 。  
集群中的每个节点负责处理一部分哈希槽。  
服务器配置见：<https://juejin.im/entry/596343056fb9a06bc340ac15>  
Java代码引用  
- 直接基于jedis使用，见<https://blog.csdn.net/qiushisoftware/article/details/78819742>
- 通过spring来管理，见<https://blog.csdn.net/guying4875/article/details/79045345>
