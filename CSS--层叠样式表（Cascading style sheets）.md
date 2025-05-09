# 基础认知
## 1、初识：css决定样式美观
### 1.1css语法规则
+ **css写在****<font style="color:#389E0D;">style标签</font>****中，style标签一般写在****<font style="color:#389E0D;">head标签里</font>****，****<font style="color:#389E0D;">title标签下面（最简单的一种写法）</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1650894200046-e2467975-9928-40e0-9b11-64cc1f1d3246.png)

+ **<font style="color:#F5222D;">选择器就是你想改变的html标签--p就表示body里的p段落</font>**
+ **CSS注释，同html：contrl+/**

### 1.2 CSS引入方式
#### 内嵌式：CSS写在<font style="color:#389E0D;">style</font>标签中
+ style标签虽然可以写在页面任意位置，但是通常约定写在**<font style="color:#389E0D;">head</font>**标签中

#### 外联式：CSS写在一个<font style="color:#389E0D;">单独的.css文件</font>中
+ 提示：需要通过**<font style="color:#389E0D;">link标签</font>**在网页中引入

#### 行内式：CSS写在标签的<font style="color:#C41D7F;">style属性</font>中---只能控制该单个标签（实际中比较少用）
+ 配合js使用

| 引入方式 | 书写位置 | 作用范围 | 使用场景 |
| :---: | :---: | :---: | :---: |
| 内嵌式 | head标签 | 当前页面 | 小案例 |
| **外联式** | 单独的CSS文件 | **多个页面** | **项目中** |
| 行内式 | 标签的style属性内 | 当前标签 | 配和js使用 |


### 1.3 基础选择器
理解选择器的作用，能够使用基础选择器在HTML中选择元素

**作用：选择页面中对应的标签，方便后续设置样式**

#### 1.3.1 标签选择器--<font style="color:#CF1322;">标签名{CSS属性名：属性值；}</font>
作用：通过标签名，找到页面中**<font style="color:#389E0D;">所有</font>**这类标签，设置样式

注意点：

+ **标签选择器选择的是一类标签，而不是单独某一个**
+ 标签选择器无论嵌套关系有多深，都能找到对应到的标签

#### 1.3.2 类选择器-- <font style="color:#D4380D;">.类名{css属性名：属性值；}</font>
作用：通过类名，找到页面中所有带有这个类名的标签，设置样式

注意点：

+ 所有标签上都有**<font style="color:#C41D7F;">class属性</font>**，<font style="color:#C41D7F;">class属性的属性值为类名（类似于名字）</font>
+ 类名可以有**<font style="color:#C41D7F;">数字、字母、下划线、、中划线</font>**组成，但**<font style="color:#096DD9;">不能以数字或者中划线</font>**开头
+ **一个标签可以同时有多个类名，类名之间以空格隔开**
+ **类名可以重复，一个类选择器可以同时选中多个标签**

#### 1.3.3 id选择器--<font style="color:#D4380D;">#id属性值{css属性名：属性值；}</font><font style="color:#C41D7F;">----本身不是用于控制CSS样式效果，而是多用于配合js</font>
作用：通过id属性值，找到页面中带有这个id属性值的标签，设置样式

注意点：

+ 所有标签上都有**id属性--id=“”**
+ id属性类似于身份证号码，**<font style="color:#389E0D;">在一个页面中是唯一</font>**的，**<font style="color:#D4380D;">不可重复的！</font>**
+ 一个标签上只能有一个id属性值
+ 一个id选择器只能选中一个标签

#### 1.3.4 通配符选择器--*{css属性名：属性值；}
作用：找到**<font style="color:#D4380D;">页面中所有的标签</font>**，设置样式

注意点：zdf	

+ 在开发中使用极少，只会在极特殊情况下才会用到	
+ **<font style="color:#389E0D;">可能会用于去除标签默认的margin和padding--默认边距</font>**（后续讲解）

#### 1.3.5 <font style="color:rgb(51, 51, 51) !important;">CSS [attribute="value"]选择器</font>
[一篇文章带你了解 CSS 属性选择器-51CTO.COM](https://www.51cto.com/article/758928.html)

### 1.4字体和文本样式
能够使用字体和文本相关样式修改元素外观样式

#### 1.4.1 字体样式
1. **字体大小：****<font style="color:#C41D7F;">font-size</font>**
+ 取值：**<font style="color:#389E0D;">数字+px</font>**
+ 谷歌浏览器默认文字大小是**<font style="color:#389E0D;">16px</font>****<font style="color:#C41D7F;"></font>**
+ 单位需要设置，否则无效
2. **字体粗细：****<font style="color:#C41D7F;">font-weight</font>**
+ 取值
    - **关键字**

| 正常 | **normal** |
| :---: | :---: |
| 加粗 | **bold** |


    - **纯数字：100-900的整百数**

| 正常 | **<font style="color:#389E0D;">400</font>** |
| :---: | :---: |
| 加粗 | **<font style="color:#389E0D;">700</font>** |


+ 不是所有字体都提供了9中粗细，因此部分取值页面中无变化
+ **实际开发中以：****<font style="color:#389E0D;">正常、加粗</font>****两种取值使用最多，更多使用****<font style="color:#C41D7F;">纯数字</font>****来设置**
3. **字体样式：****<font style="color:#C41D7F;">font-style</font>**
+ 正常（默认值）：**normal**
+ 倾斜：**italic**
4. **字体类型：****<font style="color:#C41D7F;">font-family</font>**
+ 常见取值：具体字体1，具体字体2，具体字体3，具体字体4......字体系列
    - **具体字体**：“Microsoft YaHei”、微软雅黑、黑体、宋体、楷体等....
    - **字体系列**：sans-self、serif、monospace等
+ **<font style="color:#389E0D;">渲染规则</font>**
    - **从左往右按顺序查找，如果电脑中为安装该字体，则显示下一个字体**
    - **如果都不支持，此时会根据操作系统，显示最后****<font style="color:#389E0D;">字体系列</font>****的默认字体**
+ 如果字体名称中存在多个单词，推荐使用引号包裹
+ **<font style="color:#08979C;">最后一项字体系列不需要引号包裹</font>**
+ 网页开发时，尽量使用系统常见自带字体，保证不同用户浏览网页都可以正确显示
+ windows电脑字体默认**微软雅黑**、mac默认**苹方字体**
+ **现在的网页一般用的都是像微软雅黑这样比较规整的字体**

#### 1.4.2 常见字体类型系列（了解）
+ **<font style="color:#389E0D;">无衬线字体（sans-serif）--英文表示这一系列字体</font>**
    1. 特点：文字笔画粗细均匀，并且首尾无装饰
    2. 场景：<font style="color:#389E0D;">网页中大多采用无衬线字体</font>
    3. 常见该系列字体：<font style="color:#389E0D;">黑体、Arial</font>
+ **衬线字体（serif）**
    1. 特点：文字笔画粗细不均，并且首尾有笔锋装饰
    2. 场景：<font style="color:#389E0D;">报刊书籍中应用广泛</font>
    3. 常见该系列字体：<font style="color:#389E0D;">宋体、Times New Roman</font>
+ **等宽字体（monospace）**
    - 特点：<font style="color:#08979C;">每个字母或文字的宽度相等</font>
    - 场景：一般用于程序代码编写，有利于代码的阅读和编写
    - 常见该系列字体：：<font style="color:#08979C;">Consolas、fira code</font>

#### 1.4.3 样式的层叠问题
如果给同一个标签设置了相同的样式，此时浏览器会如何渲染呢？

+ **<font style="color:#389E0D;">如果给同一个标签设置了相同的属性，此时样式会层叠覆盖，写在最下面的会生效</font>**
+ css--层叠样式表--表示样式可以一层一层的层叠覆盖

#### 1.4.4 字体font相关属性的连写（复合属性）
- [x] **属性名：font**

取值：**<font style="color:#389E0D;">font：style weight size family；</font>**

省略要求：**只能省略前两个，如果省略了相当于设置了默认值，按顺序设置的**

注意点：如果需要**同时设置单独和连写形式**

+ 要么把单独的样式写在连写的**<font style="color:#389E0D;">下面</font>**
+ 要么把单独的样式写在连写的**<font style="color:#389E0D;">里面</font>**

#### 1.4.5 文本样式
- [x] **文本缩进属性：text-indent**

取值：

    1. 数字+px
    2. **<font style="color:#389E0D;">数字+em（推荐，1em=当前标签的font-size的大小）</font>**
- [x] **文本水平对齐方式属性：text-align（内容对齐方式）**

取值：

| 属性值 | 效果 |
| :---: | :---: |
| **left** | **左对齐** |
| **center** | **居中对齐** |
| **right** | **右对齐** |


text-align：center能让哪些元素**水平居中**？

1. **文本**
2. **span标签、a标签**
3. **input标签、img标签**

注意点：如果需要让以上元素**<font style="color:#D4380D;">水平居中</font>**，text-align属性给**<font style="color:#D4380D;">以上元素的所在标签（文本的父元素</font>**）设置

#### 1.4.6 文本修饰
- [x] **text-decoration**
- [x] 取值：

| 属性值 | 效果 |
| :---: | :---: |
| **underline** | **下划线（常用）** |
| **line-through** | **删除线（不常用）** |
| **overline** | **上划线（几乎不用）** |
| **none** | **无装饰线（常用）** |


注意点：

+ 在开发中会使用**<font style="color:#389E0D;">text-decoration：none；</font>****清除a标签默认的下划线**

#### 1.4.3 行高--控制一行的上下间距（只要是文本都可以控制！！！不论是啥标签，比如a标签都可！）
- [x] **line-height**

取值

+ 数字+px  （行高=上间距+文本高度+下间距）
+ 倍数（当前标签font-size的倍数）

应用：

+ 让**<font style="color:#E8323C;">单行文本垂直居中</font>**可以 设置**<font style="color:#E8323C;">line-height：文字父元素高度</font>**
+ 网页精准布局时，会设置**<font style="color:#E8323C;">line-height：1</font>**<font style="color:#E8323C;"> </font>**<font style="color:#E8323C;">可以取消上下间距</font>**

行高与font连写的注意点：

+ 如果同时设置了行高和font连写，注意<font style="color:#E8323C;">覆盖问题</font>
+ **font：style weight size****<font style="color:#389E0D;">/</font>****line-height family；**

#### 颜色常见取值（了解）
- [x] 如，文字颜色：color
- [x] 如：背景颜色：background-color

属性值：

| 颜色表示方式 | 表示含义 | 属性值 |
| --- | --- | --- |
| 关键词 | 预定义的颜色名 | red、green、blue、yellow... |
| rgb表示法 | 红绿蓝三原色，每项取值范围是0-255 | rgb(0,0,0)、rgb(255,255,255)... |
| rgba表示法 | 红绿蓝三原色+a表示透明度，取值范围是0-1 | rgba(255,255,255,0.5)... |
| 十六进制表示法 | #开头，将数字转换成十六进制表示 | #000000,#ff0000... |


### 标签水平居中方法总结 margin: 0 auto
如果需要让div、p、h（大盒子）水平居中？

+ 可以通过margin：0 auto；实现

注意点：

+ 如果需要让div、p、h（大盒子）水平居中，直接给当前元素本身设置即可
+ margin：0 auto 一般针对要固定宽度的盒子，如果大盒子没有设置宽度，此时会默认占满父元素的宽度                                                                                             

### chrome调试工具
#### 谷歌浏览器网页鼠标右击--检查，出现调试页面，根据需要调试
# CSS进阶
## 1、选择器进阶
目标：能够理解复合选择器的规则，并**使用复合选择器在HTML中选择元素**

### 1.1 复合选择器
#### 1.1.1 后代选择器<font style="color:#F5222D;">：空格</font>
作用：根据HTML标签的嵌套关系，选择**父元素****<font style="color:#E8323C;">后代中</font>**满足条件的元素

选择器语法：**<font style="color:#E8323C;">选择器1 选择器2{css}</font>**

结果：

+ 在选择器1所找到标签的后代（儿子、孙子、重孙子。。。）中，找到满足选择器2的标签，设置样式

注意点：

+ 后代包括：儿子、孙子、重孙子。。。
+ 后代选择器中，选择器与选择器之间通过**<font style="color:#F5222D;">空格</font>**隔开

#### 1.1.2 子代选择器：<font style="color:#F5222D;">></font>  （<font style="color:#F5222D;">选择器1>选择器2{CSS}</font>）
作用：根据HTML标签的嵌套关系，选择**父元素****<font style="color:#F5222D;">子代中</font>**满足条件的元素

结果：在选择器1所找到标签的子代（儿子）中，找到满足选择器2的标签，设置样式

注意点：

1. 子代只包括：儿子
2. 子代选择器中，选择器与选择器之间通过**<font style="color:#F5222D;">></font>**隔开

### 1.2 并集选择 ：<font style="color:#F5222D;"> 选择器1，选择器2{CSS}</font>
作用：**同时选择多组标签，设置相同的样式**

结果：找到选择器1和选择器2选中的标签，设置样式

注意点：

1. 并集选择器中的每组选择器之间通过**<font style="color:#F5222D;">，</font>**分离
2. **并集选择器中的每组选择器可以是基础选择器或者复合选择器**
3. **并集选择器中的每组选择器通常一行写一个**，提高代码的可读性

### 1.3 交集选择器：紧挨着 <font style="color:#F5222D;">选择器1选择器2{css}</font>
作用：选中页面 同时满足多个选择器的标签

结果：（<font style="color:#F5222D;">既又原则</font>）找到页面中**既能被选择器1选中**，**又能被选择器2选中**的标签，设置样式

注意点：

1. 交集选择器中的选择器是紧挨着的，没有东西分隔
2. **交集选择器中如果有标签选择器，标签选择器必须写在最前面**

### 1.4 hover伪类选择器：<font style="color:#F5222D;">选择器：hover{css}</font>
作用：选中鼠标悬停在元素上的状态，设置样式

注意点：<font style="color:#F5222D;">伪类选择器中的元素的某种状态，</font><font style="color:#389E0D;">任何一个标签都可以添加伪类</font>

### 1.5 Emmet语法
作用：通过简写语法，快速生成代码

语法：类似于刚刚学习的选择器的写法          

| 记忆 | 示例 | 效果 |
| --- | --- | --- |
| 标签名 | div | <div></div> |
| 同级 | div<font style="color:#F5222D;">+</font>p | <font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">div</font><font style="color:#808080;background-color:#1e1e1e;">></</font><font style="color:#569cd6;background-color:#1e1e1e;">div</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">p</font><font style="color:#808080;background-color:#1e1e1e;">></</font><font style="color:#569cd6;background-color:#1e1e1e;">p</font><font style="color:#808080;background-color:#1e1e1e;">></font> |
| 类选择器 | <font style="color:#F5222D;">.</font>red  | <divclass="red"></div> |
| id选择器 | **<font style="color:#F5222D;">#</font>**one | <divid="one"></div> |
| 交集选择器 | p.red#one | <pclass="red"id="one"></p> |
| 子代选择器 | ul**<font style="color:#F5222D;">></font>**li | <ul><br/>        <li></li><br/>    </ul> |
| 内部文本(父子级）只要是创建父子级关系的都可以用这个 | ul>li**<font style="color:#F5222D;">{我是li的内容}</font>** | <font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><font style="color:#d4d4d4;background-color:#1e1e1e;">我是li的内容</font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font> |
| 创建多个 | ul>li**<font style="color:#F5222D;">*</font>**3 | <font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font> |
| $将每个子集的内容分别按顺序设为1,2,3 | ul>li{**<font style="color:#F5222D;">$</font>**}*2 | <font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><font style="color:#d4d4d4;background-color:#1e1e1e;">1</font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">        </font><font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><font style="color:#d4d4d4;background-color:#1e1e1e;">2</font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">li</font><font style="color:#808080;background-color:#1e1e1e;">></font><br/><font style="color:#d4d4d4;background-color:#1e1e1e;">    </font><font style="color:#808080;background-color:#1e1e1e;"></</font><font style="color:#569cd6;background-color:#1e1e1e;">ul</font><font style="color:#808080;background-color:#1e1e1e;">></font> |


**<font style="color:#F5222D;">css里也可以用这种简写语法，可以提示css属性：单词的首字母</font>**

## 2、背景相关属性
**能够使用背景相关属性装饰元素的背景样式**

### 2.1背景颜色 : <font style="color:#F5222D;">background-color (bgc)</font>
颜色取值：关键字、rgb表示法、rgba表示法、十六进制。。。。

注意点：

+ 背景颜色默认是透明：rgb（0,0,0,0）、transparent
+ 背景颜色不会影响到盒子大小，并且还能看清盒子的大小和位置，**一般在布局中会先习惯给盒子设置背景颜色**

### 2.2 背景图片 background-image（bgi）
#### 属性值：<font style="color:#F5222D;">background-image：url（‘图片的路径’）</font>
注意点：

+ 背景图片中**<font style="color:#389E0D;">url可以省略引号</font>**
+ 背景图片默认是在**<font style="color:#389E0D;">水平和垂直方向平铺的</font>**
+ 背景图片仅仅是指给盒子起到装饰效果，**<font style="color:#389E0D;">类似于背景颜色，是不能撑开盒子的</font>**

### 2.3 背景平铺 <font style="color:#389E0D;">background-repeat(bgr)</font>
#### 属性值：
+ **<font style="color:#389E0D;">repeat：</font>**（默认值）水平和垂直方向都平铺
+ **<font style="color:#389E0D;">no-repeat：</font>**不平铺（图片只显示一个）
+ **<font style="color:#389E0D;">repeat-x：</font>**沿着水平方向（x轴）平铺
+ **<font style="color:#389E0D;">repeat-y：</font>**沿着垂直方向（y轴）平铺

### 2.4 背景位置 ：<font style="color:#389E0D;">background-position</font>(bgp)
#### 属性值：<font style="color:#389E0D;">background-position：水平方向位置 垂直方向位置；</font>
![画板](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1652607828751-d28c756c-34c9-4bfd-8478-1c4e421da742.jpeg)

**取值为****<font style="color:#CF1322;">正数</font>****：****<font style="color:#CF1322;">图片向右向下</font>****移动；****<font style="color:#CF1322;">负数</font>****：****<font style="color:#CF1322;">图片向左向上</font>****移动。**

#### background-image：right 0；（表示只显示图片右半部分）
背景图和背景色只显示在盒子里

#### 背景图位置如果是英文单词可以颠倒顺序，结果不变；但如果是数字px则不能颠倒，效果会改变
#### 注意点：方位名词取值和坐标取值可以混使用，第一个取值表示水平，第二个取值表示垂直
### 2.5 背景图片大小---也可以用来调整背景颜色面积？
作用：设置背景图片的大小

- [x] 语法：**<font style="color:#389E0D;">background-size: 宽度 高度；</font>**

取值：

| **属性值** | **效果** |
| :---: | :---: |
| **<font style="color:#1D39C4;">数字+px</font>** | 简单方便，常用 |
| **<font style="color:#1D39C4;">百分比</font>** | 相对于当前盒子自身的宽高百分比 |
| **<font style="color:#1D39C4;">contain</font>** | 包含，将背景图片**等比缩放**，直到不能超出盒子（可能会出现空白） |
| **<font style="color:#1D39C4;">cover</font>** | 覆盖，将背景图片**等比缩放**，直到**刚好填满整个盒子没有空白** |


### 2.6 背景相关属性连写  background(bg)-----称为复合属性
#### 属性值：单个属性的和谐，取值之间以空格隔开
- [x] **<font style="color:#389E0D;">background：color image repeat position/size;</font>****（工作中一般单独写position，推荐按该顺序写，**但实际上可以不分先后顺序）
- [x] 还可以写一个**<font style="color:#389E0D;">attachment</font>**属性，表示背景图片附着，不随滚动而滚动

#### 省略问题：
+ 可以按照需求省略
+ 特殊情况**：在pc端，如果盒子大小和背景图片大小一样，此时可以直接写background：url（）**

#### 注意点：
+ background-size和background连写同时设置时，需要注意覆盖问题
+ 如果需要设置单独的样式和连写
+ ①**要么把单独的样式写在连写的下面**
+ ②**要么把单独的样式写在连写的里面**

### 2.6 （拓展）img标签和背景图片的区别
#### 需求：需要在网页中展示一张图片的效果？
#### 方法一：直接写上img标签即可
+ img标签是一个标签，不设置宽高默认会以原尺寸显示

#### 方法二：div标签+背景图片
+ 需要设置div的宽高，因为背景图只是装饰的css样式，不能撑开div标签

#### img标签在工作中用来显示比较重要的图片！
#### 装饰性的，不重要的图用背景图！
## 3、元素显示模式
目标：能够认识**三种常见的元素显示模式**，并通过代码实现不同元素显示模式的**转换**

### 3.1 块级元素（block）
#### 显示特点：
1. **独占一行（一行只能显示一个）**
2. **宽度默认是父元素的宽度，高度默认由内容撑开**
3. **<font style="color:#F5222D;">可以设置宽高</font>**

#### 代表标签：
+ **div、p、h系列**、ul、li、dl、dt、dd、form、header、nav、footer......

### 3.2 行内元素（inline）
#### 显示特点：
+ **一行可以显示多个**
+ **宽度和高度默认由内容撑开**
+ **<font style="color:#E8323C;">不可以设置宽高</font>**

#### 代表标签
+ **a、span**、b、u、i、s、strong、ins、em、del.......

### 3.4 行内块元素（inline-block）兼具上述两种显示模式的特点
#### 显示特点：
1. 一行可以显示多个
2. 可以设置宽高（block），<font style="color:rgba(0, 0, 0, 0.75);">默认宽度是本身内容的宽度（inline）</font>
3. <font style="color:rgba(0, 0, 0, 0.75);"><img />、<input />、<td></font>

#### 代表标签：
+ **img 、input、textarea**、button、td、select.....
+ 特殊情况：img标签有行内块元素特点，但是Chrome调试工具显示结果是inline

#### 注意点：
<font style="color:rgb(77, 77, 77);">如果元素是</font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">inline-block</font><font style="color:rgb(77, 77, 77);">或</font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">inline</font><font style="color:rgb(77, 77, 77);"> 他们默认宽度已经固定了，不是独占一行的，那么左右外边距为auto，是没有办法自动调整为居中的，margin：0 auto；只能让</font>**<font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">block</font>**<font style="color:rgb(77, 77, 77);">元素居中----</font>**<font style="color:#DF2A3F;">为啥呢？？</font>**

### 3.5 元素显示模式转换
#### 目标：改变元素默认的显示特点，让元素符合布局要求
#### 语法
| 属性 | 效果 | 使用频率 |
| --- | --- | --- |
| **<font style="color:#389E0D;">display:block</font>** | 转换成**块级元素** | **较多** |
| **<font style="color:#389E0D;">display:inline-block</font>** | 转换成**行内块元素** | **较多** |
| **<font style="color:#389E0D;">display:inline</font>** | 转换成**行内元素** | 极少 |


### 拓展1：HTML嵌套规范注意点
#### 1、块级元素一般作为大容器，可以嵌套：文本、块级元素、行内元素、行内块元素等等....
- [x] **<font style="color:#531DAB;">但是：P标签中不要嵌套div、p、h等块级元素</font>**

#### 2、a标签内部可以嵌套任意元素
- [x] **<font style="color:#531DAB;">但是：a标签不能嵌套a标签</font>**

# 4、CSS三大特性
#### 目标：能够认识不同选择器的优先级公式，能够进行CSS权重叠加计算，分析并解决css冲突问题
## 4.1继承性
#### 特性：子元素有默认集成父元素样式的特点（子承父业）
#### 可以继承的常见属性（<font style="color:#F5222D;">文字控制属性</font>都可以集成）
1. color
2. font-style、font-weight、gont-size、font-family
3. text-indent、text-align
4. line-height
5. ......

#### 注意点：可以通过调试工具判断样式是否可以继承(<font style="color:#389E0D;">inherited</font>--集成)
#### （拓展）继承失效的特殊情况：<font style="color:#E8323C;">如果元素有</font><font style="color:#389E0D;">浏览器默认样式</font><font style="color:#E8323C;">，此时继承性仍然存在，但是</font><font style="color:#389E0D;">优先显示浏览器的默认样式</font>（子标签自己本身有的属性就不会继承父类的这个属性）
如：

1. a标签的color会继承失效
2. h系列标签的font-size会继承失效

## 4.2 层叠性
#### 特性：
1.  给同一个标签设置不同的样式--此时样式会层叠叠加--会共同作用在标签上
2. 给同一个标签设置相同的样式--此时样式会层叠覆盖--最终写在最后的样式会生效

#### 注意点：
+ **当样式冲突时，只有当****<font style="color:#F5222D;">选择器优先级相同</font>****时，才能通过层叠性判断结果**

## 4.3 优先级
#### 特性：不同选择器具有不同的优先级，<font style="color:#389E0D;">优先级高的选择器样式会覆盖优先级低的选择器样式</font>
#### 优先级公式：
#### <font style="color:#F5222D;">继承<通配符选择器<标签选择器<类选择器<id选择器<行内样式<!important（谁的能选择的范围越广，谁的优先级就最低）</font>
#### 注意点：
1. **<font style="color:#389E0D;">！important写在属性值的后面，分号的前面！--CSS里写</font>**
2. ！important**不能提升继承的优先级**，**只要是继承那优先级就最低**
3. 实际开发中不建议使用！important

## 4.4 权重叠加计算
当用多个方式来选择某个标签时，判断哪个生效，就要进行权重叠加计算比较！！

#### 场景：如果是<font style="color:#F5222D;">复合选择器</font>，此时需要通过<font style="color:#389E0D;">权重叠加计算方法</font>，<font style="color:#F5222D;">判断最终哪个选择器优先级最高会生效</font>
#### 权重叠加计算公式：（每一级之间不存在进位）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1653400512221-03043f25-46b5-4b9f-a8a1-fe0a682daeba.png)

#### 比较规则：（<font style="color:#F5222D;">按照级别，比较个数</font>）<font style="color:#F5222D;background-color:#FFFB8F;">行内，id、类选择器、标签选择器</font>
1. 先比较第一级**<font style="color:#F5222D;">数字</font>**，如果比较出来了，之后的统统不看
2. 如果第一级数字相同，此时再去比较第二级数字，如果比较出来了，之后的统统不看
3. 。。。。。。
4. 如果最终所有数字都相同，表示优先级相同，则比价层叠性（谁写在下面，谁说了算！）
5. **<font style="color:#003A8C;">如果都是继承，看文字继承哪个父级，哪个父级近，就继承哪个！！（就近原则）</font>**

#### 注意点：！important如果不是继承，则权重最高，天下第一（实际开发中慎重使用！important）
## （拓展）谷歌浏览器查错
### 遇到样式出不来，要学会通过调试工具找错
![画板](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1653404581006-6301adc6-af4a-4105-a109-ac78317f7013.jpeg)

+ ；浏览器检查中出现“黄色叹号”说明是语法出错

## PXCOOK（图片格式用设计模式，psd格式用开发模式）
## 盒子模型（专业布局）
### 1、概念
1. 页面中的**每一个标签都可以看作是一个“盒子”**，通过盒子的视角更方便地进行布局
2. 浏览器在渲染（显示）网页时，会将网页中的元素看作是一个个的矩形区域，我们也形象地称之为盒子

### 2、盒子模型
CSS中规定每个盒子分别由：**<font style="color:#E8323C;">内容区域（content）</font>**、**<font style="color:#E8323C;">内边距区域（padding）</font>**、**<font style="color:#E8323C;">边框区域（border）</font>**、**<font style="color:#E8323C;">外边距区域（margin）</font>**构成，这就是**<font style="color:#E8323C;">盒子模型</font>**

记忆：可以联想现实中的包装盒

#### 2.1 内容的宽度和高度
+ 作用：利用width和height属性默认设置是盒子内容区域的大小
+ 属性：width / height
+ 常见取值：数字+px

#### 2.2 边框（border）--连写形式
+ 属性名：border
+ 属性值：单个取值的连写，取值之间以空格隔开
    - 如：border：10px solid red： （不分先后顺序，solid表示线条的种类，实线或者虚线之类的）
+ 快捷键： bd +tab
- [x] 实线：solid 
- [x] 虚线：dashed 
- [x] 点线：dotted 

#### 2.2 边框（border）--单方向设置
+ 场景：只给盒子的某个方向单独设置边框
+ 属性名：**<font style="color:#E8323C;">border-方位名词</font>**
+ 属性值：连写的取值

#### 2.3 边框（border）--单个属性
| **作用** | **属性名** | **属性值** |
| :---: | --- | :---: |
| **边框粗细** | border-width | 数字+px |
| **边框样式** | border-style | 实线solid、虚线dashed、点线 dotted |
| **边框颜色** | border-color | 颜色取值 |


**注意：**

+ **border是会撑大盒子的（做好后要检查盒子的尺寸是否是对的）**
+ **布局顺序遵循：从外往内、从上往下**
+ **每一个盒子的样式**
    - **宽高**
    - **辅助的背景颜色**
    - **盒子模型的部分：border、padding、margin**
    - **其他样式：color、font-、text**

#### <font style="color:#C41D7F;">2.4 padding 和border一样都会撑大盒子</font>
- [x] **<font style="color:#C41D7F;">padding会直接添加</font>****上下左右四个方向的内边距，但可以单独设置单个方向的内边距，也可以复合属性连写，最多同时分别设置四个方向的padding值**
- [x] **顺序：****<font style="color:#F5222D;">上右下左</font>****，如果设置三个值：1-上，2-左右，3-下；如果设置两个值：1-上下、2-左右**

<u>新浪网页优化--用padding替换box的固定宽度可以让网页更灵活，不固定box的宽度可以往里面填充任意长度的内容，并用padding保持内容与内容之间的距离，美观！！</u>

#### 2.5 css3盒模型（自动内减--内减模式）<font style="color:#E8323C;"> </font>**<font style="color:#E8323C;">box-sizing：border-box</font>**
+ 操作：给盒子设置属性**<font style="color:#389E0D;">box-sizing：border-box</font>**；即可
+ 优点：浏览器会自动计算多余大小，自动在内容中减去
+ <!-- box-sizing:border-box----当你定义一个div盒子的大小时，如果没有这个值，此时定义的范围只是内容的范围，此时再去对div做margin或者padding，盒子实际占的范围是大于所定义的范围的，为了满足要求，常常需要去人为精确地计算；而加上这个属性之后，css3会自动把magin和padding算在定义的盒子的长宽内，content部分会随着设置的margin和padding的大小而自动变化，而div所占的大小仍然是定义的大小 -->

#### 2.6 外边距（margin）和padding的写法一样
#### 2.7 清除默认的内外边距
场景：浏览器会默认给部分标签设置默认的margin和padding，但一般在项目开始前需要先清除这些标签默认的margin和padding，后续自己设置

+ 比如：body标签默认由margin：8px
+ 比如： p标签默认由上下的margin
+ 比如：ul标签默认由上下的margin和padding-left
+ 。。。。。

解决方法：

标签选择器选择标签设置margin：0；padding：0

*{}----选择全部

div, body, a.....{}----并列标签选择器

#### 2.8 版心居中
版心：网页的有效内容

**<font style="color:#E8323C;">margin: 0 auto;</font>**

#### 2.9 外边距折叠现象-① 合并现象
+ <font style="color:#E8323C;">垂直布局</font>的<font style="color:#E8323C;">块级</font>元素，<font style="color:#E8323C;">上下的margin会合并</font>
+ 结果：最终两者的距离为margin的最大值
+ 解决办法：避免就好
    - 只给其中一个盒子设置margin即可

#### 塌陷问题
+ 场景：<font style="color:#E8323C;">互相嵌套</font>的<font style="color:#E8323C;">块级</font>元素，<font style="color:#E8323C;">子元素的margin-top会作用在父元素上</font>
+ 结果：导致父元素一起往下移动
+ 解决方法：
    1. 给父元素设置<font style="background-color:#B7EB8F;">border-top</font>或者给子集用<font style="background-color:#B7EB8F;">padding-top代替margin-top</font>（分隔父子元素的margin-top）
    2. 给父元素设置<font style="background-color:#B7EB8F;">overflow：hidden  </font>✔（较好的解决方法）
    3. 转换成行内块元素
    4. 设置浮动

#### paddin和margin无法改变行内元素<font style="color:#E8323C;">垂直</font>的内外边距，无法改变行内标签的<font style="color:#E8323C;">垂直</font>位置，不可设置宽高（top和bottom不生效）----解决办法：可以通过设置行高来改变（line-height）
**水平位置（****<font style="color:#E8323C;">left</font>****和****<font style="color:#E8323C;">right</font>****是生效的）**

## CSS浮动
### 1、结构伪类选择器
目标：能够使用结构伪类选择器在HTML中定位元素

#### a、作用与优势
+ 作用：根据元素在HTML中的结构关系查找元素
+ 优势：减少对HTML中类的依赖，有利于保持代码整洁
+ 场景：常用于查找某父级选择器中的子元素

#### b、 选择器
| 选择器 | 说明 |
| :---: | :---: |
| E:first-child{} | 匹配父元素中的第一个子元素，并且是E元素 |
| E:last-child{} | 匹配父元素中最后一个子元素，并且是E元素 |
| E:nth-child(n){} | 匹配父元素中第n个子元素，并且是E元素 |
| E:nth-last-child(n){} | 匹配父元素中倒数第n个子元素，并且是E元素 |


- [x] E是元素的英文单词element的首字母E，就是元素/标签的意思

#### n的注意点
1、n为：0、1、2、3、4、5........

2、通过n可以组成常见公式（数字可以自定义，如4n、n+6等）

| **功能** | **公式** |
| :---: | :---: |
| 偶数 | 2n、even |
| 奇数 | 2n+1、2n-1、odd |
| 找到前5个 | -n+5 |
| 找到从第5个往后 | n+5 |


### 2、伪元素
伪元素：一般页面中的非主体内容可以使用伪元素（一般用于装饰性的小图）

区别：

+ 元素：HTML设置的标签
+ 伪元素：由CSS模拟出的标签效果

种类：

| **伪元素** | **作用** |
| :---: | :---: |
| ：：before | 在父元素内容的最前添加一个伪元素 |
| ：：after | 在父元素内容的最后添加一个伪元素 |


+ 找父级，在这个父级里面创建子级标签

注意点：

1. 必须设置**<font style="color:#E8323C;">content</font>**属性才能生效，content里面写想要放的内容/文字或者img之类的
2. 伪元素默认是**<font style="color:#E8323C;">行内</font>**元素

### 3、标准流
能够认识标准流的默认排布方式及其特点

标准流：又称文档流，是浏览器在渲染网页内容是默认采用的一套排版规则，规定了应该以何种方式排列元素

- [x] 常见标准流排版规则：
+ 块级元素：从上往下，垂直布局、独占一行
+ 行内元素或行内块元素：从左往右，水平布局，空间不能自动拆行

### 4、浮动
目标：能够认识使用浮动的作用，了解浮动的特点

**<font style="color:#E8323C;">浏览器解析行内块或行内标签时，如果标签换行书写或产生一个空格的距离</font>**

#### 4.1 浮动的作用
- [x] **早期的作用：图文环绕**
- [x] **现在的作用：网页布局--可以让两个标签完美地在一行排**

#### 4.2 浮动的特点（浮动标签默认是顶对齐的，可以加margin改变位置）
1. 浮动元素会**<font style="color:#D46B08;">脱离标准流</font>**（简称：脱标），**在标准流中不占位置**
+ 相当于从地面飘到空中

2、 <font style="color:#D46B08;">浮动元素比标准流高半个级别，可以覆盖标准流中的元素</font>（可以盖住标签但是盖不住内容，比如字）

3、浮动找浮动，**下一个浮动元素或在上一个浮动元素后面左右浮动**

4、浮动元素有特殊的显示效果（浮动后的标签具备行内块特点）

+ **一行可以显示多个**
+ **可以设置宽高**
+ **父级没地儿了会自动换行。。。如果父级的宽度或长度不够，子级会自动换行**

#### 注意点： 浮动的元素不能通过text-align:center或者margin:0 auto 居中
#### css书写顺序：<font style="color:#F5222D;">（浏览器的执行效率会更高）</font>
1. 浮动 / display
2. 盒子模型：margin border padding 宽度高度背景色
3. 文字样式

#### 做网站的主导航，必须是 <font style="color:#F5222D;">li>a </font>的结构（如果只用a标签，浏览器的解析效率会非常低）
带class的标签速写：.class名+.class名----自动出现有两个 class的div

#### 4.3 清除浮动
含义：<font style="color:#F5222D;">清除浮动所带来的影响</font>

+ 影响：如果子元素浮动了，此时子元素**<font style="color:#F5222D;">不能撑开标准流</font>**的块级父元素

原因：

+ 子元素浮动后脱标---不占位置

**<font style="color:#F5222D;">目的：</font>**

+ 需要父元素有高度，从而不影响其他网页元素的布局

**清除浮动的方法**

**<font style="color:#22075E;">父子级标签，子级浮动、父级没有高度，后面的标准流盒子会受影响，显示到上面的位置</font>**

- [x] **直接设置父元素高度**

特点：<font style="background-color:rgba(182,255,208,1);"></font>

    1. 优点：简单粗暴，方便
    2. 缺点：有些布局中不能固定父元素高度。如：新闻列表、京东推荐模块
- [x] **额外标签法**

操作：

    1. 在父元素内容的最后添加一个块级元素----这个元素的类名一般叫做 **<font style="background-color:rgba(182,255,208,1);">clearfix</font>**
    2. 在添加的块级元素设置 **<font style="background-color:#FFADD2;">clear:both</font>**

特点：

    1. 缺点：会在页面中添加额外的标签，会让页面的HTML结构变得复杂
- [x] ** 单伪元素清除法  ****<font style="background-color:rgba(182,255,208,1);"> : after（单冒号双冒号都可以）</font>**

操作：用伪元素代替了额外标签

①： 基本写法                                          				    ② ：补充写法

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1657444592714-14aa73d3-68da-42f3-9be4-f00a7f43483a.png)                                              ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1657444592706-e5c0022b-f49f-4de5-a5e7-53a622f10de5.png)

特点：

    1. 优点：项目中使用，直接给标签添加类即可清除浮动
- [x]  **双伪元素清除法（可以用于解决外边距塌陷和浮动影响两个问题，便于调用）**

操作：

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1657537082960-fd5872dd-9e8a-4652-9d72-69e4c1ab0b05.png)

.clearfix::before 在于解决外边距塌陷问题（外边距塌陷：<font style="color:#FA541C;">父子级标签，都是块级，子级加margin会影响父级的位置</font>）--变成了table就不是块了，自然也就解决了

特点：

    1. 优点：项目中使用，直接给标签加类即可清除浮动
- [x] **给父元素设置overflow：hidden**

操作：

    1. 直接给父元素设置overflow：hidden

特点：

    1. 优点：方便

## 学成在线项目实战
### 根目录：网站的第一级文件夹
要先建立项目的文件夹，里面用来存放各种素材和文件（这些文件夹或者文件的名字都不能出现中文），做网页的根目录最好要用英文名，因为之后要上传服务器，服务器不支持中文

1. 图片文件夹：images
2. 样式文件夹：CSS （一般工作中都会使用外联式的方法）单独的css文件要在**<font style="color:#FA541C;">html的head里用link标签</font>**来引入
3. 首页：index.html （网站的首页）每个网站的首页都叫index.html---因为服务器找首页都要找index.html
4. **wrapper-**-版心样式--整体框架的水平居中布局
5. 用于调节图片垂直对齐方式 middle：居中：**<font style="color:#389E0D;">vertical-align: middle;</font>**

5、 背景颜色如果是半透明的，用rgba的形式来设置，可以避免box里面的文字继承透明属性

6、 16px的字体实际上占位21.33px的解决方法：在body里设置line-height：1----**<font style="color:#E8323C;">body{line-height：1}---原理：重置了浏览器默认的line-height值--------涉及到有文字的box最好不要把box的高限制在文字大小，会出现问题</font>**

- [x] 7、字和字之间的间距设置属性：**<font style="color:#389E0D;">letter-spaceing</font>**
- [x] 8、标签的阴影标签：box-shadow

9、合适的地方要适当用标题标签(模块介绍文字之类的），有利于网页搜索引擎的优化以及提高代码的可读性

+ <font style="color:#E9E9E9;background-color:#F5222D;">不理解---为什么footer部分里的版心那个距离不用margin-top而是在footer里加padding-top？？？</font>
+ **答：因为在给wrapper加margin时，会出现****<font style="color:#F5222D;">塌陷</font>****，导致footer也一起向下了，所以没效果，解决办法是要清除塌陷！！！就可以解决了**

#### 10、属性选择器 
**控制placeholder的样式** ：

<font style="color:#CF1322;">/* 如果直接在input里面改的话，会同时改变用户输入的文字样式，在这里只是改placeholder里的样式*/</font>

