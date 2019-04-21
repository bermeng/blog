# 实用SQL语句

## 插入/替换

```SQL
// 如果id=1记录不存在，插入；否则，将id=1记录删除后再进行插入

REPLACE INTO user (id, name, gender, country) VALUES (1, 'John', 'M', 'China');
```

## 插入/更新

```SQL
// 如果id=1记录不存在，插入；否则，更新id=1的记录

INSERT INTO user (id, name, gender, country) VALUES (1, 'John', 'M', 'China') ON DUPLICATE KEY UPDATE name='John', gender='M', score='China';
```

## 插入/忽略

```SQL
// 如果id=1记录不存在，插入；若存在，不执行任何操作

INSERT IGNORE INTO user (id, name, gender, country) VALUES (1, 'John', 'M', 'China');
```

## 对表进行快照

```SQL
// 对country='China'的记录进行快照，并存储到新表user_of_China中

CREATE TABLE user_of_China SELECT * FROM user WHERE country='China';
```

## 将查询结果集写入到表中

```SQL
// 创建一个统计各国家用户的平均年龄表

CREATE TABLE user_average_age (
    id BIGINT NOT NULL AUTO_INCREMENT,
    country VARCHAR(50) NOT NULL,
    average_age INT NOT NULL,
    PRIMARY KEY (id)
);

// 将查询结果写入创建的表中

INSERT INTO user_average_age SELECT country, AVG(age) FROM user GROUP BY country;
```