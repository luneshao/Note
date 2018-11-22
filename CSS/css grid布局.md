# css grid布局

[原文链接](https://www.cnblogs.com/wangzhichao/p/7987346.html)

code:
```html
<style>
  .wrapper {
    display: grid;
    grid-template-rows: 200px 150px 130px;
    grid-template-columns: 90px 120px;
  }
  
  .item1{
    grid-rows-start: 1;
    grid-rows-end: 4;
    background: #eee;
  }
  .item2{
    grid-column-start: 1;
    grid-column-end: 3;
    background: #fce;
  }
</style>

<div class='wrapper'>
  <div class='item1'>1</div>
  <div class='item2'>2</div>
  <div class='item3'>3</div>
  <div class='item4'>4</div>
  <div class='item5'>5</div>
  <div class='item6'>6</div>
</div>
```

## step:

1.将display设置为grid: `display: grid`

2.设置行和列： `grid-template-rows` & `grid-template-columns`, 每个属性后有几个值就是几列, 数值为行高或列宽

3.设置子元素的大小及位置：`grid-row-start` & `grid-row-end` & `grid-column-start` & `grid-column-end`

  eg: {grid-row-start: 1; grid-row-end: 3} /*当前的子元素占两行*/
