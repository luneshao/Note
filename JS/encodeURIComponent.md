# encodeURI()和encodeURIComponent() 区别

[原文链接](https://www.cnblogs.com/season-huang/p/3439277.html)

Global对象的encodeURI()和encodeURIComponent()方法可以对URI进行编码，以便发送给浏览器。有效的URI中不能包含某些字符，例如空格。

而这URI编码方法就可以对URI进行编码，它们用特殊的UTF-8编码替换所有无效的字 符，从而让浏览器能够接受和理解。

其中`encodeURI()`主要用于整个`URI`,而`encode-URIComponent()`主要用于对`URI`中的某一段。它们的主要区别在于,

`encodeURI()`不会对本身属于`URI`的特殊字符进行编码,例如冒号、正斜杠、问号和井字号;而`encodeURIComponent()`则会对它发现的任何非标准字符进行编码。

decodeURIComponent()进行解码
