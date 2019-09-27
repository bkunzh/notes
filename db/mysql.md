# 常用
## 函数
### rand(); 从数据表随意取一条数据; 按任意顺序排列; 
SELECT rand(), t.* from innodb_table t  ORDER BY id desc;  
SELECT * from innodb_table t  ORDER BY rand() limit 1;  
SELECT * from innodb_table t  ORDER BY rand();  

## 常用sql
### show表结构，可以看到表结构、数据库引擎
show create table 0readme2
### 显示索引信息
show index from demo
### 删除临时表
drop temporary table new_table ;
### 命令行中结尾符
- ;/\g 横行输出
- \G 横向的表结构会转为使用纵向表结构输出，利于阅读

## 操作符
### `=`与`<=>`
`<=>`NULL-safe equal to operator  
当操作符右边的值不是null时，两个操作符一样。  
当操作符右边的值时null时，`=null`结果始终返回null；而`null<=>null`返回1.  
 `<=>null`等价于is null
```
select null is null;  //1
SELECT 1 <=> 1, NULL <=> NULL, 1 <=> NULL;
        -> 1, 1, 0
SELECT 1 = 1, NULL = NULL, 1 = NULL;
        -> 1, NULL, NULL
```
### not 非


## 临时表
临时表是一张表，用来临时保存一些数据，只对创建该临时表的用户可见，当会话结束时，MySQL自动删除临时表
CREATE TEMPORARY TABLE  tbl_name(……);   
用户可以创建一个和已有的普通表名字相同的临时表，在这种情况下，该用户只能看到临时表而看不见同名的普通表；  
添加IF NOT EXISTS选项:create table if not exists PLAYERS(id int(5),name varchar(20));  
只对创建该临时表的用户可见；当会话结束时，MySQL自动删除临时表。
临时表主要用于对大数据量的表上作一个子集，提高查询效率。
### 用已有表的部分数据创建一个临时表。可以指定ENGINE=MEMORY，不指定是默认引擎，即InnoDB
create temporary table demo_t (id int, name varchar(50)) ENGINE=MEMORY 
  select * from demo WHERE sex = 'woman';

## 根据已有的表来创建新表
### 复制已有表的表结构，包括非空约束、索引
create table new_table like demo;
### 把一个表的表内容复制过去
insert into new_table SELECT * from demo;
### 创建表，并把旧表的内容复制过去，但索引、主键约束不会不过复制。推荐使用以上两个来代替
CREATE table new_table2 SELECT * from demo;