## 1. redis安装

## 2. redis启动、关闭

## 3. redis配置
### 3.1 redis持久化配置
#### 1. RDB持久化方式

RDB持久化方式会在一个特定的间隔保存那个时间点的一个数据快照。

save N M

表示在N秒之内，redis至少发生M次修改则redis抓快照到磁盘

默认配置如下，如果1分钟至少发生10000次修改就备份快照或如果5分钟至少发生10次修改或如果15分钟至少发生1次修改，就备份快照

```
save 900 1
save 300 10
save 60 10000
```

RDB方式速度较快，但容易丢失数据

#### 2. AOF持久化方式

设置appendonly yes开启aof方式，redis执行修改数据的命令，会把它添加到appendonly.aof文件中，当redis重启时，将会读取AOF文件进行“重放”以恢复到redis关闭前的最后时刻。

可以设置每秒或者每修改一次刷新AOF。

appendfsync everysec 表示每秒刷新修改到AOF文件，appendfsync always 太慢

AOF 影响性能，不容易丢失数据

## 4. redis数据类型
- 1)字符串
- 2)哈希
- 3)列表
- 4)Set
- 5)SortedSet

## 5. redis操作
1) key
- keys *
- type key

2) 字符串
- set、get、del
- setnx
- incr、incrby
- decr、decrby
-append
3) 哈希
- hset、hget
- hmset、hmget、hgetall、hdel
- hincrby
- hexists
 hlen
- hkeys、hvals

格式：
- hmset key hashkey1 hashvalue1 haskey2 hashvalue2
- hmget key hashkey1 hashkey2
 hdel key hashkey1 hashkey2
 del key
 hincrby key hashkey1 xx

4) 列表
- lpush、rpush
- lrange
- lpop、rpop
- llen
- lpushx、rpushx
(xxPUSHX key value将值 value 插入到列表 key 的表尾，当且仅当 key 存在并且是一个列表)
- lrem

- lset、linsert
 - rpoplpush （备份队列、旋转）

举例：
- lpush key a b c
- lpush key 1 2 3
- lrange key 0 5 (or lrange key 0 -1)
> (结果：3 2 1 c b a)
- Rpush key a b c 
- Rpush 1 2 3
- lrange key 0 5
>(结果：a b c 1 2 3)

5) Set 集合

6) SortedSet 有序集合

## 6. redis不同数据类型在哪些场景使用
见<https://github.com/doocs/advanced-java/blob/master/docs/high-concurrency/redis-data-types.md>


更多命令用法查文档
- <http://doc.redisfans.com/>
- [google搜索](https://www.google.com.hk/search?lr=lang_zh-CN&newwindow=1&tbs=lr%3Alang_1zh-CN&source=hp&ei=V3ONXL2yN83p-QbkqZiICA&q=redis+%E6%96%87%E6%A1%A3&btnK=Google+Search&oq=redis+%E6%96%87%E6%A1%A3&gs_l=psy-ab.3...619.3487..3691...1.0..0.192.1171.14j1......0....1..gws-wiz.....6..35i39j0i67j0i131j0i10j0j0i20i263j0i203j0i22i30.-okZjDVkZBU)

## 99. 参考
- 慕课网redis教程
- 
