# 管理MySQL命令

```SQL
// 查看数据库
show databases;

// 创建数据库
create database test;

// 删除数据库
drop database test;

// 切换到指定数据库 
use test;

// 查看当前数据库下的表
show tables;

// 查看指定表的结构
desc user;

// 查看创建表的SQL语句
show create table user;

// 删除表
drop table user;

// 查看表创建时间
select * from information_schema.tables where table_schema=user order by create_time desc;

// 查看表中的所有字段
show full columns from user;

// 修改表
// 新增address列
alter table user add column address varchar(50) not null;

// 将列名address修改为addr
alter table user change column address addr varchar(50) not null;

// 删除address列
alter table user drop column address;

// 修改数据库字符集为utf8
alter database test default character set utf8;

// 修改表字符集为utf8
alter table user default character set utf8;

// 修改表的默认字符集和所有列的字符集
alter tabel user convert to character set utf8 collate utf8_general_cli;

// 修改指定字段字符集
alter table user change country country varchar(50) character set utf8 collate utf8_general_cli;
```