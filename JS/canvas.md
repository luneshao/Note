# canvas

## 绘制矩形

1. `fillRect(x, y, width, height)` : 绘制一个填充的矩形。

2. `strokeRect(x, y, width, height)` : 绘制一个矩形的边框。

3. `clearRect(x, y, width, height)` : 清除指定矩形区域，让清除部分完全透明。

## 绘制路径

1. `beginPath()` : 新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。

2. `closePath()` : 闭合路径之后图形绘制命令又重新指向到上下文中。

3. `stroke()` : 通过线条来绘制图形轮廓。

4. `fill()` : 通过填充路径的内容区域生成实心的图形。

5. `moveTo(x, y)` : 将笔触移动到指定的坐标x以及y上。

6. `lineTo(x, y)` : 绘制一条从当前位置到指定x以及y位置的直线。

## 绘制圆弧

1. `arc(x, y, radius, startAngle, endAngle, anticlockwise)`  : 画一个以（x,y）为圆心的以radius为半径的圆弧（圆），

从startAngle开始到endAngle结束，按照anticlockwise给定的方向（默认为顺时针）来生成。

2. `arcTo(x1, y1, x2, y2, radius)` : 根据给定的控制点和半径画一段圆弧，再以直线连接两个控制点。

## 二次贝塞尔曲线及三次贝塞尔曲线

1. `quadraticCurveTo(cp1x, cp1y, x, y)` : 绘制二次贝塞尔曲线，cp1x,cp1y为一个控制点，x,y为结束点。

2. `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)` : 绘制三次贝塞尔曲线，cp1x,cp1y为控制点一，cp2x,cp2y为控制点二，x,y为结束点。
