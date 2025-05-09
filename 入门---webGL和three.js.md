## **<font style="color:rgb(51, 51, 51);">2.1 canvas和webgl的区别</font>**
### 2.1.1 <canvas>画布
```plain
<canvas></canvas>
```

是HTML5新增的一个DOM元素

#### 用途：显示二维和三维的图图形
#### 绘制：<font style="color:#DF2A3F;">二维图形</font>可以使用（canvas API或者webGL API）；<font style="color:#DF2A3F;">三维图形使用WebGL API</font>
#### Canvas API：提供<font style="color:#DF2A3F;">二维</font>绘图的方式
+ 图形的绘制主要通过 **<font style="color:#DF2A3F;">CanvasRenderingContext2D</font>** 接口完成
+ canvas.getContext('2d') ----获取实例

#### WebGL API：提供<font style="color:#DF2A3F;">三维</font>绘图的方式
+ 图形的绘制主要通过**<font style="color:#DF2A3F;">WebGLRenderingContext</font>**接口完成
+ canvas.getContext('webgl') ----获取实例

##### 拓展：**<font style="color:#DF2A3F;">WebGL2RenderingContext</font>**
+ canvas.getContext('webgl2') ----获取实例

## **<font style="color:rgb(51, 51, 51);">2.2 认识webgl</font>**
### 2.2.1 什么是**<font style="color:rgb(51, 51, 51);">webgl</font>**
一种3D绘图协议，衍生于Opengl ES2.0，可以结合html5和javascript在网页上绘制和渲染2/3维图形

可以实现：

+ 数据可视化（数据图表）
+ 图形/游戏的渲染引擎
+ 交互演示、图形渲染
+ 地图
+ VR
+ 物品展示
+ 室内设计
+ 城市规划
+ 。。。。。。

### 2.2.2 与传统的3D开发相比，**<font style="color:rgb(51, 51, 51);">webgl的优势</font>**
+ 内嵌在浏览器中，不需要安装任何插件即可运行
+ 只需要一个文本编辑器和浏览器，就可以编写三维图形程序

### 2.2.3 **<font style="color:rgb(51, 51, 51);">webgl程序结构</font>**
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1699253069614-000ed21c-3b21-4b32-a414-2bcd548b6421.png)

+ GLSL ES是以字符串的形式存在在 javascript 中的

### 2.2.4 **<font style="color:rgb(51, 51, 51);">webgl的开源框架</font>**
#### three,js ：JavaScript 3D WebGL库
#### Babylon.js：web3d图形引擎
#### KickJS：web的开源图形和游戏引擎
#### ClayGL：构建可扩展的Web3D应用程序
#### PlayCanvas：网络游戏和3D图形引擎
#### WebGLStudio.js和Litescene.js：开源Web 3D图形编辑器和创建器
#### Luma：Uber的3D WebGL可视化库
#### A-Frame是用于构建VR(虚拟现实)体验的Web框架
## **<font style="color:rgb(51, 51, 51);">2.3 画一个有颜色填充的矩形</font>**
### canvas API方法
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  </head>
  <body>
    <canvas id="canvas" width="400" height="400">
      此浏览器不支持canvas
    </canvas>
  </body>
</html>

<script>
  const ctx =document.getElementById('canvas')
  const c = ctx.getContext('2d')
  // 设置填充颜色
  c.fillStyle='pink'
  // 坐标（x，y，width，height）
  c.fillRect(10,10,100,100)

</script>
```

- [x] getContext('2d')
- [x] c.fillStyle='pink'
- [x] c.fillRect(10,10,100,100)   // 坐标（x，y，width，height）

### webGL API方法
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <canvas id="canvas" width="400" height="400">
        此浏览器不支持canvas
    </canvas>
</body>
</html>

<script>
    const ctx = document.getElementById('canvas')
    const gl = ctx.getContext('webgl')
    // 指定绘图区域的背景色，设置颜色和透明度RGBA
    gl.clearColor(0.5,0.2,0.7,1.0)
    // 将指定缓冲区设定为预定的值
    gl.clear(gl.COLOR_BUFFER_BIT)
</script>
```

- [x] getContext('webgl')
- [x] **<font style="color:#2F4BDA;">gl.clearColor(0.5,0.2,0.7,1.0)    // 指定绘图区域的背景色，设置颜色和透明度RGBA</font>**
- [x] **<font style="color:#2F4BDA;">gl.clear(gl.COLOR_BUFFER_BIT)    //  清除指定缓冲区，并将指定缓冲区设定为预定的值</font>**

#### 缓冲区（颜色缓冲区、深度缓冲区、模板缓冲区、累积缓冲器、纹理缓冲区、渲染缓冲区、顶点缓冲区）
[WebGL学习 - 掘金](https://juejin.cn/post/7072249930961649678)

[颜色缓冲区、深度缓冲区、模板缓冲区和累积缓冲区-CSDN博客](https://blog.csdn.net/linjf520/article/details/52183859)

##### <font style="color:rgb(7, 17, 27);">深度缓冲区存储的是像素的深度值，在深度测试时，确定物体遮挡关系，看下哪些像素是需要绘制的（被遮挡的像素不参与绘制）</font>
- [x] **<font style="color:#2F4BDA;">gl.clearDepth(1.0)   </font>**
- [x] **<font style="color:#2F4BDA;">gl.clear(gl.Depth_BUFFER_BIT)  </font>**

##### <font style="color:rgb(7, 17, 27);">模板缓冲区可以理解为：通过一个模具进行绘制，就像模板喷字一样，不在模板中的像素不参与绘制</font>
- [x] **<font style="color:#2F4BDA;">gl.clearStencil(0) </font>**
- [x] **<font style="color:#2F4BDA;">gl.clear(gl.Stencil_BUFFER_BIT) </font>**

****

## **<font style="color:rgb(51, 51, 51);">2.4 绘制一个点</font>**


