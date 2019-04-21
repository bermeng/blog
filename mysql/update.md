# 修改操作

## 插入

```SQL
// VALUES中的值顺序必须和表中的字段顺序一致
INSERT INTO user(id, name, gender, country, address) VALUES(23, 'James', 'M', 'China', 'Beijing');
```

## 更新

```SQL
// 更新指定记录
UPDATE user set name='Justin' WHERE id=23;
```

## 删除

```SQL
// 删除指定记录
DELETE FROM user WHERE id=23;

// 删除整个表
DELETE FROM user;
```