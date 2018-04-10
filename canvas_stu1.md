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
let ctx = canvas.getContext('2d')s;
```
获得了canvas之后，就可以通过使用getContext()方法来绘制上下文。
