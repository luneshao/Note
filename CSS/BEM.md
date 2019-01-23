# css 文件组织结构

[链接](https://www.w3cplus.com/css/css-architecture-3.html)
```
  - scss/
    - lib/ 
    - helpers/ 
    - variables/ 
    - base/ 
    - layouts/ 
    - objects/ 
    - components/ 
    styles.scss 
    _utilities.scss
```
* `lib/` 文件夹
    lib/文件夹只包含一个文件 — _lib.scss。 _lib.scss 中声明了所有我在项目中使用的库文件。
* `helpers/` 文件夹
    helpers/文件夹中放置的是项目中使用的封装的方便使用的mixins 和 functions。很多这种mixins的例子，
    如： 清除浮动的hack, 元素的显隐和CSS开发的形状（如三角形）等等。
* `variables/` 文件夹
    variables/ 文件夹是存储我在项目中使用的变量的地方。
* `base/` 文件夹
    base/ 文件夹是存放我开发的除了Normalize.css之外的所有resets。例如：我会强制的重置 margins、paddings和输入框、按钮等元素的样式。
* `layouts/` 文件夹
    layouts/文件夹是用来存放我编写的在整个项目中全局使用的布局样式。
* `objects/` 和 `components/` 文件夹
    这两个文件夹是分别用来存放我编写的对象和组件的地方。 每一个对象/组件都有自己的文件。
* `_utilities.scss` 文件
    _utilities.scss文件是用来存放我编写的 公用命名空间类 。
