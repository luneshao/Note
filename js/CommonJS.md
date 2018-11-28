# commonJS
## 1.exports
    CommonJS规范规定，每个模块内部，module变量代表`当前模块`。这个变量是一个`对象`，它的exports属性（即module.exports）是对外的接口。<\br>
加载某个模块，其实是加载该模块的`module.exports属性`。<br\>
## 2.module对象的属性<br\>
* `module.id` 模块的识别符，通常是带有绝对路径的模块文件名。<br\>
* `module.filename` 模块的文件名，带有绝对路径。<br\>
* `module.loaded` 返回一个布尔值，表示模块是否已经完成加载。<br\>
* `module.parent` 返回一个对象，表示调用该模块的模块。<br\>
* `module.children` 返回一个数组，表示该模块要用到的其他模块。<br\>
* `module.exports` 表示模块对外输出的值。<br\>
## 3.exports 代替module.exports
    为了方便，Node为每个模块提供一个exports变量，指向module.exports。这等同在每个模块头部，有一行这样的命令。<br\>
```javascript
var exports = module.exports;
```
`注意，不能直接将exports变量指向一个值，因为这样等于切断了exports与module.exports的联系。
    如果一个模块的对外接口，就是一个单一的值，不能使用exports输出，只能使用module.exports输出。`<br\>
## 4.require 加载规则
    `require`命令的基本功能是，读入并执行一个JavaScript文件，然后返回该模块的exports对象。如果没有发现指定模块，会报错。
    * require命令用于加载文件，后缀名默认为.js。
    * 如果参数字符串以`“/”`开头，则表示加载的是一个位于`绝对路径`的模块文件。比如，```require('/home/marco/foo.js')```将加载/home/marco/foo.js。
    * 如果参数字符串以`“./”`开头，则表示加载的是一个位于`相对路径`（跟当前执行脚本的位置相比）的模块文件。<br\>
    比如，`require('./circle')`将加载当前脚本同一目录的circle.js。
    * 如果参数字符串不以`“./“`或`”/“`开头，则表示加载的是一个默认提供的`核心模块`（位于Node的系统安装目录中），<br\>
    或者一个位于各级node_modules目录的`已安装模块`（全局安装或局部安装）。
    * 如果参数字符串不以`“./“`或`”/“`开头，而且是一个路径，比如```require('example-module/path/to/file')```，<br\>
    则将先找到example-module的位置，然后再以它为参数，找到后续路径。
    * 如果指定的模块文件没有发现，Node会尝试为文件名添加`.js`、`.json`、`.node`后，再去搜索。`.js`件会以文本格式的JavaScript脚本文件解析，<br\>
    `.json`文件会以JSON格式的文本文件解析，`.node`文件会以编译后的二进制文件解析。
    * 如果想得到`require`命令加载的确切文件名，使用`require.resolve()`方法。
## 5.目录的加载规则
    我们会把相关的文件会放在一个目录里面，便于组织。这时，最好为该目录设置一个入口文件，让require方法可以通过这个入口文件，加载整个目录。
    在目录中放置一个package.json文件，并且将入口文件写入main字段。
## 6.模块的缓存
    第一次加载某个模块时，Node会缓存该模块。以后再加载该模块，就直接从缓存取出该模块的module.exports属性。
    如果想要多次执行某个模块，可以让该模块输出一个函数，然后每次`require`这个模块的时候，重新执行一下输出的函数。
## 7.`require`函数及其辅助方法
    `require()`: 加载外部模块
    `require.resolve()`：将模块名解析到一个绝对路径
    `require.main`：指向主模块
    `require.cache`：指向所有缓存的模块
    `require.extensions`：根据文件的后缀名，调用不同的执行函数
