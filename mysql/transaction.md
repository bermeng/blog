# 数据库事务

## 事务ACID特性

* Atomic，原子性
* Consitent，一致性
* Isolation，隔离性
* Duration，持久性

## 事务操作

```SQL
BEGIN;
...     // sql语句
COMMIT;
```

## 隔离级别

> 对于并发事务，当操作同一条数据记录时有可能会造成数据不一致问题，包括脏读、不可重复读、幻读。为避免此类问题，SQL标准定义了四种隔离级别

| 级别 | 脏读 | 不可重复读 | 幻读 |
| --- | --- | :---: | --- |
| Read Uncommitted | Yes | Yes | Yes |
| Read committed | | Yes | Yes |
| Repeatable Read | | | Yes |
| Serializable | | | | |

### Read Uncommitted

> 以下是两个并发事务的执行；出现脏读情况

| 事务 A | 事务 B |
| :---: | :---: |
|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|
|BEGIN;|BEGIN;|
|UPDATE students SET name = 'Bob' WHERE id = 1;||
||SELECT * FROM students WHERE id = 1;|
|ROLLBACK;||
||SELECT * FROM students WHERE id = 1;|
||COMMIT;|

### Read Commited

> 以下是两个并发事务的执行；出现不可重复读情况

| 事务 A | 事务 B |
| :---: | :---: |
|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|
|BEGIN;|BEGIN;|
||SELECT * FROM students WHERE id = 1;|
|UPDATE students SET name = 'Bob' WHERE id = 1;||
|COMMIT;||
||SELECT * FROM students WHERE id = 1;|
||COMMIT;|

### Repeatable Read

> 以下是两个并发事务的执行；出现幻读情况

| 事务 A | 事务 B |
| :---: | :---: |
|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;|
|BEGIN;|BEGIN;|
||SELECT * FROM students WHERE id = 5;|
|INSERT INTO students(id, name) VALUES(5, 'John') 
|COMMIT;||
||SELECT * FROM students WHERE id = 5;|
||	UPDATE students SET name = 'James' WHERE id = 5;|
||SELECT * FROM students WHERE id = 5;|
||COMMIT;|

### Serializable

> 所有事务依次执行，即串行。