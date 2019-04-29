# ES6模块导入/导出

## export/import

> import导入的变量是只读的，不能修改其值(如果是对象，可以修改其属性值)。

```JavaScript
// moduleA.js
export var a = 5

// moduleB.js
import { a } from './moduleA'
a = 6 // 错误，不能修改a的值；若a = {}，a.first = 1是可以的。
```

#### 变量

```JavaScript
// moduleA.js
var a = 5
var b = 6
export { a, b }

// moduleB.js
import { a, b } from './moduleA'
```

#### 函数

```JavaScript
// moduleA.js
export function test () {}

// moduleB.js
import { test } from './moduleA'
```

## export default/import

> export default输出一个名为default的变量或方法，import时可以随意指定名字，且不需要使用大括号。

#### 变量

```JavaScript
// moduleA.js
var a = 2
export default a // a的值赋给变量default

// moduleB.js
import a from './moduleA'
```

#### 函数

```JavaScript
// moduleA.js
export default function () {}

// moduleB.js
import test from './moduleA'
```

## 导入一个模块后再将其导出

```JavaScript
// moduleB.js
import { test } from './moduleA'
export { test }

// 两条语句结合成一条；写成一条语句后，相当于moduleB对外转发了test这个接口，本身并没有导入test，所以moduleB不能直接使用test
export { test } from './moduleA'
```