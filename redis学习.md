## 1. redis安装

## 2. redis启动、关闭

## 3. redis配置

## 4. redis数据类型
- 1)字符串
- 2)哈希
- 3)列表
- 4)Set
- 5)SortedSet

## 5. redis不同数据的操作
1) 字符串
 set、get、del
 setnx
 incr、incrby
 decr、decrby
 append
2) 哈希
 hset、hget
hmset、hmget、hgetall、hdel
hincrby
hexists
hlen
hkeys、hvals

格式：
hmset key hashkey1 hashvalue1 haskey2 hashvalue2
hmget key hashkey1 hashkey2
hdel key hashkey1 hashkey2
del key
hincrby key hashkey1 xx

3) 列表
lpush、rpush
lrange
lpop、rpop
llen
lpushx、rpushx
(RPUSHX key value将值 value 插入到列表 key 的表尾，当且仅当 key 存在并且是一个列表)
lrem
 
lset、linsert
rpoplpush （备份队列）




举例：
lpush key a b c
lpush key 1 2 3
lrange key 0 5 (or lrange key 0 -1)
(结果：3 2 1 c b a)
Rpush key a b c 
Rpush 1 2 3
lrange key 0 5
(结果：a b c 1 2 3)

4) Set 集合

5) SortedSet 有序集合

 
更多命令用法查文档
- <http://doc.redisfans.com/>

## 99. 参考
- 慕课网redis教程
- 
