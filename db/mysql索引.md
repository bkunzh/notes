# 索引类型
## 1. 普通索引
由关键字KEY或INDEX定义的索引。应该为那些最经常出现在查询条件(WHERE column = ...)或排序条件(ORDER BY column)中的数据列创建索引
## 2. 唯一索引
索引列的值必须唯一，但允许有空值
## 3. 主键索引
是一种特殊的唯一索引，一个表只能有一个主键，不允许有空值
## 4. 组合索引
指多个字段上创建的索引，只有在查询条件中使用了创建索引时的第一个字段，索引才会被使用 
ALTER TABLE `table` ADD INDEX name_city_age (name,city,age); 
## 5. 前缀索引
在较长的字段建立索引，可以建立前缀索引。如果要模糊匹配只有右边模糊匹配才会用到索引。
alter table `table` add index idx2 (msg(15));
## 6. 全文索引
仅支持InnoDB和MyISAM表，并且只能包含CHAR，VARCHAR和TEXT列。索引总是在整个列上进行；不支持列前缀索引

# 索引方式
## BTree
InnoDB、MyISAM只支持BTree方式
## Hash
Hash 索引仅仅能满足"=","IN"和"<=>"查询，不能使用范围查询