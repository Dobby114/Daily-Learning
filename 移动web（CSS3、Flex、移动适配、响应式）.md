## CSS3
css3和html5的属性不是支持所有浏览器的，他们对老版本浏览器支持较差

css常用的语义化标签：[https://blog.csdn.net/HarryHY/article/details/101481075](https://blog.csdn.net/HarryHY/article/details/101481075)

### 字体图标
目标：使用字体图标技巧实现网页中**<font style="color:#E8323C;">简洁的图标</font>**效果

+ 字体图标**<font style="color:#E8323C;">展示的是图标，本质是字体。</font>**
+ 处理网页中**<font style="color:#E8323C;">简单的、颜色单一</font>**的图片

#### 字体图标的优点：
+ **<font style="color:#096DD9;">灵活性</font>**：灵活地修改样式，例如：尺寸、颜色等
+ **<font style="color:#096DD9;">轻量级</font>**：体积小、渲染块、降低服务器请求次数
+ **<font style="color:#096DD9;">兼容性</font>**：几乎兼容所有主流浏览器
+ **<font style="color:#096DD9;">使用方便</font>**：
        1. **<font style="color:#F5222D;">下载字体包 </font>**
        2. **<font style="color:#F5222D;">使用字体图标</font>**

#### 图标库（下载官方库里的简单的图标，复杂的不可以）
+ Iconfont：[https://www.iconfont.cn/](https://www.iconfont.cn/)
+ 添加至项目然后下载至本地

#### 使用字体图标--类名：（css样式调整同字体--大小、颜色等）
+ **<font style="color:#389E0D;">引入字体图标样式表</font>**

<font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">link</font><font style="color:#9cdcfe;background-color:#1e1e1e;">rel</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"stylesheet"</font><font style="color:#9cdcfe;background-color:#1e1e1e;">href</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"../icon/download/icon_font/iconfont.css"</font><font style="color:#808080;background-color:#1e1e1e;">></font>

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662187692674-c21fdb1c-41ff-476f-a5a1-f08a2de15cc5.png)

一定是下载的icon文件夹里的**iconfont.css**

+ **<font style="color:#389E0D;">调用图标对应的类名，必须调用</font>****<font style="color:#F5222D;">2个类名</font>**
    1. <font style="color:#F5222D;">iconfont</font>类：基本样式，包含字体的使用等（固定）
    2. <font style="color:#F5222D;">icon--xxx</font>：图标对应的类名----不带点儿

#### 上传矢量图：（图标库没有项目所需的图标）
1. 与设计师沟通，得到**<font style="color:#F5222D;">SVG矢量图</font>**
2. IconFont网站上传图标（**去除颜色提交**），下载使用



### 平面转换
目标：使用transformer属性实现元素的位移、旋转、缩放等效果

如果写了多个transform，前面写的属性会被**覆盖**

#### 注意transform覆盖问题
#### 平面转换
+ 改变盒子在平面内的形态（**<font style="color:#E8323C;">位移</font>**、旋转、**<font style="color:#E8323C;">缩放</font>**）
+ 2D转换

#### 平面转换属性
- [x] **<font style="color:#E8323C;">transform</font>**

#### 位移：使用transform实现元素位移效果
- [x] 语法：**<font style="color:#389E0D;">transform：translate（水平移动距离，垂直移动距离）；</font>**
- [x] 取值（**正负**均可）
+ 像素单位数值
+ 百分比（参照物为盒子自身尺寸）

注意：<font style="color:#D46B08;">x轴正向为右，y轴正向为下</font>

**<font style="color:#D46B08;">可以使用translate快速实现绝对定位的元素居中效果</font>**

##### 技巧
+ translate()如果只给**<font style="color:#D46B08;">一个值</font>**，表示**x轴**方向移动
+ **单独设置某个方向**的移动距离：**<font style="color:#389E0D;">translateX()和translateY()</font>**

#### 旋转：使用rotate实现元素旋转效果----<font style="color:#CF1322;">必须配合过渡才会有效果</font>
- [x] 语法：**<font style="color:#389E0D;">transform：rotate（角度）</font>**；如----transform：rotate(360deg)
- [x] 技巧：取值正负均可（正--顺时针；负--逆时针）

#### 转换原点：<font style="color:#F5222D;">使用transform-origin属性改变转换原点</font>（转换包括位移、旋转、缩放）
- [x] 语法：
+ 默认原点是盒子中心点
+ **<font style="color:#389E0D;">transform-origin：原点水平位置 原点垂直位置；</font>****--属性加在标签本身而不是加在hover上**
- [x] 取值
+ <font style="color:#D4380D;">方位名词（left、top、right、bottom、center）</font>
+ 像素单位数量
+ 百分比（参照盒子自身尺寸计算）

#### 多重转换（有两个或两个以上的转换效果）---<font style="color:#096DD9;">一定要用复合属性</font>，如果拆成两个会<font style="color:#CF1322;">被覆盖</font>（都是transform属性）
目标：使用transform复合属性实现多形态转换-----复合属性，多个属性之间用空格隔开

- [x] **<font style="color:#389E0D;">transform：translate() rotate(); </font>** （位移+旋转）--先旋转后位移会产生另外一种效果，**一般先位移后旋转**，因为<font style="color:#096DD9;">旋转会改变坐标轴向</font>。

##### 多重转换如果涉及到旋转往往最后书写
#### 缩放--用scale改变元素的尺寸
- [x] transform:scale(x轴缩放倍数,y轴缩放倍数);
+ 一般情况下，**只为scale设置一个值**，表示x轴和y轴等比例缩放
+ <font style="color:#CF1322;">transform:scale（缩放倍数）；</font>
+ scale值**大于1表示放大**，scale值**小于1表示缩小**

### 渐变
使用background-image属性实现渐变背景效果

+ 渐变是多个颜色逐渐变化的视觉效果
+ 一般用于设置盒子的背景
- [x] **background-image: linear-gradiernt(颜色1，颜色2)；**
- [x] **透明：tranparent**
- [x] 常用：transparent → rgba()

### 空间转换
目标：使用**<font style="color:#E8323C;">transform</font>**属性实现元素在空间内的位移、旋转、缩放等效果

+ 空间：是从坐标轴角度定义的。<font style="color:#E8323C;">x、y和z</font>三条坐标轴构成了一个立体空间，<font style="color:#E8323C;">z轴负轴位置与视线方向相同。</font>
+ 空间转换也叫<font style="color:#E8323C;">3D转换</font>
+ <font style="color:#E8323C;">属性：transform</font>

#### 空间位移
目标：使用translate实现元素空间位移效果

- [x] 语法：
    - [x] **transform: translate3d(x , y, z)**
    - [x] **transform: translateX(值)**
    - [x] **transform: translateY(值)**
    - [x] **transform: translateZ(值)**
- [x] 取值（<font style="color:#E8323C;">正负</font>均可）
+ 像素单位数值
+ 百分比

####  透视
目标：使用**<font style="color:#389E0D;">pespective</font>**属性实现透视效果（近大远小，近实远虚）

- [x] 属性：**<font style="color:#D4380D;">添加给父级</font>**
+ **<font style="color:#389E0D;">perspective: (值px)</font>**
+ 取值：像素单位数值，数值一般在**<font style="color:#D4380D;">800-1200px</font>**
+ 透视距离也称为视距，所谓视距就是**<font style="color:#D4380D;">人的眼睛到屏幕的距离。</font>**

####  空间旋转
目标：使用rotate实现元素空间旋转效果

- [x] transform：rotateZ（值deg）；
- [x] transform：rotateX（值）；
- [x] transform：rotateY（值）；
- [x] x和y轴上的旋转一般配合**<font style="color:#096DD9;">perspective属性</font>**更好看

##### 左手法则：
判断旋转方向：**<font style="color:#096DD9;">左手握住旋转轴，将拇指指向正值方向，此时手指弯曲方向为旋转正值方向。</font>**

##### <font style="color:#096DD9;"> </font>拓展
+ rotate3d(x,y,z,角度度数) :用来**设置自定义旋转轴的位置**及**旋转的角度**
+ x，y，z取值为0-1之间的数字

#### 立体呈现（添加给父级）
目标：使用**<font style="color:#CF1322;">transform-style：preserve-3d</font>**呈现立体图形

##### 实现方法
+ 添加**<font style="color:#389E0D;">transform-style：perserve-3d；</font>**
+ 使**<font style="color:#CF1322;">子元素</font>**处于真正的3d空间
+ 默认值flat，表示子元素处于2D平面内呈现

#### 空间缩放
使用**<font style="color:#389E0D;">scale</font>**实现空间缩放效果

- [x] 语法
+ transform: scaleX (倍数）;
+ transform: scaleY (倍数）;
+ transform: scaleZ (倍数);
+ transform: scale3d (x,y,z);

### 动画
使用**<font style="color:#389E0D;">animation</font>**添加动画效果

过渡：实现<font style="color:#FF7A45;">2个状态间</font>的变化过程

##### 动画效果：实现<font style="color:#08979C;">多个状态</font>间的变化过程，<font style="color:#08979C;">动画过程可控</font>（重复播放、最终画面、是否暂停）
+ 动画的本质是快速切换大量图片时在人脑中形成的具有<font style="color:#FF7A45;">连续性的画面</font>
+ 构成动画的最小单元：<font style="color:#FF7A45;">帧或动画帧</font>

#### 实现步骤
##### 1、定义动画（在css样式中定义）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661060570037-af1dfa91-d84a-4e24-a387-878192a1b958.png)                ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661060570059-788207d5-8f45-41f7-a3b3-55b57f8bdd42.png)

并且动画的开始状态和盒子的默认样式是相同的，此时可以省略开始状态的代码，即from()

##### 2、使用动画（在css中给需要的盒子的css样式加上动画）
<font style="color:#389E0D;">百分比任取，表示的是动画总时长占比</font>

##### ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661060643680-816c339f-a868-45a5-b38c-c3a93d604e10.png)
##### 控制属性
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661061716374-562ab20f-95bf-4b92-ae8a-56f29598ad30.png)

- [x] 速度曲线：如**<font style="color:#389E0D;">linear</font>**，表示匀速；**<font style="color:#389E0D;">steps（数字</font>**）--逐帧动画，表示将一个动画拆分为几部实现
- [x] 延迟时间：让动画延迟一段时间再执行
- [x] 重复次数：直接数写**<font style="color:#389E0D;">数字</font>**或者**<font style="color:#389E0D;">infinite（无限循环）</font>**
- [x] 动画方向：**<font style="color:#389E0D;">alternate</font>**（正--反--正）s
- [x] 执行完毕时状态：**<font style="color:#389E0D;">最初状态--backwards（</font>**默认值），**<font style="color:#389E0D;">结束状态--forwards</font>**
+ **<font style="color:#389E0D;">动画名称和动画时长</font>**必须赋值
+ 取值不分先后顺序
+ <font style="color:#389E0D;">如果有2个时间值，第一个时间表示动画时长，第二个时间表示延迟时间</font>

##### 拆分属性
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661063087101-31bcbcf7-678a-44b6-b845-895bd08c50d7.png)

#### 使用step实现逐帧动画
##### 精灵图动画制作步骤
+ **准备显示区域**
    - 设置盒子尺寸是一张小图的尺寸，背景图为当前精灵图
+ **定义动画**
    - 改变背景图的位置（<font style="color:#CF1322;">移动的距离就是精灵图的宽度</font>）
+ **使用动画**
    - 添加速度曲线<font style="color:#CF1322;">steps(N) </font>,<font style="color:#389E0D;">N与精灵图上小图个数</font><font style="color:#CF1322;">相同</font>
    - 添加无限重复效果

#### 多组动画
使用animation属性给一个元素添加多个动画效果

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1661067116205-e6df907f-025a-463a-914a-3ff25aa5ef6a.png)

