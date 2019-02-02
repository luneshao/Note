## echarts 笔记

### 1.颜色主题
  [颜色](http://echarts.baidu.com/tutorial.html#ECharts%20%E4%B8%AD%E7%9A%84%E6%A0%B7%E5%BC%8F%E7%AE%80%E4%BB%8B)
  var chart = echarts.init(dom, 'light'); </br>
  [个性配置](http://echarts.baidu.com/theme-builder/) </br>
  ```javascript
  // 假设主题名称是 "vintage"
  $.getJSON('xxx/xxx/vintage.json', function (themeJSON) {
    echarts.registerTheme('vintage', JSON.parse(themeJSON))
    var chart = echarts.init(dom, 'vintage');
  });
  ```
  ### 2.异步数据加载及更新
  ####  2.1.loading 动画
    一个 loading 的动画来提示用户数据正在加载。 </br>
  ```javascript
  myChart.showLoading();
  $.get('data.json').done(function (data) {
    myChart.hideLoading();
    myChart.setOption(...);
  });
  ```
  #### 2.2.数据的动态更新
    所有数据的更新都通过 setOption实现，你只需要定时获取数据，setOption 填入数据, </br>
    ECharts 会找到两组数据之间的差异然后通过合适的动画去表现数据的变化。
  ```javascript
  setInterval(function(){
    var a = 10;
    a += Math.floor(Math.random() * 10);
    population.series[0].data.push(a);
    population.xAxis.data.push('新增');
    myChart.setOption(population);
  }, 1000);
  ```
### 3.使用dataset管理数据
#### 
