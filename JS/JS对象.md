# JS对象

[原文链接](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/Objects/Object_prototypes)<br>

## OOP 面向对象

JavaScript 用一种称为`构建函数`的特殊函数来定义对象和它们的特征。构建函数非常有用，因为很多情况下您不知道实际需要多少个对象（实例）。

构建函数提供了创建您所需对象（实例）的有效方法，将对象的数据和特征函数按需联结至相应对象。
	
### 1.理解原型对象

* 浏览器首先检查，person1 对象是否具有可用的 valueOf() 方法。

* 如果没有，则浏览器检查 person1 对象的原型对象（即 Person）是否具有可用的 valueof() 方法。

* 如果也没有，则浏览器检查 Person() 构造器的原型对象（即 Object）是否具有可用的 valueOf() 方法。Object 具有这个方法，于是该方法被调用。
	
### 2.prototype 属性：继承成员被定义的地方

继承的属性和方法是定义在 prototype 属性之上的（你可以称之为子命名空间 (sub namespace) ）——那些以 Object.prototype. 开头的属性，而非仅仅
	
  以Object. 开头的属性。
	
### 3.create()

  create() 实际做的是从指定原型对象创建一个新的对象。
	
### 4.constructor 属性

  每个对象实例都具有 constructor 属性，它指向创建该实例的构造器函数。
	
### 5.修改原型

  但更关键的是，整条继承链动态地更新了，任何由此构造器创建的对象实例都自动获得了这个方法。
	
  这种继承模型下，上游对象的方法不会复制到下游的对象实例中；下游对象本身虽然没有定义这些方法，但浏览器会通过上溯原型链、从上游对象中找到它们。
	
  这种继承模型提供了一个强大而可扩展的功能系统。
	
### 6.构造函数

	`注意`: 如果不写new，这就是一个普通函数，它返回undefined。但是，如果写了new，它就变成了一个构造函数，它绑定的this指向新创建的对象，

	并默认返回this，也就是说，不需要在最后写return this;。
	
## 1.String 对象

### 截取字符串

```javascript
	var str = 'jsString';
	str.slice(0, 3); jsS
```

	第一个参数是开始提取的字符位置，第二个参数是提取的最后一个字符后一位置。所以提取从第一个位置开始，直到但不包括最后一个位置。
	
	(此例中)你也可以说第二个参数等于被返回的字符串的长度。

###  2.charAt()方法

	charAt() 方法可返回指定位置的字符。
	
```javascript
<script type="text/javascript">
	var str="Hello world!"
	document.write(str.charAt(1))
</script>
```

输出结果:'e'。

## 2.Date 对象

### 构造函数

```javascript
  new Date();
  new Date(value);
  new Date(dateString);
  new Date(year, month[, day[, hour[, minutes[, seconds[, milliseconds]]]]]);
```
### 参数

  `value`:代表自1970年1月1日00:00:00 (世界标准时间) 起经过的毫秒数。
	
  `dateString`: 表示日期的字符串值。该字符串应该能被 Date.parse() 方法识别。
	
  `year/month/day/hour/min/sec`:整数值。
	
  `milliseconds`:毫秒。
	
### 方法

  `Date.now()`:返回至今的毫秒数。
	
  `Date.parse()`:解析一个表示日期的字符串，并返回从 1970-1-1 00:00:00 所经过的毫秒数。
	
  `Date.UTC()`:接受和构造函数最长形式的参数相同的参数（从2到7），并返回从 1970-01-01 00:00:00 UTC 开始所经过的毫秒数。
	
### Date 事例

  `Date.prototype.getTime()`: 返回从1970-1-1 00:00:00 UTC（协调世界时）到该日期经过的毫秒数，
	
	 对于1970-1-1 00:00:00 UTC之前的时间返回负值。
	 
### conversion getter

  `Date.prototype.toDateString()`:以人类易读（human-readable）的形式返回该日期对象日期部分的字符串。
	
  `Date.prototype.toTimeString()`:以人类易读格式返回日期对象时间部分的字符串。
	
  `Date.prototype.toLocaleDateString()`: 返回一个表示该日期对象日期部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
	
  `Date.prototype.toLocaleTimeString()`:返回一个表示该日期对象时间部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
  

  `Date.prototype.toTimeString()`:以人类易读格式返回日期对象时间部分的字符串。
	
  `Date.prototype.toLocaleDateString()`: 返回一个表示该日期对象日期部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
	
  `Date.prototype.toLocaleTimeString()`:返回一个表示该日期对象时间部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
	
## 3.Math对象

	Math 是一个内置对象， 它具有数学常数和函数的属性和方法。不是一个函数对象。
	
	与其它全局对象不同的是, Math 不是一个构造器.  Math 的所有属性和方法都是静态的. 
	
### 属性

	`Math.PI`:圆周率，一个圆的周长和直径之比，约等于 3.14159。
	
	`Math.LOG2E`:以2为底E的对数, 约等于 1.443.
	
	`Math.SQRT1_2`:1/2的平方根, 约等于 0.707.
	
### 方法

	`Math.abs(x)`:返回绝对值.
	
	`Math.cbrt(x)`:返回数值的立方根.
	
#### polyfill

	```javascript
	if (!Math.cbrt) {
		Math.cbrt = function(x) {
			var y = Math.pow(Math.abs(x), 1/3);
			return x < 0 ? -y : y;
		};
	}
	```
	
	`Math.ceil(x)` : 函数返回大于或等于一个给定数字的最小整数。
	
	`Math.floor(x)` : 返回小于x的最大整数。
	
	`Math.hypot([x[,y[,…]]])` : 返回其参数平方和的平方根。
	
	`Math.max([x[,y[,…]]])` : 返回参数中的最大值。
	
	`Math.min([x[,y[,...]]])` : 返回参数中的最小值。
	
	`Math.pow(x,y)` : 返回x的y次幂。
	
	`Math.random()` : 返回一个[0, 1)的随机数。
	
	`Math.round(x)` : 返回四舍五入的x的整数。
	
	`Math.sign()` : 函数返回一个数字的符号, 指示数字是正数，负数还是零。此函数共有5种返回值, 分别是 1, -1, 0, -0, NaN. 
	
	代表的各是正数, 负数, 正零, 负零, NaN。
	
	`Math.sqrt(x)` : 返回x的算术平方根。
	
	`Math.trunc(x)` : 返回x的整数部分,去除小数。
	
## 4.Array对象

### 方法

* `reduce`: 累加器。 eg: `arr.reduce(reducer[, init])`
	
	`reducer`函数包含四个参数：acc(累加器), item(当前项), index(索引), arr(源数组)
	
```javascript
var arr = [1, 2, 3, 4, 5]

arr.reduce((acc, num) => return acc + num)

>15
```

回调函数第一次执行时，`accumulator` 和`currentValu`的取值有两种情况：如果调用`reduce()`时提供了`initialValue`，

`accumulator`取值为`initialValue`，`currentValue`取数组中的第一个值；如果没有提供 `initialValue`，

那么`accumulator`取数组中的第一个值，`currentValue`取数组中的第二个值

数组去重

```javascript
let arr = [1,2,1,2,3,5,4,5,3,4,4,4,4];
let result = arr.sort().reduce((init, current)=>{
    if(init.length===0 || init[init.length-1]!==current){
        init.push(current);
    }
    return init;
}, []);
console.log(result); //[1,2,3,4,5]
```

* `find()` : 返回数组中满足提供的测试函数的第一个元素的值。否则返回 `undefined`。