##### 走马灯（无缝动画）
### CSS变量---全局定义&局部定义&使用var(变量名，默认值)
[https://juejin.cn/post/7152857013972631560](https://juejin.cn/post/7152857013972631560)

## 移动端
### 移动端特点
#### PC端网页与移动端网页有什么不同？
+ PC屏幕<font style="color:#CF1322;">大</font>，网页<font style="color:#CF1322;">固定版心</font>
+ 手机屏幕<font style="color:#CF1322;">小</font>，网页宽度多数为<font style="color:#CF1322;">100%（没有版心，直接充满）</font>

#### 如何在电脑里面边写代码边调试移动端网页效果？
- [x] 使用**<font style="color:#CF1322;">谷歌模拟器</font>**

#### 分辨率（物理分辨率和逻辑分辨率）
[移动web 第三天.pdf](https://www.yuque.com/attachments/yuque/0/2022/pdf/2587809/1661078013029-dc14ee41-7773-4b84-b3be-26f92fb5b549.pdf)

| 手机型号（熟悉） | 物理分辨率 | 逻辑分辨率 | 比例关系 |
| --- | --- | --- | --- |
| iPhone6/7/8 | 750*1334 | 375*667 | 2：1 |


屏幕尺寸指的是屏幕对角线的长度，一般用英寸来度量

- [x] <font style="color:#D46B08;">物理分辨率</font>是生产屏幕时就固定的，它是不可被改变的
- [x] <font style="color:#D46B08;">逻辑分辨率</font>是由软件（驱动）决定的

**<font style="color:#CF1322;">前端代码参考逻辑分辨率</font>**

#### 视口（移动端需要注意，这个meta重要）
目标：使用**<font style="color:#389E0D;">meta标签</font>**设置视口宽度，制作适配不同设备宽度的网页

默认情况下，网页的宽度和逻辑分辨率**<font style="color:#D4380D;">不相同</font>**，所以需要设置视口宽度=device-width

**目标：**网页宽度和逻辑分辨率（设备，此设备非彼设备）相同

**解决办法：**添加视口标签

如果注释掉meta标签，那么html的宽度会一直是980

#### 二倍图 （以二倍图为主，还有其他倍数的，目的是为了让网页中的图片不失真）
目标：能够使用像素大厨软件测量二倍图中元素的尺寸

我们书写代码都是基于逻辑分辨率，而逻辑分辨率相对于物理分辨率是有比例的，所以此时需要比例图，为了让图在屏幕上显示时不会模糊失真。

### 百分比布局（古老的布局方案）
目标：能够使用百分比布局开发网页

+ 百分比布局，也叫流式布局
+ 效果：<font style="color:#E8323C;">宽度自适应，高度固定</font>。

### Flex布局/弹性布局：（必须要有父级元素和子级元素）
目标：能够使用Flex布局模型<font style="color:#E8323C;">灵活、快速</font>的开发网页

可以完成浮动的效果，且比浮动更灵活（如flex没有清除浮动的困扰）

浏览器兼容性查询工具: [https://caniuse.com/](https://caniuse.com/)  (查询技术兼容和不兼容的浏览器版本）

- [x] 是一种<font style="color:#E8323C;">浏览器提倡</font>的<font style="color:#E8323C;">布局模型，相比浮动，网页性能更高，渲染更快</font>
- [x] 布局网页更<font style="color:#E8323C;">简单、灵活</font>
- [x] 避免<font style="color:#E8323C;">浮动脱标</font>的问题

#### Flex布局模型构成
作用：

+ 基于Flex精确灵活控制块级盒子的布局方式，<font style="color:#E8323C;">避免浮动布局中脱离文档流现象发生</font>
+ Flex布局非常适合结构化布局

设置方式

+ 父元素添加**<font style="color:#E8323C;">display：flex</font>**，子元素可以自动的挤压或拉伸
+ <font style="color:#08979C;">子元素设置宽高直接生效</font>

组成部分

+ 弹性容器
+ 弹性盒子（**<font style="color:#E8323C;">弹性盒子都是沿着主轴排列</font>**）
+ **<font style="color:#E8323C;">主轴（默认主轴在水平）</font>**
+ **<font style="color:#E8323C;">侧轴/交叉轴 </font>**

#### 主轴对齐方式
目标：使用**<font style="color:#389E0D;">justify-content</font>**调节元素**<font style="color:#CF1322;">在主轴的对齐方式</font>**

- [x] **修改主轴对齐方式属性：****<font style="color:#CF1322;">justify-content</font>**

| 属性值 | 作用 |
| :---: | :---: |
| flex-start | 默认值，起点开始依次排列 |
| flex-end | 终点开始依次排列 |
| **<font style="color:#CF1322;">center</font>** | <font style="color:#CF1322;">沿主轴居中排列</font> |
| **<font style="color:#CF1322;">space-around</font>** | 弹性盒子沿主轴<font style="color:#CF1322;">均匀排列</font>，空白部分间距均分在弹性盒子<font style="color:#CF1322;">两侧（每个子级两侧的距离是相等的）</font><br/>视觉效果（<font style="color:#E8323C;">子级之间的距离是父级两头距离的2倍</font>） |
| **<font style="color:#CF1322;">space-between</font>** | 弹性盒子沿主轴<font style="color:#CF1322;">均匀排列</font>，空白间距均分在相邻盒子<font style="color:#CF1322;">之间</font> |
| **<font style="color:#CF1322;">space-evenly</font>** | 弹性盒子沿主轴<font style="color:#CF1322;">均匀排列</font>，弹性盒子与容器之间<font style="color:#CF1322;">间距相等（所有地方的间距都相等）</font> |


#### 侧轴对齐方式
目标：使用**<font style="color:#389E0D;">align-items</font>**调节元素在**侧轴的对齐方式**

- [x] 修改侧轴对齐方式属性：
+ **<font style="color:#F5222D;">align-items</font>**（<font style="color:#08979C;">添加到弹性容器--</font>**<font style="color:#F5222D;">父级</font>**）
+ align-self：控制**<font style="color:#1D39C4;">某个弹性盒子</font>**在侧轴的对齐方式（<font style="color:#08979C;">添加到弹性盒子--</font>**<font style="color:#F5222D;">子级</font>**）

| 属性值 | 作用 |
| :---: | :---: |
| flex-start | 默认值，起点开始依次排列 |
| flex-end | 终点开始依次排列 |
| **<font style="color:#CF1322;">center</font>** | <font style="color:#CF1322;">沿侧轴居中排列</font> |
| **<font style="color:#CF1322;">stretch</font>** | **<font style="color:#F5222D;">默认值</font>**，弹性盒子沿着主轴线被**<font style="color:#F5222D;">拉伸</font>**至铺满（父级）容器，当子级设置了**<font style="color:#F5222D;">高度</font>**，则不会被拉伸 |


#### 伸缩比--flex：值；
目标：使用<font style="color:#F5222D;">flex属性</font>修改弹性盒子**<font style="color:#389E0D;">伸缩比</font>**

- [x] 属性：**<font style="color:#389E0D;">flex：值；</font>**
- [x] 取值分类：<font style="color:#F5222D;">数值</font>（整数）--表示占用父级剩余尺寸的份数

<font style="color:#F5222D;">注意：只占用父盒子剩余尺寸</font>

#### 小兔鲜儿--确认订单
##### lib文件夹，一般用来存放可以要从外部引入的文件，比如iconfont，一些库或者框架等
#### 修改主轴方向----<font style="color:#389E0D;">flex-direction</font>
使用flex-direction改变元素排列方向

+ 主轴默认是水平方向，侧轴默认是垂直方向
+ 修改主轴方向属性：flex-direction

| 属性值 | 作用 |
| :---: | :---: |
| row | 行，水平（默认值） |
| **<font style="color:#D4380D;">column</font>** | **<font style="color:#D4380D;">列，垂直</font>** |
| row-reverse | 行，从右向左 |
| column-reverse | 列，从上向下 |


#### flex实现水平居中效果：
将主轴对齐方式和侧轴对齐方式都设为居中：

justify-content: center;

align-items: center;

##### 先确定主轴对齐方式，再选择对应的属性实现主轴或者侧轴的对齐方式
#### 弹性盒子换行：<font style="color:#389E0D;">flex-wrap：wrap；（添加在弹性盒子的父级上）</font>
目标：使用flex-wrap实现弹性盒子多行排列效果

他的默认值是不换行

##### 调整行对齐方式：<font style="color:#389E0D;">align-content  （添加到父级）</font>
+ 取值与justyfi-content基本相同（space-evenly）

#### <font style="color:rgb(27, 27, 27);">text-overflow</font>
<font style="color:#08979C;">用于确定如何提示用户存在隐藏的溢出内容</font><font style="color:rgb(27, 27, 27);">。其形式可以是</font><font style="color:#389E0D;">裁剪</font><font style="color:rgb(27, 27, 27);">、显示一个</font><font style="color:#389E0D;">省略号（“…”）</font><font style="color:rgb(27, 27, 27);">或</font><font style="color:#389E0D;">显示一个自定义字符串</font><font style="color:rgb(27, 27, 27);">。</font>

| <font style="color:rgb(255, 255, 255);">值</font> | <font style="color:rgb(255, 255, 255);">描述</font> |
| --- | --- |
| <font style="color:rgb(51, 51, 51);">clip</font> | <font style="color:rgb(51, 51, 51);">剪切文本。</font> |
| <font style="color:rgb(51, 51, 51);">ellipsis</font> | <font style="color:rgb(51, 51, 51);">显示省略符号</font><font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);background-color:rgb(236, 234, 230);">...</font>**<font style="color:rgb(51, 51, 51);"> </font><font style="color:rgb(51, 51, 51);">来代表被修剪的文本。</font> |
| _<font style="color:rgb(51, 51, 51);">string</font>_ | <font style="color:rgb(51, 51, 51);">使用给定的字符串来代表被修剪的文本。</font> |
| <font style="color:rgb(51, 51, 51);">initial</font> | <font style="color:rgb(51, 51, 51);">设置为属性默认值。</font> |
| <font style="color:rgb(51, 51, 51);">inherit</font> | <font style="color:rgb(51, 51, 51);">从父元素继承该属性值。</font> |


<font style="color:rgb(27, 27, 27);">text-overflow 属性并不会强制“溢出”事件的发生，因此为了能让文本能够溢出容器，</font><font style="color:#CF1322;">你需要在元素上添加几个额外的属性</font><font style="color:rgb(27, 27, 27);">：</font>[overflow](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow)<font style="color:rgb(27, 27, 27);"> 和 </font>[white-space](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space)

+ overflow: hidden;   （溢出隐藏）
+ white-space: nowrap;  （不换行）<font style="color:rgb(51, 51, 51);">white-space属性指定元素内的空白怎样处理。</font>[white-space(学习）](https://www.runoob.com/cssref/pr-text-white-space.html)

### 移动适配
网页中任何元素的宽高都要保证能随着设备宽高的变化而等比缩放

**<font style="color:#389E0D;">实现在不同宽度的设备中，网页元素尺寸等比缩放效果</font>**

### rem
目标：能够使用<font style="color:#E8323C;">rem</font>**<font style="color:#E8323C;">单位</font>**设置网页元素的**尺寸**

网页效果

+ 屏幕<font style="color:#E8323C;">宽度不同</font>，网页元素<font style="color:#E8323C;">尺寸不同（等比缩放）</font>

PX 单位或者百分比布局可以实现吗？（px不行，百分比要确定高度）

##### rem单位（要先给html设置一个字号）
+ <font style="color:#E8323C;">相对</font>单位（根据别人去计算单位）
+ rem单位是相对于<font style="color:#E8323C;">HTML标签字号（根标签字号）</font>计算结果（网页的根是HTML标签）
+ **<font style="color:#E8323C;">1rem=1HTML字号大小</font>**

#### rem移动适配--媒体查询
目标：能够使用**<font style="color:#E8323C;">媒体查询</font>**设置**<font style="color:#E8323C;">差异化CSS</font>**样式

##### 手机屏幕大小不同，分辨率不同，如何设置不同的HTML标签字号？
+ **<font style="color:#E8323C;">媒体查询</font>**

**<font style="color:#E8323C;">媒体查询</font>**能够**<font style="color:#E8323C;">检测视口的宽度</font>**，然后编写**<font style="color:#E8323C;">差异化的CSS样式</font>**

- [x] 写法

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662168974891-0fd8b6db-ee0f-4894-9f81-696a80849a1a.png)



##### 设备宽度不同，HTML标签的字号设置多少合适？
- [x] 目前rem布局方案中，将网页等分成**<font style="color:#E8323C;">10份</font>**，HTML标签的字号为**<font style="color:#E8323C;">视口宽度的1/10</font>**

#### rem单位尺寸
1. 确定设计稿**<font style="color:#1D39C4;">对应的设备</font>**的**<font style="color:#1D39C4;">HTML标签字号</font>**
+ 查看**<font style="color:#389E0D;">设计稿宽度</font>**→确定**<font style="color:#389E0D;">参考设备宽度（视口宽度</font>**）→确定**<font style="color:#389E0D;">基准根字号</font>**（<font style="color:#CF1322;">1/10视口宽度</font>）
2. rem单位的尺寸
+ rem单位的尺寸=**<font style="color:#CF1322;">px单位数值/基准根字号</font>**

#### flexible
目标：使用flexible js配合rem实现在<font style="color:#CF1322;">不同宽度</font>的设备中，网页元素尺寸<font style="color:#CF1322;">等比缩放</font>效果

+ flexible.js 是手淘开发出的一个用来适配移动端的**<font style="color:#CF1322;">js框架</font>**
+ 核心原理就是根据**<font style="color:#CF1322;">不同视口宽度</font>**给网页中的<font style="color:#CF1322;">html</font>根节点设置不同的**<font style="color:#CF1322;">font-size</font>**

#### Less 
目标：使用**<font style="color:#CF1322;">Less语法</font>**<font style="color:#389E0D;">快速编译生成CSS代码</font>

+ Less是一个<font style="color:#CF1322;">CSS预处理器</font>，Less文件后缀是<font style="color:#CF1322;">.less</font>
+ 扩充了语言，使CSS具备一定的逻辑性、计算能力
+ <font style="color:#CF1322;">注意：浏览器不识别Less代码，目前阶段，网页要引入对应的CSS文件。</font>

##### Easy Less：
+ vscode插件
+ 作用：less文件保存自动生成.css文件

##### 注释：
1. 单行注释 （less中的单行注释不会显示在css文件中，因为css不支持双斜杠的注释方式）
+ 语法：//注释内容 
+ 快捷键：ctrl+/
2. 块注释
+ 快捷键：shift+alt+A

##### 计算----less4.0要求除法要放到小括号里面写（4.0之前的没要求），其他加减乘直接写
##### 嵌套
目标：能够使用Less嵌套写法生成后代选择器

嵌套：

+ 快速生成后代选择器

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662168847333-54b03f82-4ddd-4aca-8f92-3dc89efd3cac.png)           ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662168847334-2e58e9fa-0d89-4a88-8bde-2371a92fdfb7.png)                ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662168847332-c7c12e3d-5ecb-452e-90fa-ed9be5ff7cb6.png)



