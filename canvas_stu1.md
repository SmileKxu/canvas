## canvas 学习

canvas 元素是一个标签
```html
<canvas id='tutroial' width='150' height='150' ></canvas>
```
cancas 标签只有两个属性(width和height)。这些都是可选的，并且可以利用DOM properties来设置。
若没有设置width和height，那么初始化宽度为300像素高度为150像素。

<canvas>元素需要结束标签(</canvas>)。如果结束标签不存在，则文档其余部分会被认为是替代内容，将不会显示出来。

canvas起初是空白的。为了展示，首先脚本需要找到渲染上下文，然后在它的上面绘制。
<canvas>元素有一个叫做getContext()的方法，这个方法是用来获得渲染上下文和它的绘画功能。
getContext()只有一个参数，上下文的格式。
```html
let canvas = document.querySelector('#tutorial');
let ctx = canvas.getContext('2d');
```
获得了canvas之后，就可以通过使用getContext()方法来绘制上下文。

#### 检查支持性
替换内容是用于在不支持<canvas>标签的浏览器中展示的。通过简单的测试getContext()方法的存在，脚本可与检查
编程支持性。上面的代码片段变成如下:
```html
let canvas = document.getElementById('tutorial');

if(canvas.getContext){
   let ctx = canvas.getContext('2d');
} else {
   // canvas-unsupported code here
}
```

### 绘制矩形
HTML中的元素canvas只支持一种原生的图形绘制:矩形。所有其他的图形的绘制都至少需要生成一条路径。
canvas提供了三种方法绘制矩形:
```js
fillRect(x, y, width, height)
// 绘制一个填充的矩形
strokeRect(x, y, width, height)
// 绘制一个矩形的边框
clearRect(x, y, width, height)
// 清除指定矩形区域，让清楚部分完全透明
```

### 绘制路径
图形的基本元素是路径。路径是通过不同颜色和宽度的线段或曲线相连形成的不同形状的点的集合。
一个路径，甚至一个子路径，都是闭合的。使用路径绘制图形需要一些额外的步骤。
1. 首先，你需要创建路径起始点。
2. 然后使用画图命令去画出路径。
3. 之后需要把路径封闭
4. 一旦路径生成，就能通过描边或者填充路径区域来渲染图形。

以下是所要用到的函数:
```js
beginPath()
// 新建一条路径，生成之后，图形绘制命令被指向到路径上生成路径。
closePath()
// 闭合路径之后图形绘制命令又重新指向到上下文中。
stroke()
// 通过描边来绘制图形轮廓。
fill()
// 通过填充路径的内容区域生成实心的图形
```
生成路径的第一步叫做beginPath()。每次这个方法调用之后，列表清空重置，然后我们就可以
重新绘制新的图形。第一条路径构造命令通常被视为是moveTo()。

第二步就是调用函数指定绘制路径。

第三，就是闭合路径closePath()，不是必须的。这个方法会通过绘制一条从当前点到开始点的直线来闭合
图形。如果图形是已经闭合了的，即当前点为开始点，该函数什么也不做。当调用fill()函数时，所有没有
闭合的形状都会自动闭合，所以你不需要调用closePath()函数。但是调用stroke()时不会闭合。

### 移动笔触
moveTo(x, y); 将笔触移动到指定的坐标x以及y上。
当canvas初始化或者beginPath()调用后，你通常会使用moveTo()函数设置起点，我们也能够使用moveTo()
绘制一些不连续的路径。

### 线
绘制直线，需要用到的方法lineTo()。
lineTo(x, y); 绘制一条从当前位置到指定x以及y位置的直线。
该方法有两个参数:x以及y，代表坐标系中直线结束的点。

### 圆弧
绘制圆弧或者圆，我们使用arc()方法。
```js
arc(x, y, radius, startAngle, endAngle, anticlockwise)
```
画一个以(x, y)为圆心的以radius为半径圆弧(圆)，从startAngle开始到endAngle
结束，按照anticlockwise给定的方向(默认为顺时针)来生成。
arc()函数中的角度单位是弧度，不是度数。角度与弧度的js表达式为:
```
radians = (Math.PI/180)*degress
```

### canvas 色彩
若要对canvas图形上色，两个重要的属性就是: fillStyle 和 strokeStyle

fillStyle = color 设置图形的填充颜色。
strokeStyle  color 设置图形的轮廓的颜色

