# VUE-CLI 学到的配置

## css相关

### 自动化导入

如果你想自动化导入文件 (用于颜色、变量、mixin……)，你可以使用 `style-resources-loader`。例子是一个关于`Stylus` 的在每个单文件组件

和 `Stylus` 文件中导入 .styl 文件。

```javascript
// vue.config.js
const path = require('path')

module.exports = {
  chainWebpack: config => {
    const types = ['vue-modules', 'vue', 'normal-modules', 'normal']
    types.forEach(type => addStyleResource(config.module.rule('stylus').oneOf(type)))
  },
}

function addStyleResource (rule) {
  rule.use('style-resource')
    .loader('style-resources-loader')
    .options({
      patterns: [
        path.resolve(__dirname, './src/styles/imports.styl'),
      ],
    })
}
```