##### Less语法--变量
目标：能够使用**<font style="color:#E8323C;">Less</font>**变量设置**<font style="color:#E8323C;">属性值</font>**

变量

1. 把颜色提前存储到一个容器，设置属性值为这个容器名
2. 变量：**<font style="color:#096DD9;">存储数据，方便使用和修改</font>**
3. 语法
+ 定义变量：**<font style="color:#E8323C;">@变量名：值；</font>**
+ 使用变量：**<font style="color:#E8323C;">css属性：@变量名;</font>**

rem移动适配：根字号变量

##### Less 引入公共样式文件
目标：能够使用**<font style="color:#096DD9;">Less导入写法引用其他Less文件</font>**

- [x] 导入: **<font style="color:#389E0D;">@import“文件路径”；（一般加在开头，import后面要加空格）</font>**

如果导入的是less文件，可以省略后缀

##### Less导出css文件
- [x] 方法一：配置EasyLess插件（指定所有的less 文件导出的地方）

vscode设置 → 搜索Easy → 在setting文件中打开 → 在less.compile中写导出路径（out:"路径"）

- [x] 方法二：在每个less文件的**<font style="color:#D46B08;">第一行写</font>**：（可以指定该文件的导出路径以及导出名字）

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662170523919-f7dedd50-3742-454f-b6bc-3c47be7143ae.png)

