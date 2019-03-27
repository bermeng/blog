# Basis

## 数据类型

1. bool
2. 整型
3. string
4. 派生类型
    - pointer
    - array
    - struct
    - channel
    - 函数类型
    - slice
    - interface
    - map 

## :=

- 引入``:=``赋值操作符：只可用在函数体内
- 声明的一个局部变量，必须被使用

## iota

- ``iota``：特殊常量。``const``关键字出现时其被重置为0，然后在下一个``const``出现前，每出现一次``iota``，自动递增。

```text
const(
    a = iota
    b = iota
    c = iota
)
```

> 这里``a = 0; b = 1; c = 2``

## for循环

1. ``for a := 0; a < 10; a++ { }``
2. ``for a < 5 { }``
3. ``for { }``
> ``range``关键字：用在for循环中遍历array、slice（切片）、channel、map

## slice（切片）

- 定义
    - ``s1 := [] int {1, 2, 3}``
    - ``s2 := make([]int, 3, 5)`` //3位长度；5为容量

## nil

> 空值语义
- go中，任何类型未初始化时都对应一个空值
    - bool：false
    - 整型：0
    - string：""
    - 派生类型：nil