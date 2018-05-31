# css 属性笔记
## 1.font
	`font` : font-style | font-variant | font-weight | font-size | line-height | font-family ; <br>
	不过使用这种简写需要注意几点：要使简写定义有效必须至少提供 font-size 和 font-family 这两个属性 ；<br>
	同时font-weight, font-style 以及 font-varient 这几个属性如果不做设定的话将默认为normal。
## 2.contain
	`contain`: none | strict | content | [ size || layout || style || paint ]
	contain 属性允许开发者声明当前元素和它的内容尽可能的独立于 DOM 树的其他部分。这使得浏览器在重新计算布局
	样式、绘图或它们的组合的时候，只会影响到有限的 DOM 区域，而不是整个页面。
	`none`:声明元素正常渲染，没有包含规则。 
	`strict`: 声明所有的包含规则应用于这个元素。这样写等价于 contain: size layout style paint。 
	`content`: 声明这个元素上有除了 size 外的所有包含规则。等价于 contain: layout style paint。 
	`size`: 声明这个元素的尺寸会变化，不需要去检查它依赖关系中的尺寸变化。 
	`layout`: 声明没有外部元素可以影响它内部的布局，反之亦然。 
	`style`: 声明那些同时会影响这个元素和其子孙元素的属性，都在这个元素的包含范围内。
	`paint`: 声明这个元素的子孙节点不会在它边缘外显示。如果一个元素在视窗外或因其他原因导致不可见，则同样保证它的子孙节点不会被显示。
