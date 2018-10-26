# JS 类型

[原文链接](https://www.cnblogs.com/winter-cn/archive/2009/12/07/1618281.html)

Object.prototype.toString: 返回一个表示该对象的字符串。

可以通过`toString()` 来获取每个对象的类型。为了每个对象都能通过 `Object.prototype.toString()` 来检测，

需要以 `Function.prototype.call()` 或者 `Function.prototype.apply()` 的形式来调用，传递要检查的对象作为第一个参数，称为thisArg。

```javascript
var toString = Object.prototype.toString;

toString.call(new Date); // [object Date]
toString.call(new String); // [object String]
toString.call(Math); // [object Math]

//Since JavaScript 1.8.5
toString.call(undefined); // [object Undefined]
toString.call(null); // [object Null]
```

## typeof

它是用来获取类型的，按JavaScript标准的规定，typeof获取变量类型名称的字符串表示，

他可能得到的结果有6种：string、bool、number、undefined、object、function，而且JavaScript标准允许其实现者自定义一些对象的typeof值。

## instanceof

instanceof只能判断是否属于某一类型，无法得到类型

## Object.prototype.toString

因为Object.prototype.toString是取this对象属性，

所以只要用Object.prototype.toString.call或者Object.prototype.toString.apply就可以指定this对象，然后获取类型了。
