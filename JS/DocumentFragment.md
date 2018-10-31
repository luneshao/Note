# DocumentFragment的理解

官方说明：创建文档片段对象。

[原文链接](https://www.cnblogs.com/xiaohuochai/p/5816048.html)

## 特征

* `document.createDocumentFragment()`方法,创建一个文档片段。文档片段下可以通过appendChild()方法添加子节点。

* 当将文档片段添加到文档流中时，将不会添加根节点，只添加子孙节点。

* 文档片段节点没有父节点parentNode。

* 当从某一结点下，将其子节点往文档片段中append时，目标节点下的节点会被移除。

## 作用

* 若有大量节点需要添加进文档流，可以采用文档片段的形式。减少浏览器渲染次数，优化性能。
