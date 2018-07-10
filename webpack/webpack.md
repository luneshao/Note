# webpack笔记
 
## loader

webpack 可以使用 loader 来预处理文件。

### style-loader

样式不会添加在 `import/require()` 上，而是在调用 `use/ref` 时添加。如果 `unuse/unref` 与 `use/ref` 一样频繁地被调用，那么样式将从页面中删除。

loader 可以将文件从不同的语言（如 TypeScript）转换为 JavaScript，或将内联图像转换为 data URL。

### 实例

1.首先安装相对应的 loader;

2.然后指示 webpack 对每个 .css 使用 css-loader，以及对所有 .ts 文件使用 ts-loader
