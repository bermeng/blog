# Grid布局

## 作用在容器上

- ``grid-template-columns``

> 示例：

```css
grid-template-columns: [网格分隔线名字] 60px [网格分隔线名字] auto [网格分隔线名字] 100px // 三列
```

- ``grid-template-rows``

> 示例：

```css
grid-template-rows: [] 30% [] 100px [] 80px [] 40px // 四行
```

- ``grid-template-areas``：对网络划分区域
    - 子项使用``grid-area``归属到划分到指定的区域
- ``grid-template``
    - ``grid-template-columns, grid-template-rows, grid-template-areas``三者的简写
- 网格间隙
    - ``grid-column-gap``
    - ``grid-rows-gap``
    - 简写： ``grid-gap``，先row后column
***

- ``justify-items``：网格水平显示方式
- ``align-items``：网格垂直显示方式
- 简写：``place-items``，先align后justify

***

- ``justify-content``
- ``align-content``
- 简写：``place-content``

***

- ``grid-auto-rows``
- ``grid-auto-columns``
- ``grid-auto-flow``

***

- ``grid``

```css
grid-template-rows, grid-template-columns, grid-template-areas, grid-auto-rows, grid-auto-columns, grid-auto-flow的简写
```
- Grid布局中，``/``前面是rows相关属性，后面是columns相关属性

## 作用在子项上

- ``grid-column-start``
- ``grid-column-end``
- 简写：``grid-column``

***

- ``grid-row-start``
- ``grid-row-end``
- 简写：``grid-row``

***

- ``grid-area: <row-start> / <column-start> / <row-end> / <column-end>``

***

- ``justify-self``
- ``align-self``
- 简写：``place-self``