##### 禁止导出
- [x] 在less文件**<font style="color:#D46B08;">第一行</font>**添加：//out: false  

### vw  、vh移动适配  
目标：实现在不同宽度的设备中，网页元素尺寸等比缩放效果   

#### vw/vh单位尺寸  
1. 确定<font style="color:#E8323C;">设计稿对应</font>的vm尺寸（**<font style="color:#E8323C;">1/100视口宽度</font>**）  
+ 查看设计稿宽度→ 确定参考设备宽度（视口宽度）→ 确定vw尺寸（1/100视口宽度）
2. vw单位的尺寸=**<font style="color:#E8323C;">px单位数值/</font>**(1/100视口宽度）--**<font style="color:#389E0D;">除以vw或者vh的结果一样！！</font>**
3. **<font style="color:#389E0D;">宽和高不能一个用vw一个用vh，因为这样在切换不同比例的设备时，盒子比例会不一样，会变型</font>**

变量：@vm

### 响应式
一套代码能够兼容不同的屏幕设备，适配不同的屏幕设备，展现不同但兼容的布局效果

#### 媒体查询
媒体特性主要用来描述<font style="color:#D4380D;">媒体类型的具体特征</font>，如当前屏幕的宽高、分辨率、横屏或竖屏。

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662291226770-c32f9d4a-bfef-43bf-aab5-e5a8dd171e35.png)

