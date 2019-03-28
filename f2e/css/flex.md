# Flex布局

## 属性

- ``order``：项目沿主轴方向上的排列顺序。数值越小越靠前
- ``flex-grow``
    - 默认值：``0``
- ``flex-shrink``
    - 默认值：``1``
- ``flex-basis``
    - 默认值：``auto``
    - ``flex-direction: row | row-reverse``时，``flex-basis和width``同时存在，``flex-basis``优先级高于``width``
    - 同理，``flex-direction: column | column-reverse``时，``flex-basis``优先级高于``height``
    - 当``flex-basis``和``width | height``，其中一个值为``   auto``时，非``auto``的优先级更高
- ``flex``
    - ``flex-grow, flex-shrink, flex-basis``三者的简写
    - 默认值：``0 1 auto``
    - 值为``none``时，等价于：``0 0 auto``
    - 值为``auto``时，等价于：``1 1 auto``
- ``flex-flow``
    - ``flex-direction, flex-wrap``的简写