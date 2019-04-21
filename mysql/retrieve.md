# 查询操作

## 基本查询

```SQL
SELECT * FROM user;
```

## 条件查询

```SQL
SELECT * FROM user WHERE gender='M';
```

## 投影查询
```SQL
SELECT id, name, country FROM user;
```

## 排序查询(默认ASC)

```SQL
SELECT * FROM user ORDER BY age DESC;
```

## 分页查询

```SQL
// LIMIT = pageSize
// OFFSET = pageSize * (pageIndex - 1)
SELECT id, name, country FROM user ORDER BY age DESC LIMIT 3 OFFSET 0;
```

## 聚合查询

### 聚合函数

| 聚合函数 | 说明 |
| --- | --- |
| COUNT | 计算总记录数 |
| SUM | 某一列的和， 数值类型 |
| AVG | 某一列的平均值， 数值类型 |
| MAX | 某一列的最大值 |
| MIN | 某一列的最小值 |

### 示例

```SQL
SELECT COUNT(*) male FROM user WHERE gender='M';
```

## 多表查询

```SQL
SELECT
    s.id sid,
    s.name sname,
    c.id cid,
    c.name cname
FROM students s, classes s
WHERE s.gender='M' AND s.class_id=c.id;
```
## 连接查询

```SQL
// 内连接(两表的交集)
SELECT s.id, s.name sname, s.class_id c.name cname
FROM students s
INNER JOIN classes c
ON s.class_id=c.id;

// 左连接(左表数据全部返回, 即使右表无对应数据)

SELECT s.id, s.name sname, s.class_id c.name cname
FROM students s
LEFT OUTER JOIN classes c
ON s.class_id=c.id;

// 右连接(右表数据全部返回，即使左表无对应数据)
SELECT s.id, s.name sname, s.class_id c.name cname
FROM students s
RIGHT OUTER JOIN classes c
ON s.class_id=c.id;
```