目标：能够根据设宽度的变化，设置差异化css样式（包括html）

**<font style="color:#E8323C;">所有的css样式都有层叠性</font>**

- [x] **<font style="color:#389E0D;">max-width</font>**<font style="color:#D4380D;">（从大到小按顺序书写）</font>
- [x] **<font style="color:#389E0D;">mini-width</font>**（<font style="color:#D4380D;">从小到大按顺序书写）</font>

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662291239086-7ab59662-5fbf-40e8-b26a-095df4f3e33e.png)

##### link写法
+ 外链式css引入

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662295508846-78f4f1da-1f20-4aa4-baf0-8ed0a88fc010.png)

隐藏：display：none；

#### BootStrap---做响应式网页的框架
目标：使用**<font style="color:#D4380D;">BootStrap</font>**框架**<font style="color:#D4380D;">快速</font>**开发**<font style="color:#D4380D;">响应式</font>**网页

[移动web 第7天.pdf](https://www.yuque.com/attachments/yuque/0/2022/pdf/2587809/1662296671259-188bfc2e-85b0-4d4c-af54-31b07ec6c10b.pdf)

##### 使用步骤
1. 官网下载、引入BootStrap提供的样式（css文件）
2. 调用类：使用BootStrap提供的样式
+ container：响应式布局版心类

##### 栅格系统
目标：使用BootStrap栅格系统**<font style="color:#E8323C;">布局</font>**响应式网页

+ 栅格化是指将整个网页的宽度等分若干等分
+ BootStrap3默认把网页等分成**<font style="color:#E8323C;">12等份</font>**
- [x] **<font style="color:#096DD9;">下图中 的类前缀要记住-------*表示的是12份中的几份，自己按需填数字</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662378105887-302d2876-836e-4f45-b0a7-0a33543dd59c.png)

