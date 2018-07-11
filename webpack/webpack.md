# webpack笔记
 
## 1.loader

webpack 可以使用 loader 来预处理文件。

### style-loader

样式不会添加在 `import/require()` 上，而是在调用 `use/ref` 时添加。如果 `unuse/unref` 与 `use/ref` 一样频繁地被调用，那么样式将从页面中删除。

loader 可以将文件从不同的语言（如 TypeScript）转换为 JavaScript，或将内联图像转换为 data URL。

### 实例

1.首先安装相对应的 loader;

2.然后指示 webpack 对每个 .css 使用 css-loader，以及对所有 .ts 文件使用 ts-loader.

## 2.output

### .1 output.filename

* 对于单个文件入口，filename是一个静态名称。

* 使用入口名称 : [name].bundle.js ;

* 使用内部`chunk id` : [id].bundle.js ;

* 使用每次构建中，唯一的`hash`的生成 : [name].[hash].bundle.js ;

* 使用基于`chunk`内容的hash : [chunkhash].bundle.js

## 代码分离

### 动态导入

动态地加载模块。调用 import() 之处，被作为分离的模块起点，意思是，被请求的模块和它引用的所有子模块，会分离到一个单独的 chunk 中。
