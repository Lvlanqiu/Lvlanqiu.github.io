

> 因为公司项目需求，于是开始这个canvas探索之旅，说实话，网上的资料都是好几年前的了，忽然觉得自己非常脱轨。但是还是要好好研究一下，毕竟是工作，要吃饭的 : )


开发基于h5、js

### 1.html结构
```
<canvas id="drawPanel" width="500" height="500">这里是替代内容</canvas>
```
### 2.上下文渲染（2d），也就是画笔
```
var canvas = document.getElementById("drawPanel");
var ctx = document.getContext('2d');//画笔对象
```
有了ctx这个对象，你就可以调用canvas的各种画图方法，比如矩形、弧形等。 图形的基本元素是路径， 路径是通过不同颜色和宽度的线段或曲线相连形成的不同形状的点的集合
### 3.激动人心的第三步 : ) 我们来整理一下我们的构建步骤
- 初始化一个canvas
- 设置canvas的宽高和背景色(当然是#ffffff)
    - cxt.fillStyle
- 设置笔触的颜色和粗细
    - cxt.strokeStyle
    - cxt.lineWidth
- 一个小小的优化，笔触设置为圆头
    - cxt.lineCap
- 通过3个事件：touchstart、touchmove、touchend来监听记录用户的绘画路径，并将其画在canvas上

####然后我们再来详细说明一下3个监听事件中，我们要做的事情，大致就是 创建绘图路径-设置路径起点-绘出路径-关闭路径-渲染图形
- touchstart
    - cxt.beginPath();//~~开始一段冒险~~，不，是初始化一个路径
    - cxt.moveTo();//~~从纯白镇出发~~，不，是设置起点
- touchmove
    - cxt.lineTo();//脑中记录好要走的路线
    - cxt.stroke();//嘿，将墨水儿泼出去
- touchend
    - cxt.closePath();//嗯，停笔，毛笔可以洗洗挂起来了
#### 最后呢就是2个基本的操作：清除画布和保存成图片
- cxt.clearRect();//清除一个矩形内容，内容变透明
    - fillRect(x, y, width, height);//直接画一个白色填充矩形也是可以的
- canvas.toDataURL();// 图片转为base64格式

---

结束语：以上是对[金大光](https://blog.csdn.net/qq_17757973/article/details/78721917)先生博文的总结，是一个十分粗糙的原形，但是提供了一个很好的思路了，也可以满足项目需求，但是这个功能是有很大的深入空间的，比如说锯齿，笔刷的研究。

[1]: https://blog.csdn.net/qq_17757973/article/details/78721917
