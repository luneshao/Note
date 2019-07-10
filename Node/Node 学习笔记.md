# Node 学习笔记

## assert断言

### 1. assert.AssertionError 类

`Error` 的子类，表明断言的失败。`assert` 模块抛出的错误都是 `AssertionError` 这个类的实例。

### 2. 严格模式

当使用严格模式时，`assert` 中的任何函数都将使用严格函数模式中使用的相等性。即 assert.deepEqual() 将与 assert.deepStrictEqual() 一样效果。使用方式如下：

```js
  const assert = require('assert').strict;
```

note：严格模式下当抛出错误时，将会明确存在差异的位置。

### 3.assert(value[, message])

* value：判断 value 是否为 `true`
* message `<string> | <Error>`：自定义输出的错误文本和错误类型
