# JS学习笔记

## 1.String 对象
    
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
  ``