**<font style="color:#389E0D;">.search  input::placeholder{</font>**

**<font style="color:#389E0D;">    </font>****<font style="color:#389E0D;">font-size</font>****<font style="color:#389E0D;">: </font>****<font style="color:#389E0D;">14px</font>****<font style="color:#389E0D;">;</font>**

**<font style="color:#389E0D;">    color: #bfbfbf;  }</font>**

## CSS定位装饰
#### 目标：能够说出定位的常见应用场景，并且能够说出不同定位方式的特点
### 1.1 网页常见布局方式
#### 1、标准流
1. 块级元素独占一行  →  垂直布局
2. 行内元素/行内块元素一行显示多个  →  水平布局

#### 2、浮动
1. 可以让原本垂直布局的 <font style="color:#F5222D;">块级元素变为水平布局</font>

#### 3、定位
1. 可以让元素自由的摆放在网页的任意位置
2. 一般用于 <font style="color:#F5222D;">盒子之间的层叠情况</font>

### 1.2 定位的常见应用场景
####  1、可以解决盒子与盒子之间的层叠问题
+ 定位之后的元素层级最高，可以层叠在其他盒子上面

#### 2、可以让盒子始终固定在屏幕中的某个位置
### 1.3 使用定位的步骤
#### 1、设置定位方式
- [x] 属性名：**<font style="color:#C41D7F;">position</font>**
- [x] 常见属性值

| **定位方式** | **属性值** |
| :---: | :---: |
| 静态定位 | static |
| <font style="color:#FFFFFF;">相对定位</font> | <font style="color:#FFFFFF;">relative</font> |
| <font style="color:#FFFFFF;">绝对定位</font> | <font style="color:#FFFFFF;">absolute</font> |
| <font style="color:#FFFFFF;">固定定位</font> | <font style="color:#FFFFFF;">fixed</font> |


#### 2、设置偏移值（根据实际需要正数或者负数都可以）
+ 偏移值设置分为两个方向，<font style="color:#F5222D;">水平和垂直</font>方向各选一个使用即可
+ 选取的原则一般**<font style="color:#F5222D;">就近原则</font>**（离哪边近用哪个）（也可以写百分比）

方位属性：

[CSS绝对定位（absolute）、相对定位（relative）方法（详解）_IT萌萌熊的博客-CSDN博客](https://blog.csdn.net/Z_CH8648/article/details/128002291)

### 1.4 相对定位
介绍：自恋型定位，相对于自己之间的位置进行移动（且同时占用之前的位置）

代码： **<font style="color:#C41D7F;">position：relative；</font>**

特点：

+ 需要配合方位属性实现移动
+ 相对于自己原来位置进行移动
+ 在页面中占位置  →  没有脱标（原位置）
+ 并且占有原来的位置
+ 仍然具有标签原来的显示模式特点
+ 如果同时定义了left和right的位置，以**<font style="color:#389E0D;">left</font>**为准，如果同时定义了top和bottom的位置，以**<font style="color:#389E0D;">bottom</font>**为准

#### 应用场景：
+ 配合绝对定位组CP（**<font style="color:#F5222D;">子绝父相</font>**）
+ **<font style="color:#1D39C4;">用于小范围的移动</font>**

### 1.5  绝对定位
介绍：拼爹型，相对非静态定位的父级定位元素移动（和父级的定位类型无关，只要有，就相对）---一般工作中会将父级的定位方式控制为relative

代码：**<font style="color:#C41D7F;">position：absolute；</font>**

特点：

1. 需要配合方位属性实现移动
2. 默认相对于浏览器可视区域进行移动
3. 在页面中不占位置  →  **<font style="color:#389E0D;">已经脱标</font>**
4. 会**<font style="color:#F5222D;">改变原标签的显示模式</font>**特点，具备**<font style="color:#F5222D;">行内块</font>**的显示特点（行内多个且宽高可修改）
5. **先找已经定位的父级，如果有这样的父级就以****<font style="color:#389E0D;">父级</font>****为参照物进行定位**
6. **有父级，但父级没有定位，以****<font style="color:#389E0D;">浏览器窗口</font>****为参照进行定位**

#### 应用场景：
1. 配合绝对定位组CP(**<font style="color:#F5222D;">子绝父相</font>**） ---<font style="color:#135200;">父级（广义上的父级）一般用相对定位，子级用绝对定位（因为父级没有已经定位的爷级，所以用相对定位比较好调整位置，而子级有了已经定位的父级，用绝对定位根据父级调整子级的位置比较合适）</font>
2. **绝对定位查找父级的方式：就近找定位的父级，如果逐层找不到定位的父级，就以浏览器窗口为参照进行定位。**

#### 绝对定位居中
- [x] <font style="color:#E8323C;">绝对定位的的盒子不能使用左右margin auto居中</font>

解决方法：通过绝对定位的位置来居中，<font style="background-color:#B7EB8F;">定位50%</font>+<font style="background-color:#B7EB8F;">按实际情况+或者-盒子宽或者高的一半</font>。

- [x] 位移属性：**<font style="color:#003A8C;">transform：translate（-50%，-50%）</font>**----移动自己高度宽度的一半，负的表示往左往上挪
+ 如果子级和父级的宽度相同，子级的宽度可以写100%

### 1.6 固定定位 
介绍：死心眼型定位，**相对于浏览器**进行定位移动

- [x] 代码：**<font style="color:#C41D7F;">position:fixed</font>**

特点：

1. 需要配合方位属性实现移动
2. 相对于浏览器可视区域进行移动
3. 在页面中不占位置  →  已经脱标
4. 具备行内块显示特点----尽量设置尺寸或者里面有内容，否则盒子会看不见

#### 应用场景
1. 让盒子固定在屏幕中的某个位置

### 1.7 元素层级问题
#### 不同布局方式元素的层级关系：
+ **<font style="color:#389E0D;">标准流< 浮动< 定位</font>**

#### 不同定位之间的层级关系：
+ 相对、绝对、固定默认层级相同
+ 此时**<font style="color:#C41D7F;">HTML中</font>**写在**下面的元素**层级更**高**，会覆盖上面的元素 
    - 如果想要改变这个默认位置，用**<font style="color:#C41D7F;"> z-index: 整数；</font>****其中数值取值越大，显示顺序越靠上（**每个元素的z-index默认值为0**）----这个属性只能加在****<font style="color:#DF2A3F;">有定位的盒子上，才能生效</font>**
    - <font style="color:rgb(0, 0, 0);">z-index只在定位元素（</font><font style="color:#601BDE;">position=static除外，因为元素默认就是static，相当于没用position样式</font><font style="color:rgb(0, 0, 0);">）中作用，</font>**<font style="color:#DF2A3F;">也是就z-index要配合position一起使用</font>**
    - ![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1713431472304-0541412d-cee3-4871-b390-6fd21ee15715.png)

[不起眼的 z-index 却能牵扯出这么大的学问 - 北风吹雪 - 博客园](https://www.cnblogs.com/bfgis/p/5440956.html)

## 装饰
目标：能够完成元素的装饰效果

### 1.1 认识基线（了解）
基线：浏览器文字类型元素排版中存在用于对齐的基线（baseline）

### 1.2 文字对齐问题
场景：解决**行内/行内块元素垂直对齐**问题

问题：当图片和文字在一行中显示时，其实底部不是对齐的

原因：浏览器遇到**<font style="color:#CF1322;">行内和行内块标签</font>**当做**文字**处理，默认文字是按基线对齐的

### 1.3 垂直对齐方式
- [x] 属性名：**vertical-align----用于行内/行内块标签**
- [x] 属性值

| **属性值** | **效果** |
| :---: | :---: |
| baseline | 默认，基线对齐 |
| top | 顶部对齐 |
| middle | 中部对齐 |
| bottom | 底部对齐 |


+ 但凡是处理**行内块和文字**对齐或者是**行内块和行内块**对齐，想要居中对齐，都用**middle**
+ 还有一种处理方式是**将标签的显示模式转为块**

### 2.1 光标类型
场景：设置鼠标光标在元素上是显示的样式

- [x] 属性名：**cursor**

常见属性值：

| **属性值** | **效果** |
| :---: | :---: |
| default | 默认，通常是箭头 |
| pointer | 小手效果，提示用户可以点击 |
| text | 工字型，提示用户可以选择文字 |
| move | 十字光标，提示用户可以移动 |


### 3.1 边框圆角
**场景：让盒子四个角变得圆润，增加页面细节，提升用户体验**

- [x] 属性名：**<font style="color:#389E0D;">border-radius</font>**

常见取值：数字+px、百分比（圆角的圆的半径）

赋值规则：从左上角开始赋值，然后顺时针赋值，没有赋值的看对角

#### 边框圆角的常见应用：
- [x] 画一个正圆
1. 盒子必须是正方形
2. 设置边框圆角为盒子高度的一般  →  border-raduis：50%
- [x] 胶囊按钮
1. 盒子要求是长方形
2. 设置  →  border-radius：盒子高度的一半

### 4.1 溢出部分显示效果
溢出部分：指的是盒子内容部分超出盒子范围的区域

场景：控制内容溢出部分的显示效果，如：显示、隐藏、滚动条

- [x] 属性名：**<font style="color:#389E0D;">overflow</font>**

常见属性值：

| **属性值** | **效果** |
| :---: | :---: |
| visible | 默认值，溢出部分可见 |
| hidden | 溢出部分隐藏 |
| scroll | 无论是否溢出，都显示滚动条 |
| auto | 根据是否溢出，自动显示或隐藏滚动条 |


### 5.1 元素本身<font style="color:#E8323C;">隐藏</font>
场景：让某元素本身在屏幕中不可见。如：鼠标悬停可见：hover，之后元素隐藏

常见属性：

1. **visibility：hidden（占位置，一般不用）**
2. **<font style="color:#CF1322;">display：none（可以脱标，一般用这个）</font>**

### 6.1 元素<font style="color:#CF1322;">整体</font>透明度
场景：让某元素整体（包括内容）一起变透明

- [x] 属性名：**<font style="color:#389E0D;">opacity</font>**

属性值：0~1之间的数字

+ 1：表示完全不透明
+ 0：表示完全透明

注意点：

+ opacity会让元素整体透明，包括里面的内容，如：文字、子元素等

## 小兔鲜儿项目
### 1.1 精灵图的介绍
**场景：项目中将多张小图片，合并成一张大图片，这张大图片称之为精灵图**

优点：<font style="color:#E8323C;">减少服务器发送次数，减轻服务器的压力，提高页面加载速度</font>

例如：需要在网页中展示8张小图片

+ 8张小图片分别发送  →  发送8次
+ 合成一张精灵图发送  →  发送一次

#### 精灵图的使用步骤
1. 创建一个盒子、设置**盒子的尺寸和小图尺寸相同**
2. 将精灵图设置为盒子的**<font style="color:#389E0D;">背景图片</font>**
3. 修改**<font style="color:#CF1322;">背景图位置</font>**
    - 通过PxCook测量小图片**左上角**坐标，分别取**<font style="color:#CF1322;">负值</font>**设置给盒子的**<font style="color:#389E0D;">background-position:x y（负数，图片向左上移动；正数，图片向右向下移动）</font>**
+ **精灵图一般使用行内标签**

### 2.1 背景图片大小
作用：设置背景图片的大小

- [x] 语法：**<font style="color:#389E0D;">background-size: 宽度 高度；</font>**

取值：

| **属性值** | **效果** |
| :---: | :---: |
| **<font style="color:#1D39C4;">数字+px</font>** | 简单方便，常用 |
| **<font style="color:#1D39C4;">百分比</font>** | 相对于当前盒子自身的宽高百分比 |
| **<font style="color:#1D39C4;">contain</font>** | 包含，将背景图片**等比缩放**，直到不能超出盒子（可能会出现空白） |
| **<font style="color:#1D39C4;">cover</font>** | 覆盖，将背景图片**等比缩放**，直到**刚好填满整个盒子没有空白** |


### 3.1 盒子阴影（一般写在最后）
作用：给盒子添加阴影效果，吸引用户注意，体现页面的制作细节

- [x] 属性名：**<font style="color:#389E0D;">box-shadow</font>**

取值：

| **参数（需要按顺序书写）** | **作用** |
| :---: | :---: |
| **<font style="color:#1D39C4;">h-shadow</font>** | 必须，水平偏移量。允许负值 |
| **<font style="color:#1D39C4;">v-shadow</font>** | 必须，垂直偏移量。允许负值 |
| **<font style="color:#1D39C4;">blur</font>** | 可选，模糊度 |
| **<font style="color:#1D39C4;">spread</font>** | 可选，阴影扩大 |
| **<font style="color:#1D39C4;">color</font>**<br/>**<font style="color:#1D39C4;">inset</font>** | 可选，阴影颜色<br/>可选，将阴影改为内部阴影 |


+ 注意：如果是外阴影，不能写outset，添加了会导致属性报错---默认值就是外阴影

### 4.1 过渡
作用：让**<font style="color:#08979C;">元素样式慢慢</font>**的变化，常配合**hover**使用，增强网页交互体验

- [x] 属性名：**<font style="color:#389E0D;">transition：属性1 时长，属性2 时长；</font>****（如果变化的属性多，直接写all，表示所有）**

常见取值：

| **参数** | **取值** |
| :---: | :---: |
| **<font style="color:#1D39C4;">过渡的属性</font>** | all：所有能过渡的属性都过渡 / 具体属性名如：width：只有width过渡 |
| **<font style="color:#1D39C4;">过渡的时长</font>** | 数字+ s（秒） |


#### 注意点
1. 过渡需要：**默认状态和hover状态样式不同**，才能有过渡效果
2. transition属性给**需要过渡的元素**本身加
3. transition属性设置在不同状态中，效果不同的
    1. 给默认状态设置，鼠标移入移出都有过渡效果
    2. 给hover状态设置，鼠标移入有过渡效果，移出没有过渡效果

### 5.1 文字阴影
- [x] **<font style="color:#389E0D;">text-shadow：水平（数字+px）  垂直（数字+px） 模糊（数字+px） 阴影颜色</font>**

### 6.1 网页与网站的关系
### 7.1 骨架结构标签
#### 1.1 DOCTYPE 文档说明
<!DOCTYPE html> 文档类型声明，告诉浏览器该网页的HTML版本----HTML5

注意点：DOCTYPE需要写在页面的第一行，不属于HTML标签

#### 1.2 网页语言
+ <font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">html </font><font style="color:#9cdcfe;background-color:#1e1e1e;">lang</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"en"</font><font style="color:#808080;background-color:#1e1e1e;">></font>  标识网页使用的**<font style="color:#CF1322;">语言</font>**
+ 作用：<font style="color:#CF1322;">搜索引擎归类</font>+<font style="color:#CF1322;">浏览器翻译</font>
+ 常见语言：**<font style="color:#CF1322;">zh-CN</font>**简体中文/ **<font style="color:#CF1322;">en</font>** 英文
+ <font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">meta </font><font style="color:#9cdcfe;background-color:#1e1e1e;">charset</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"UTF-8"</font><font style="color:#808080;background-color:#1e1e1e;">></font>    标识网页使用的字符编码方式（保存和打开的字符编码需要统一设置，否则可能或出现乱码）
+ <font style="color:#808080;background-color:#1e1e1e;"><</font><font style="color:#569cd6;background-color:#1e1e1e;">meta </font><font style="color:#9cdcfe;background-color:#1e1e1e;">name</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"viewport"</font><font style="color:#9cdcfe;background-color:#1e1e1e;">content</font><font style="color:#d4d4d4;background-color:#1e1e1e;">=</font><font style="color:#ce9178;background-color:#1e1e1e;">"width=device-width, initial-scale=1.0"</font><font style="color:#808080;background-color:#1e1e1e;">></font>  →  将宽度=设备宽度（这个元素在开发移动端网页的时候要用）

### 8.1 SEO简介
SEO(Search Engine Optimization）：搜索引擎优化

作用：让网站在搜索引擎上的排名靠前

提升SEO的常见方法：

1. 竞价排名
2. 将网页制作成html后缀
3. 标签语义化（在合适的地方使用合适的标签）
4. ......

#### 1.1 SEO三大标签（里面的文字一般不需要自己编写）
1. **<font style="color:#CF1322;">title</font>**：网页标题标签
2. **<font style="color:#CF1322;">descriptin</font>**：网页描述标签（<meta name="description" content="........">）
3. **<font style="color:#CF1322;">keywords</font>**：网页关键词标签 (<meta name="keywords" content=".........">）

### 9.1 ico图标设置
场景：显示在标签页标题左侧的小图标，习惯使用.ico格式的图标----浏览器最上面的页面图标

#### 常见代码：（favicon）
<font style="background-color:#FFEC3D;"><link rel="shortcut icon" href="icon图标路径" type="image/x-icon"></font>

这个图标一般会放在根目录下面

### 10.1 版心
版心是指网页中主体内容所在区域，一般在浏览器窗口水平居中显示，常见的宽度值为960px/980px/1190px/1210px等。

网页设计中，宽度的设置，是没有绝对固定的值的，根据需求出发

#### 布局流程
为了提高网页制作的效率，布局时通常需要遵循一定的布局流程，具体如下：

1. 确定页面的版心（可视区）
2. 分析页面中的行模块，以及每个行模块中的列模块
3. 制作HTML结构
4. css初始化，然后开始运用盒子模型的原理，通过div+css布局来控制网页的各个模块

### 二、项目结构搭建
能够用专业方式完成项目结构搭建和基础公共样式

#### 1.1 文件和目录准备
1、新建项目文件夹<font style="color:#F5222D;">xtx-pc-client（小兔鲜-pc端）</font>，在vscode中打开

+ 在实际开发中，项目文件夹不建议使用中文
+ 所有项目相关文件都保存在<font style="color:#F5222D;">xtx-pc-client</font>目录中

2、复制favicon.icon到xtx-pc-client目录

+ 一般习惯将ico图表放在项目根目录

3、 复制<font style="color:#F5222D;">imags</font>和<font style="color:#F5222D;">uploads</font>目录到<font style="color:#F5222D;">xtx-pc-client</font>目录中

+ images：存放网站**<font style="color:#CF1322;">固定使用</font>**的图片素材，如：<font style="color:#00474F;">logo、样式修饰图片</font>....等
+ uploads：存放网站**<font style="color:#CF1322;">非固定使用</font>**的图片素材，如：<font style="color:#00474F;">商品图片、宣传图片...</font>等

4、新建index.html 在根目录

5、新建css文件夹保存网站的样式，并新建一下css文件：

+ base.css：基础公共样式（如默认样式的清除之类的）
+ common.css：该网站**多个网页相同模块的重复样式**，如：<font style="color:#003A8C;">头部、底部</font>
+ index.css：首页样式

### HTML/css命令规范
1. [https://blog.csdn.net/weixin_45785873/article/details/106354569](https://blog.csdn.net/weixin_45785873/article/details/106354569)

### 问题
#### 1、给 li 元素加float：right，列表元素会颠倒顺序
解决办法：**<font style="color:#08979C;">给li的父元素 ul 加 float：right，给 li 加 float：left</font>**

#### 2、图片居中方法（或居中失效的原因）
[解决方法](https://blog.csdn.net/weixin_45999422/article/details/124173543?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-124173543-blog-114537819.t0_layer_eslanding_sa&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-124173543-blog-114537819.t0_layer_eslanding_sa&utm_relevant_index=1)

#### 3、行内元素与margin和padding之间的一些问题
<font style="color:rgb(33, 37, 41);">1.首先行内元素是否具有盒子模型？  
</font><font style="color:rgb(33, 37, 41);">	答：行内元素同样具有盒子模型。</font>

<font style="color:rgb(33, 37, 41);">2.行内元素的padding、margin是否无效？</font>

+ <font style="color:rgb(33, 37, 41);">行内元素的padding-top、padding-bottom、margin-top、margin-bottom属性设置是</font>**<font style="color:#08979C;">无效</font>**<font style="color:rgb(33, 37, 41);">的；</font>
+ <font style="color:rgb(33, 37, 41);">行内元素的padding-left、padding-right、margin-left、margin-right属性设置是</font>**<font style="color:#08979C;">有效</font>**<font style="color:rgb(33, 37, 41);">的；</font>
+ <font style="color:rgb(33, 37, 41);">行内元素的padding-top、padding-bottom从显示的效果上是增加的，但其实设置的是无效的。并不会对他周围的元素产生任何影响。</font>

#### 4、做banner图的不成文习惯与规定
1. 如果有多张图，一般用**ul嵌套li标签**，有几个图片，就有几个li标签
2. 然后banner图下面的<font style="color:#08979C;">小圆点</font>，一般用**ol嵌套li标签**

##### 文字超出了它本身应该占有的高度，还有一种解决办法是直接给文字加一个高度
#### 3、为什么有些网页放大后显示会错位？？
### :activate 伪类---用户按下按键和松开按键的反馈表现
<font style="color:rgb(27, 27, 27);">匹配被用户激活的元素--</font><font style="color:rgb(78, 78, 78);"> CSS 3 规定</font><font style="color:#08979C;"> :active 伪类必须只匹配主按键</font><font style="color:rgb(78, 78, 78);">；对于右手操作鼠标来说，就是</font><font style="color:#08979C;">左键</font><font style="color:rgb(78, 78, 78);">。</font>

<font style="color:rgb(27, 27, 27);">它让页面能在浏览器监测到激活时给出</font><font style="color:#08979C;">反馈</font><font style="color:rgb(27, 27, 27);">。当用鼠标交互时，它代表的是用户按下按键和松开按键之间的时间。</font>

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663657490615-dd4f711c-9fda-46ec-9664-344d78879cd2.png)

- [x] 当用户按下有a标签的组件时，颜色变成红色，松开后恢复原来的
+ <font style="color:rgb(27, 27, 27);">这个样式可能会被后声明的其他链接相关的伪类覆盖，这些伪类包括 </font>[:link](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:link)<font style="color:rgb(27, 27, 27);">，</font>[:hover](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:hover)<font style="color:rgb(27, 27, 27);"> 和 </font>[:visited](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:visited)<font style="color:rgb(27, 27, 27);">。</font>
+ <font style="color:rgb(27, 27, 27);">为保证样式生效，需要把 :active 的样式放在所有链接相关的样式之后。这种链接伪类先后顺序被称为 </font>_**<font style="color:rgb(27, 27, 27);">LVHA 顺序</font>**_<font style="color:rgb(27, 27, 27);">：</font>**<font style="color:rgb(27, 27, 27);background-color:#FFEC3D;">:link — :visited — :hover — :active</font>**