BootStrap3用float实现div盒子在一行排，因为float的兼容性好，flex不兼容低版本的浏览器

##### container
- [x] **<font style="color:#D4380D;">.container</font>** 是Bootstrap中专门提供的类名，所有应用该类名的盒子，默认已被指定宽度且居中
- [x]  **<font style="color:#D4380D;">.container-fluid</font>**也是Bootstrap中专门提供的类名，所有应用该类名的盒子，宽度均为100%
- [x] 分别使用**<font style="color:#D4380D;">.row</font>**类名和**<font style="color:#D4380D;">.col</font>**类名定义栅格布局的行和列，col自带15px的左右padding

注意：

1. container类自带间距15px；
2. row类自带间距-15px（row类要写在container里面，作为他的子级调用可以抵消container的15px ）

##### 全局样式
目标：掌握Bootstrap手册，使用<font style="color:#D4380D;">全局css样式</font>美化标签

网站首页(bootcss.com) → Bootstrap3中文文档 → <font style="color:#D4380D;">全局css样式</font> → 按<font style="color:#D4380D;">分类导航</font>查找目标类

##### <font style="color:rgb(51, 51, 51);">Glyphicons 字体图标---和iconfont字体图标的使用方法一样，引用+两个类名（两个都直接复制即可）</font>
##### 插件
目标：使用Bootstrap插件实现常见的**<font style="color:#D4380D;">交互效果</font>**

