# JS对象
## OOP 面向对象
	JavaScript 用一种称为`构建函数`的特殊函数来定义对象和它们的特征。构建函数非常有用，因为很多情况下您不知道实际需要多少个对象（实例）。<br>
	构建函数提供了创建您所需对象（实例）的有效方法，将对象的数据和特征函数按需联结至相应对象。
## 1.String 对象
### 截取字符串
```javascript
	var str = 'jsString';
	str.slice(0, 3); jsS
```
	第一个参数是开始提取的字符位置，第二个参数是提取的最后一个字符后一位置。所以提取从第一个位置开始，直到但不包括最后一个位置。（此例中）你也可以说第二个参数等于被返回的字符串的长度。
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
  `Date.prototype.getTime()`: 返回从1970-1-1 00:00:00 UTC（协调世界时）到该日期经过的毫秒数，<br>
    对于1970-1-1 00:00:00 UTC之前的时间返回负值。
### conversion getter
  `Date.prototype.toDateString()`:以人类易读（human-readable）的形式返回该日期对象日期部分的字符串。
  `Date.prototype.toTimeString()`:以人类易读格式返回日期对象时间部分的字符串。
  `Date.prototype.toLocaleDateString()`: 返回一个表示该日期对象日期部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
  `Date.prototype.toLocaleTimeString()`:返回一个表示该日期对象时间部分的字符串，该字符串格式与系统设置的地区关联（locality sensitive）。
  
