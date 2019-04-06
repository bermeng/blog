# 类数组对象

## 特征

- 数字索引
- length属性，且length为正整数

## 示例

```JavaScript
var o = {0: 'a', 1: 'b', length: 2}
```

## 类数组对象转换为数组

```JavaScript
// 方法一
[].slice.call()

// 方法二
Array.from()
```