- [x] 插件使用步骤
+ 引入Bootstrap样式（也就是css样式表）
+ 引入js文件：jQuery.js + Bootstrap.min.js （用script标签引入）
+ 复制HTML结构，调节内容

#### 企业网站或者是内容非常少的网站适合改版成响应式，内容多的比如电商站不适合
电商站：pc端是一个网站，移动端是一个网站要分开开发

### 实战演练
#### flex实现长文字后面省略号
+ text-overflow：ellipsis；
+ white-space：nowrap；
+ overflow：hidden；

然后再给文字限制一个宽度，不然弹性盒子会拉伸，不生效

也可以：（此法相当于给文字设置了一个宽度）

+ width：0；
+ flex：1

移动端是没有hover的，因为没有箭头

#### 实现在不同宽度设备中等比缩放网页效果
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1662212103620-03eebbb6-d49b-46ac-85c9-7fddc0c1fd0b.jpeg)

因为如果给盒子设置具体的宽高的话，在不同的设备中会出现不一样的问题？？（可是不是适配了吗？）

## 问题
### 1、href 、src、url
[解释链接](https://blog.csdn.net/qq_40695234/article/details/125901543?utm_medium=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-125901543-blog-null.pc_404_mixedpudn&depth_1-utm_source=distribute.pc_feed_404.none-task-blog-2~default~BlogCommendFromBaidu~Rate-1-125901543-blog-null.pc_404_mixedpud)

#### 一种写法：鼠标移入box，before向左移动100%： .box:hover::before {transform: translateX（100%）
#### HTML中一般用i标签放小图标
#### 数据都是来自于后台，只有加了标签才能换数据
- [x] html中换行写的块级元素之间会有小间距
- [ ] 

