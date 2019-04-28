# DOM节点

## 节点类型

> 共12种。每种节点类型都有自己的nodeType，nodeName，nodeValue

* 元素节点：1
* 属性节点：2
* 文本节点：3
* 文档(document)节点：9

## 新建节点

```JavaScript
// 创建
createElement()
createTextNode()

// 添加到DOM(三种方式)
parentNode.appendChild(child)
parentNode.insertBefore(newNode, refrenceNode)
parentNode.replaceChild(newNode, oldNode)
```