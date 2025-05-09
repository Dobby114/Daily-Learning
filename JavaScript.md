[编写好的javas](https://github.com/rwaldron/idiomatic.js)一些课程知识和资源获取：[https://codingheroes.io/resources/](https://codingheroes.io/resources/)

emoji：用win+. 可以调出vs自带的小表情图片

定义：一种高级的面向对象的多范式编程语言

html：名词

css：形容词

js：动词--实现各种交互、风格操纵以及从远程服务器上加载数据等等

ES5：ECMAScript  ，ES6之后的版本被称为 modern js

在html中引入js文件

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662432781906-7e4eccb1-d6c9-4ac2-8264-0fe767e317ed.png)

#### 变量
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662433122285-02c4f6c6-6016-4222-85f6-eae7264eb95a.png)

命名规则

+ 不能以数字开头，可以以字母、下划线和$符号开头（约定：通常变量名不以大写字母开头）
+ 如果是一个约定俗成的常数，通常用大写，如 PI=301415
+ 如果有多个单词，除了第一个单词后所有单词首字符要大写，如：firstName、firstNamePerson
+ 不能有空格
+ 不能有特殊字符
+ 不能有关键词，如new、function
+ 不能有其他符号

### 数据类型
1. Number 数字
2. String 字符串：需要加引号（单引号或者双引号都可以）
3. Boolean（布尔值）：逻辑符（true 或者 false）
4. Undefined：未赋值的变量（已经声明，但未赋值）
5. Null：空值（人为设置的空对象）
6. Symbol（es2015）
7. Biglnt（es2020）：数字类型的数据不能承载的更大的整数

js有动态类型特性：他会自动定义存储到变量中的值的数据类型----在js中，<font style="color:#E8323C;">是值有数据类型，而不是变量！</font>

可以对同一个变量赋不同数据类型的值

#### null和undefined的区别
1. null表示一个变量**被人为设置为空对象**，转为**<font style="color:#DF2A3F;">数值时为0；</font>**转为布尔时为false
2. undefined表示一个”未定义“的原始值，转为**<font style="color:#DF2A3F;">数值时为NaN；</font>**转为布尔时为false

#### typeof：查看某个值或者变量的数据类型
- [x] 首次定义变量是需要用 let ，后面改变这个变量的值时，不需要用 let，直接分配新的值

#### 类型转换
- [x] Number() 函数可以将其他数据类型值转换为数字类型，但是原变量的值仍然是转换前的数据类型，需要将Number(被转换的变量) 赋给新的变量才行

**<font style="color:#D46B08;">JS只能转换</font>****<font style="color:#CF1322;">数字</font>****<font style="color:#D46B08;">、</font>****<font style="color:#CF1322;">字符串</font>****<font style="color:#D46B08;">和</font>****<font style="color:#CF1322;">布尔</font>****<font style="color:#D46B08;">三种类型的数据</font>**

#### 强制转换
当处理两个不同数据类型的值时，js会自动进行强制转换，让其中一个值的数据类型匹配另一个值的数据类型，让两个数据类型一致从而进行计算（通常发生在运算中）

+ 当运算符是<font style="color:#389E0D;">减号、除号、乘号、幂次等</font>时，js会将式子中的<font style="color:#CF1322;">字符串强制转换为数字</font>
+ 当运算符是<font style="color:#389E0D;">+号</font>时，js会自动将式子中的<font style="color:#CF1322;">数字强制转换为字符串，并且会运算式子中可运算的加法</font>

如：<font style="background-color:#87E8DE;">2+3+4+‘5’=‘95’</font>

#### 布尔值
**虚假值：****<font style="color:#531DAB;">0，'' ，indefined，null，NaN</font>**

当这五个虚假值被转换为<font style="color:#D4380D;">布尔</font>时，会转换为**<font style="color:#D4380D;">false</font>**，**<font style="color:#D4380D;">其他的都是true</font>**

js通常在两种情况下强制转换布尔值

- [x] 逻辑运算符
- [x] 逻辑语句，如if else

可以用布尔值转换**来检查变量是否实际定义（**但当它定义为<font style="color:#1D39C4;">虚假值</font>时，会出现和未定义一样的结果**）**

### 声明变量的三种方式
尽量正确地声明变量，以避免出现各种bug

可以同时声明多个变量（和python差不多）

#### <font style="color:#D46B08;">let：声明</font>空变量或者后续会改变的变量（作用域？）
#### <font style="color:#D46B08;">const：变量</font>中的值后续不能更改（常量变量）
不能声明空的const变量

#### <font style="color:rgb(77, 77, 77);">const定义的数组和对象的值可以被改变，因为数组和对象都属于引用数据类型</font>
[为什么const定义的数组和对象的值可以变_JJYdesu的博客-CSDN博客_const声明的数组可以改变吗](https://blog.csdn.net/weixin_40764047/article/details/121947261)

#### <font style="color:#D46B08;">var：</font>（比较旧的声明变量的方式）---函数范围？
和let类似，后续可以修改变量，但其实还是有很多不同，后续学习

### 运算符
运算法优先级：

[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

#### 算数运算符：=、+ 、- 、*   、 / 、**（幂）、x++、x--、x+=；等等
通过+实现两个字符串的连接

#### 比较运算符：>, < ,>=,<=,===<font style="color:#1D39C4;">（js里是三个等于号</font>），==，！==（严格不等于），！=（松散不等于）
##### <font style="color:#1D39C4;">==</font> 不判断数据类型，只判断值是否相等（相当于做了强制转换）---松散的相等比较符（要避免，容易导致错误）
##### <font style="color:#1D39C4;">===</font> 不仅判断值，还判断值的类型是否相等---严格比较符（默认使用）
### 逻辑运算符
##### AND<font style="color:#1D39C4;">（&&）</font> , OR<font style="color:#1D39C4;">（ll）</font> , NOT<font style="color:#1D39C4;">(!)</font> 逻辑运算符  
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662476216887-7cd32305-b14e-4442-9eb5-e5e9aa55ce6d.png)

**<font style="color:#D4380D;">按照需要可以同时组合多个运算符</font>**



### 字符串编码
#### 用反引号 ``
- [x] 写一个字符串模板，相比于用+号连接字符串，这种方式可以更加方便简单地<font style="color:#E8323C;">控制空格，</font>变量用**<font style="color:#E8323C;">${变量名}</font>**<font style="color:#E8323C;"> </font>引入

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662468807406-2d093f09-9e29-49b5-b26c-379525a4334c.png)



- [x] 在反引号内输入任何字符串
- [x] **<font style="color:#E8323C;">回车</font>**创建多行文本

### if ——else if——if 语句
如果花括号里的语句只有一行，我们实际上可以不写花括号（表示一个代码块）

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662469349548-d99ad089-6eb3-464f-a9a2-83718ff748b7.png)

+ else 是可选选项，如果需要就写
+ **<font style="color:#08979C;">注意分号！！</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662469625617-579459ef-f8a2-40c4-961b-9482f5444ae2.png)      ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662469726697-93623710-d3a2-4e7c-a476-79f4c528ea48.png)

+ 如上左写代码会出错：**<font style="color:#D46B08;">代码块内定义的变量在代码块外无法访问</font>**
+ 但是如图右这样写的话就没问题，<font style="color:#D46B08;">定义了一个全局变量</font>，在代码块内进行了赋值修改

### switch 语句  -------多个比较
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662896170815-59ea44f8-ddca-4564-a391-7d7259ffe65b.png)



#### 注意
1. 每个case 都执行了**<font style="color:#E8323C;">严格比较</font>**，即：===，如果匹配，则会执行子语句
2. 每个case都必须要有break，如果某个case没有break，则代码将会**<font style="color:#E8323C;">从匹配的case语句开始执行</font>**，然后继续执行下一个case语句，**<font style="color:#E8323C;">不论值是否匹配</font>**
3. 当case中的条件**<font style="color:#E8323C;">都不匹配时</font>**，执行default语句

### 语句和表达式
<font style="color:rgb(33, 37, 41);">主要区别在于：</font>**<font style="color:rgb(33, 37, 41);">一条语句执行一个动作，一个表达式产生一个值</font>**

<font style="color:rgb(33, 37, 41);">意思是一个表达式执行后一定会生成一个</font>**<font style="color:#E8323C;">值</font>**<font style="color:rgb(33, 37, 41);">，而语句不一定会产生值。</font><font style="color:#08979C;">语句主要是用来执行动作，程序就是由一系列语句组成</font><font style="color:rgb(33, 37, 41);">。</font>

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662897062575-e0f1d603-6594-4ad1-b03f-205e383cef0a.png)

## 条件运算符（三元运算符）----条件 ？表达式1：表达式2；--必须是<font style="color:#389E0D;">表达式</font>！！
运算符总是会产生值，它是一个表达式

必须要有一个else模块，在冒号背后

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662948361245-545260b6-373d-43d2-a6a7-db1c0aaa3ed3.png)

赋值

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662948361258-245a8ead-d012-4802-8c61-9a4612f23c67.png)

字符串里的值

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662948539643-5a28fdae-ce98-4416-b085-94ec8308ebbe.png)

## ES5,ES6+,ESnext
[兼容查询表](https://kangax.github.io/compat-table/es6/)

浏览器没有前向兼容性，老的浏览器不懂新的js语言

+ 用最新的谷歌浏览器
+ 将现在的js语法转译到之前的版本（转译工具--Babel）

## 激活严格模式（放在开头）
严格模式可以让我们更容易编写安全的js （更容易避免错误，如拼写错误）

- [x] **<font style="color:#389E0D;">‘use  strict’;</font>**
- [x] 严格模式禁用了未来版本中的一些私有或者关键词（或许我的描述不对）

## 函数 (它的本质是一个值）
- [x] <font style="color:#389E0D;"> </font>**<font style="color:#389E0D;">function  （可以重复利用的代码块）</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662985543362-35116aab-e25d-4dff-acaa-f65fc107ddc3.png)

### 函数声明和表达
#### fuction（函数声明式）--如上
#### 匿名函数，不定义函数名，而是直接将函数体赋给一个变量，我认为，这个变量既是一个具有函数功能的值 （函数表达式）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662988321166-e30f98e0-44d3-4ee6-8d9a-f0ef3cffb6e0.png)

- [x] **可以在函数申明之前调用函数**
- [x] **函数表达式写法**：<font style="color:#4C16B1;">不能在未定义函数之前调用函数</font>

### 箭头函数
变量→箭头→表达式

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662989768870-1c79a589-9ce6-4fa5-9675-cf43112e960d.png)

### 函数调用（和python一样）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1662990021092-3a877a5b-7776-4c9c-8e43-90984d211a12.png)

alt +（↑）可以让选中的这行代码移动到上一行

ctrl + d 选中该页面中所有出现的这个单词

## 数组
不能对数组进行上述其他数字和字符串之间的运算（加减乘除等）

如果直接让两个数组相加，这两个数组会被强制转为字符串然后连接起来

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663396756783-6a450b40-e8f2-4b84-9116-7c8416fd9979.png)

### 数组操作
#### push：添加元素到数组末尾
- [x] 将push的函数赋给新的值得到的是该数组的**长度**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400560862-29b27baa-eb24-4ed6-ab81-40440d3dcd7c.png)

#### unshift：将元素添加到数组开头
- [x] 将unshift的函数赋给新的值得到的是该数组的**长度**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400642133-baed7256-bae5-42b4-b359-a99628124faf.png)

#### pop：删除数组的最后一个元素，并返回最后一个元素
- [x] 被删除的**最后一个变量**将会存储到 lastName 中

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400698058-ede6c6b4-5e5f-4633-87ee-a49d9d25c6c1.png)

#### shift：删除数组第一个元素，其他和pop一样
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400739137-5b93ac63-5eb8-4b80-9836-4023775ab055.png)

#### indexOf：定位元素并返回该元素的下标---执严格比较
- [x] 当该元素不存在时，返回-1

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400836363-a3807e01-6406-4ba6-9769-5833030d0592.png)

#### includes：如果函数在数组中，返回true，如果不在返回false
- [x] 该函数执行强制比较，不会进行数据类型的强制转换，即“23” 和23不相等

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663400906999-6f1e75b1-252a-4fdf-8ebc-785ff88003c0.png)

## 对象（object）
数组中的元素不能命名，只能以索引的方式引用他们

对象定义了键值对，给每个值赋予了一个名字（和字典好像），此时元素的顺序不重要，可以用名字来引用他们

### 键类型
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1746427980660-cfd20c2c-7870-4d3f-b99e-4a79e24a8344.png)

- [x] 函数也是可以的

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663415227886-d1e17bcf-60d7-4a4e-aa27-5375d275f579.png)

### 点记法：Dot notation
修改对象中的值 

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663415741851-5a9c3603-b6c6-4166-98d6-129b3525138d.png)

### 括号记法：Bracket notation
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663415791509-b0c39046-b775-461f-bf9e-5776b33d5858.png)

### 两者之间最大的区别在于，我们可以在括号记法里放入任何我们想要的表达式，实现更多的目的
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663415927159-2b561dfd-e4d3-4f59-a96d-f08cab6cbf5b.png)

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663416638960-c339b6ae-ac06-48aa-8172-2c4374043dc2.png)

#### 添加新元素
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663416906588-daee5c1a-85d1-460f-a7da-85b9b0bde53a.png)

### 对象方法
函数实际上是另一中类型的值，我们可以创建键值对将函数保存在对象中，但他的值必须是一种表达式的写法

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663417814643-3e4c8a86-ab58-4ba5-8b0d-54e7f5acf25d.png)

#### this关键词：对象中存储的函数中的变量可以用<font style="color:#F5222D;">this</font>来代替
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663418699359-c5a15300-e486-4122-8ec2-2d34c53b1d47.png)

##### 此时，当外界语句调用对象中的函数时，this就是调用这个函数的的对象整体
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663418826413-4d4e6fa2-198e-48e3-8aae-2ba6c7e2d193.png)

此时，不需要传入变量，函数中的this就是yihui这个对象，并在函数计算是直接找到了this.year（当然我认为这个不出错的前提是，函数中用的变量已经在对象中定义了！！）

- [x] **<font style="color:#F5222D;">当函数是以箭头函数的形式写的话，用this就会有问题，</font>**（此时this就指向最外层的global（window），global对象中并没有year这个属性，就是undefined！！！！！）

##### 也可以用this来直接存储计算的变量到对象中
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663422461530-34fae9d3-b6e0-48c6-a4f3-a888fc3b2c93.png)

## for 循环
- [x] for （变量初始值；循环条件；变量叠加）{循环体}；

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663424185313-d60152f0-5218-4b10-bf18-753e40f26ede.png)

### 循环数组
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663429179287-1dd340eb-43e1-4575-8ad0-ee60e87a55e8.png)

### breaking---退出全部循环
### continuing---退出当前循环，继续循环下一个
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663429784025-9b47f141-fca2-4d8a-8447-c258987742d8.png)

### 后循环
用i--

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663465114299-d16142d6-32d2-4307-bc4b-bcc3e6765153.png)

### 循环内循环
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663465439867-fb4ebe9c-06e6-44b6-b8ac-08eb4d5d8227.png)

### while循环
当while后的条件为真时，开始循环

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663465819934-c687991e-a632-45e7-86a4-457a8fc51063.png)

<font style="color:#E8323C;">while 根据条件来决定是否进行循环，它不依赖任何计数器，不像for，它在前端中的应用更多</font>

+ 当我们不知道要循环几次是用while循环
+ 当明确知道要循环几次时，可以选for循环

## 开发者技巧和编辑器设置
### prettier插件以及配置以及个性化修改配置---设置→default form→prettier
保存时自动调整代码的格式--更整洁，更好看，更一致

### Monokai Pro插件、TODO Highlight插件
### 浏览器页面自动重新加载--live server
1. live server插件---右下角
2. 使用node.js或者npm包(没学）

codewars：[https://www.codewars.com/dashboard](https://www.codewars.com/dashboard)

### 调试工具
发现问题-找到问题-解决问题

#### 谷歌调试工具--检查→源代码→打断点→调试/ 还可以设置在遇到异常时暂停！！
#### 在js代码里想要暂停的代码前写上 debugger，浏览器会自动打开调试工具，并停在这一行
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663503224101-bde4dc8b-8219-4ddd-a689-f5ec354f8704.png)

## **<font style="color:rgb(68,68,68);">JavaScript in the Browser: DOM and Events</font>**
### 什么是DOM，DOM的操作是什么？
#### DOM
 [什么是DOM?](https://wangdoc.com/javascript/dom/general.html)

<font style="color:rgb(74, 74, 74);">DOM 是 J</font><font style="color:#389E0D;">avaScript 操作网页的接口</font><font style="color:rgb(74, 74, 74);">，全称为“</font><font style="color:#389E0D;">文档对象模型</font><font style="color:rgb(74, 74, 74);">”（</font><font style="color:#389E0D;">Document Object Model</font><font style="color:rgb(74, 74, 74);">）。它的作用是</font>**<font style="color:#F5222D;">将网页转为一个 JavaScript 对象，从而可以用脚本进行各种操作（比如增删内容）</font>**<font style="color:rgb(74, 74, 74);">。</font>

<font style="color:rgb(74, 74, 74);">浏览器会根据 DOM 模型，将结构化文档（比如 HTML 和 XML）解析成一系列的</font>**<font style="color:#389E0D;">节点</font>**<font style="color:rgb(74, 74, 74);">，再由这些节点组成一个</font>**<font style="color:#389E0D;">树状结构（DOM Tree）</font>**<font style="color:rgb(74, 74, 74);">。所有的节点和最终的树状结构，都有</font><font style="color:#389E0D;">规范的对外接口</font><font style="color:rgb(74, 74, 74);">。</font>

<font style="color:#389E0D;">DOM 只是一个接口规范</font><font style="color:rgb(74, 74, 74);">，可以用各种语言实现。所以严格地说，</font>**<font style="color:#CF1322;">DOM 不是 JavaScript 语法的一部分，但是 DOM 操作是 JavaScript 最常见的任务，离开了 DOM，JavaScript 就无法控制网页。</font>**<font style="color:rgb(74, 74, 74);">另一方面，JavaScript 也是最常用于 DOM 操作的语言。后面介绍的就是 JavaScript 对 DOM 标准的实现和用法。</font>

#### 函数实际上是一个值，我们可以将其作为参数传入到别的函数中去
### <font style="color:#CF1322;">添加事件监听器！！addEventListener（‘事件’，function{发生变化的操作}）</font>
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663587833440-5507d4d0-7698-42a8-af9a-10dd947faa1f.png)

这里是为.check组件添加了click事件---花括号里面写点击.check时会发生的事件！！

#### 用户界面返回的值通常是字符串的形式！！
#### <font style="color:#389E0D;">document.querySelector(选择器).value</font>
- [x] **<font style="color:#389E0D;">Math.random()</font>**
- [x] **<font style="color:#389E0D;">Math.trunc()</font>**

#### <font style="color:#389E0D;">document.querySelector(选择器).textContent</font>
#### 更改css样式--<font style="color:#389E0D;">document.querySelector('选择器').style.属性='值'</font>
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663587514058-0aa99062-ab6e-4d0c-b435-aab4fc4603a6.png)

这里的属性和css中的属性的书写方式不大一样，后面必须是要以字符串的形式。

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663590026860-65c583b2-a1ec-4b34-9357-9dc7f50b776b.png)

将input里的值重设为空的

#### 重构
重构代码，避免重复代码--更简洁

+ 可以构建重构函数，重复调用

#### 选择多个组件(必须要有相同的名字？）---<font style="color:#389E0D;">querySelectorAll</font>
得到带有该属性的所有组件列表，它是组件列表不是数组！但它能用大多数数组可以用的函数，比如forEach

#### 分析页面，将可能会改变的类存储到变量
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663643560909-55283c8a-3e85-4886-a2b4-8f645c4f4606.png)

#### 通过<font style="color:#E8323C;">.classList</font>获得该组件所有的类，通过<font style="color:#E8323C;">.remove</font>和<font style="color:#E8323C;">.add</font>删除或增加类
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663643581835-e77d39bd-6420-42ee-9f74-3ee3148fcc56.png)

#### 将页面中重复的代码写入重构函数，传入<font style="color:#E8323C;">重构函数</font>实现功能！！--不带括号
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663644025211-384d5f1f-d53c-4519-815c-ba97a40a6941.png)

原来的匿名函数变成了重构函数的名字！！

### KEYBOARD(键盘事件）
keyboard事件是全局事件，他们不会发生在一个特定的元素上，对于全局事件，通常在**<font style="color:#E8323C;">整个文档（document)</font>**上进行操作

在**<font style="color:#389E0D;">整个文档上添加事件监听器</font>**（**<font style="color:#E8323C;">'keydown'、‘keypress’、‘keyup</font>**’）

给函数设定一个形参，当按下时，我们在键盘上按下的键的信息（包括值包括很多东西）就会被存储到形参中去，被按下的键的值=**<font style="color:#E8323C;">形参.key</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663649118403-af9901ee-9e79-4cb6-b859-55218b39c05c.png)

- [x] **<font style="color:#389E0D;">.contains（）函数 ：</font>**<font style="color:rgb(77, 77, 77);">确定元素中是否包含指定的类名，返回值为true 、false；</font>

#### 画流程图分析问题：[diagrams.net](https://www.diagrams.net/index.html)<font style="color:rgb(30, 32, 34);">  
</font>
### 选择ID选择器的两种方法
- [x] #
- [x] getElimentById （在选择很多数据时**<font style="color:#389E0D;">更快！！</font>**）

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1663677440011-0456ad5c-2cfc-4a16-8f18-16fccd5f84f0.png)

### pig game
#### 1、先分析问题，最好整理一个问题的流程图，按照流程图的思路解决问题
#### 2、打开思路巧用变量
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664179138951-3615ac58-6b53-4cb3-aa84-e9eef1c20eab.png)

#### 3、元素属性可以直接这样改
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664179138952-2d49e71a-7155-4f5f-94d7-3ce8a6d3d908.png)

#### 4、toggle函数：如果改元素不包含某个类，则添加这个类；如果该元素包含这个类，则删除这个类
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664179139008-1a3a26cf-6579-4435-8180-9f49ae04e4c6.png)

#### 5、注意全局变量和局部变量
# 高阶JavaScript
定义：JavaScript是一种高级的，面向对象的多范式编程语言

#### 高级的(high-level)
#### 垃圾回收（garbage-collected）
+ 标记清除法
+ 引用计数法

#### 解释型的或者即时编译的（interpreted or just-in-time compiled）？？后续再学
所有的代码最终都要被翻译到机器码（发生在Javascript引擎内部）

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664197864911-73082570-46f7-4f45-9bbe-7a825dac499b.png)

#### 多范式
###### 程序化编程 
用线性的方式组织函数

##### 面向对象编程（OOP）
1. 命令式
2. 申明式

##### 函数化编程（FP）
#### 基于原型的，面向对象的（prototype-based object-oriented）
#### 一等函数（first-class function）
可以作为函数的参数，可以作为函数的返回值，也可以赋值给变量

#### 动态语言（动态类型）
在js中不会将数据类型分配给变量

#### 单线程的
#### 非阻塞的事件循环（non-blocking event loop）
### js引擎和内存管理（runtime）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664197988967-35962e0a-da24-4b6a-9904-a5c02ffebcc1.png) 

### 执行上下文里面存储的是（<font style="color:#E8323C;">代码在执行上下文/调用堆栈中运行顺序</font>）
- [x] 变量环境
1. 定义的变量
2. 定义的函数
3. argument对象（传递的参数）
- [x] 作用域链
- [x] this 关键词（在执行之前，发生在创建阶段）

**<font style="color:#E8323C;">箭头函数没有参数对象和this关键词</font>**

调用堆栈（先进后出）：执行上下文的地方--他就像js的一张地图，它可以保证上下文的执行顺序永远不会丢失

当关闭网页，全局上下文从调用堆栈中弹出。

### 作用域和作用域链
作用域是我们的代码中申明变量的地方（同样适用于函数，因为函数终归是一个值存储在变量中！）

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1746426808116-007184d5-e398-489d-bc4d-66e2c837d74e.png)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1746426842747-f8cd8be3-bd08-45cd-9a8d-82ff576f6a91.png)

#### 词法作用域
#### 全局作用域
顶级代码----任何函数或者块之外申明的变量

#### 函数作用域
每个函数都会创建一个作用域-----函数内部（又称本地范围或者反全局范围）

函数外部无法访问函数内部定义的变量，但是函数内部可以访问全局上下文中定义的变量

**<font style="color:#E8323C;">var是函数作用域，块作用域不适用于var</font>**

#### 块作用域
快：花括号内的所有内容（比如在if或者循环语句中常常出现） 

**块内申明的变量只能在该块之内访问（****<font style="color:#E8323C;">仅限于let 和const申明的变量！！！</font>****）**

#### 作用域链
子作用域可以访问父作用域的变量

变量查找：当函数需要某个变量，它会先在当前作用域中查找，如果没找到则会在作用域链中一层一层地往外查找，直到找到为止，没找到则报错。

**作用域链和调用堆栈的区别**

**作用域链和调用堆栈中执行上下文的顺序无关，****<font style="background-color:#FBDE28;">只与函数/变量定义的位置有关</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664939637641-d6b87266-0802-42cd-9cec-42c96898aa39.png)

### 总结
- [x] 作用域决定了：<font style="background-color:#FBDE28;">变量在哪里？在哪里可以访问某个变量？在哪里不可以？</font>
- [x] 在js中一共有3中类型的作用域：全局作用域、函数作用域以及块作用域。
- [x] <font style="color:#DF2A3F;">只有let和const变量是块作用域</font>。var申明的变量在最近的函数作用域范围内（<font style="color:#DF2A3F;">var是函数作用域</font>）。
- [x] 在js中采用词法作用域，我们可以在这里得到获得某个变量的规则，该作用域只取决于代码中的函数和块写在哪里，而与他们在哪里调用没有任何关系
- [x] 所有作用域总是可以访问他的所有父作用域，这就是<font style="background-color:#FBDE28;">作用域链</font>
- [x] 当一个变量不在当前的作用域中，引擎会在作用域链中查找直到直到找到该变量，这被称为<font style="background-color:#FBDE28;">变量查找</font>
- [x] <font style="background-color:#FBDE28;">作用域链是单向的</font>：外部作用域永远无法访问内部作用域
- [x] 当前范围内的作用域链等于其所有父作用域的所有变量环境的相加
- [x] 作用域链与函数调用顺序无关，它不会影响作用域链。（词法作用域）

###  提升机制
定义：<font style="background-color:#FBDE28;">使一些变量在定义之前就能被访问</font>（在他们的作用域中被提升到顶部的变量）

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664952726658-c5dd9717-6fb3-41b6-8740-d4adcd74b480.png)

#### Temporal dead zone(暂时性死区TDZ）
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1664952921696-83f198b3-bb41-40ca-8cd5-de6b63de890a.png)

<font style="color:rgb(51, 51, 51);">ES6 明确规定，如果区块中存在 let 和 const 命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。 而使用var申明的变量，不会报错，但是该变量被当成undefine处理（不完全对，var申明是在编译的时候实现的，而赋值或其他操作在执行的时候实现），存在很多问题隐患，所以尽量不要使用var来申明变量。</font>

<font style="color:rgb(51, 51, 51);">总之，在代码块内，使用 let或者const 命令声明变量之前，该变量都是不可用的。这在语法上，称为 “暂时性死区”（temporal dead zone，简称 TDZ）。</font>

**<font style="color:#E8323C;">undefine取反是1</font>**

**在全局上下文中，用var申明的变量将会在windows中创建一个属性。**

### <font style="color:rgb(51, 51, 51);"> this 关键词</font>
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1665387288836-d1dec380-907e-42b1-8437-173a65b586bd.jpeg)

#### this绑定的对象不指向函数本身也不指向它的变量环境
#### this绑定的对象只与调用的位置有关
- [x] **<font style="color:#531DAB;">默认绑定</font>**，函数独立调用，在非严格模式下，this指向全局上下文；在严格模式下，this指向undefined。（**<font style="color:#E8323C;">常规函数调用，就算它调用的位置在某个上下文内，它还是默认绑定！！</font>**）
- [x] **<font style="color:#531DAB;">隐式绑定</font>**，调用位置被包含在某个函数或者某个块内，this指向这个函数或者这块（有上下文）
- [x] **<font style="color:#531DAB;">显示绑定，call（）、apply（）或者bind（</font>****<font style="color:#C41D7F;">）-----fn.call(obj，参数1，参数2。。。)--调用函数fn时将this绑定到obj-----bind()方法返回一个新的函数,并且该函数中的this指向bind（）中的第一个参数</font>**
- [x] **<font style="color:#531DAB;">当一个函数被调用为事件监听时，this指向attached的DOM元素</font>**
- [x] **<font style="color:#531DAB;">箭头函数不使用四条标准的绑定规则，没有它自己的this</font>**，它根据当前的**<font style="color:#C41D7F;">词法作用域</font>**来决定this（无论this绑定到什么）---指向其词法作用域内的this（指向其父级作用域？？）。
- [x] const self = this;

#### call( )和apply( )方法
- [x] 区别：参数传递方式----call方法，参数逐个传递；apply方法，参数需以数组方式传递

```javascript
// Call method
book.call(eurowings, 23, 'Sarah Williams');
console.log(eurowings);

book.call(lufthansa, 239, 'Mary Cooper');
console.log(lufthansa);

const swiss = {
  airline: 'Swiss Air Lines',
  iataCode: 'LX',
  bookings: [],
};

book.call(swiss, 583, 'Mary Cooper');

// Apply method
const flightData = [583, 'George Cooper'];
book.apply(swiss, flightData);
console.log(swiss);

book.call(swiss, ...flightData); //call方法直接传入数组会报错
```

#### bind（）绑定方法
与apply() 、call()不同的是，bind不会立即调用该函数，而是创建一个**<font style="color:#E8323C;">新函数，并且绑定this---就可以得到绑定了不同对象的新的函数！！----甚至是分别得到绑定了不同对象以及设置的固定参数的新的函数！</font>**

```javascript
const bookEW = book.bind(eurowings);
const bookLH = book.bind(lufthansa);
const bookLX = book.bind(swiss);
bookEW(23, 'Steven Williams');  //传入两个参数
```

##### 部分应用（.bind(null, 参数1,，参数2，等等)）----但不能用undefined来作为参数占用符
```javascript
const bookEW23 = book.bind(eurowings, 23);  //设置了一个参数
bookEW23('Jonas Schmedtmann');
bookEW23('Martha Cooper');  //只需传入一个参数！！

```

```javascript
// Partial application
const addTax = (rate, value) => value + value * rate;
console.log(addTax(0.1, 200));

const addVAT = addTax.bind(null, 0.23); //通过设置null，利用bind来得到预设参数的新函数
// 这里也可以不是null，是指用null是一个标准
//但是这里不可以用undefined的作为占位符来跳过参数
// addVAT = value => value + value * 0.23;
```

##### 事件监听器绑定this，用bind，因为需要传入一个函数，而不是调用它，call和apply只能调用，不能得到新的函数
```javascript
// With Event Listeners
lufthansa.planes = 300;
lufthansa.buyPlane = function () {
  console.log(this);

  this.planes++;
  console.log(this.planes);
};
// lufthansa.buyPlane();

document
  .querySelector('.buy')
  .addEventListener('click', lufthansa.buyPlane.bind(lufthansa));
//如果这里不绑定this 的话，这个函数里的this会指向.buy元素！！
```

#### 最好不要在箭头函数中用到this，会出现无法预知的错误（很容易出现）
<font style="color:rgb(51, 51, 51);">argument 关键词只能在常规函数里可以用</font>

### <font style="color:rgb(51, 51, 51);">原始值和对象（基本类型和引用类型）</font>
#### <font style="color:#D22D8D;">原始值</font><font style="color:#D22D8D;">存储在调用栈中（基本类型数据）  
</font><font style="color:#D22D8D;">对象存储在堆中</font>
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1665459304077-305ea643-1776-4b6d-84a0-2a0c56cd49d3.jpeg)

#### <font style="color:#D22D8D;">调用栈中的值不可改变，如果改变了，会分配一个新的内存地址</font>
#### <font style="color:#D22D8D;">堆中的值可以改变，将一个对象复制赋值给另一个对象，这两个对象指向同一个地址，改变其中的一个对象的值，另一个对象也会改变！</font>
#### ![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1665459304087-11504f01-c503-4d6b-9fed-ae02a38febed.jpeg)
#### <font style="color:#DF2A3F;">object.assign()</font>函数---对象浅克隆
- [x] object.assign()的功能是将第二个参数的属性复制到第一个参数中（**<font style="color:#D22D8D;">分配新的内存地址</font>**）

<font style="background-color:#FADB14;">const jessica2 = {</font>

<font style="background-color:#FADB14;">    firstName:'jessica',</font>

<font style="background-color:#FADB14;">    lastName:'davis',</font>

<font style="background-color:#FADB14;">    age:27,</font>

<font style="background-color:#FADB14;">    family:['Alice','Bob']</font>

<font style="background-color:#FADB14;">};</font>

<font style="background-color:#13C2C2;">const jessicaCopu = Object.assign({},jessica2)   </font>

此时相当于将jessica2浅拷贝给jessicaCopu对象（该对象分配了新的内存地址）

- [x] **但是这种方式****<font style="color:#FA541C;">只能复制第一层的值，不能复制对象中的对象</font>****，如family数组中的值，如果改变jessicaCopu中family中的值，jessica2中的该属性的值也会改变，所以称之为****<font style="color:#FA541C;">浅拷贝</font>****。（浅拷贝二者指向同一个地址，改变其中一个，另一个会自动改变！！！）**
- [x] 如果多个源对象有都有相同的属性，，则用最后一个复制的值

### 数组解构----用 [ ] 来解构
解构：分解复杂的数据结构+成较小的数据结构，如变量（方便、快速地处理复杂的数据结构）

- [x] 获值

<font style="background-color:#D9D9D9;">const arr = [1,2,3]</font>

<font style="background-color:#FFFB8F;">const [x,y,z] = arr;    将arr数组中的值按顺序分别赋给变量x，y，z（注意这里x，y，z是单独的变量）</font>

<font style="background-color:#B7EB8F;">const [one, ,three] = arr     用空格表示跳过，获得arr数组中第一个值和第三个值</font>

- [x] 置换顺序（两个变量的值置换顺序）

```javascript
let [x,  ,y]  =  arr;
[x, y] = [y, x];
```

- [x] 从函数返回值

```javascript
const restaurant = {
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  order: function(starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]
  }

const [first, second] = restaurant.order(2,0);  #返回的两个值赋给两个变量
```

- [x] 嵌套解构

```javascript
const nested = [2,4,[5,6]];
const [i, ,[j,k]] = nested; #用嵌套的变量获得嵌套数组里的值！
```

- [x] 设置默认值--当数组长度未知时，变量数可能超过数组长度，此时可以设置一个默认值，不然超出的变量会被赋予undefined

```javascript
const [p,q,r] = [8,9]; #此时r会是undefined
const [p =1,q = 1,r =1] = [8,9]; #此时p是8，q是9，r是1，就不会是undefined
```

### 对象解构---用 { } 来解构--<font style="color:#DF2A3F;">属性名要和对象中定义的属性名一样</font>
- [x] 通过{} 和属性名来获值

```javascript
const restaurant = {
  name_r: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  openingHours: {
    thu: {
      open: 12,
      close: 22,
    },
    fri: {
      open: 11,
      close: 23,
    },
    sat: {
      open: 0, // Open 24 hours
      close: 24,
    },
  },
  order: function({startIndex, mainIndex, time, address}) {
    console.log(startIndex, time)
  }
};
const {name_r,openingHours,categories} = restaurant;
```

- [x] 获值的同时给值赋予新的名字（先拿到再赋新的名字）

```javascript
const{name:restaurantName,
  openingHours:hours,
  categories:tags
}=restaurant;
```

- [x] 设置默认值，以防该值不存在

```javascript
const { name = [], startMenu: starts = []} = restarant;  #
  //当该值存在则获得该值，否则为默认值
```

- [x] 同时改变多个**<font style="color:#E8323C;">已定义变量的值</font>**--用**<font style="color:#E8323C;">( )</font>**将代码包装起来

```javascript
let a = 111;
let b = 999;
const obj = {a: 23,b: 7, c: 14};
({a,b} = obg);  #因为{a，b}相当于是一个代码块，我们不能为代码块分配任何东西，
  必须要用（）将他们包裹在一起
```

- [x] 嵌套对象

```javascript
// 前面已经将对象中的openingHours属性赋给了变量openingHours
const { fri: {open, close} } = openingHours    # 对应名字取值
const { fri: {open：o, close: c} } = openingHours  # 获值且改名
```

- [x]  **<font style="color:#DF2A3F;">将对象作为参数传入函数自动解构（按名称！）</font>**

```javascript
const restaurant = {
  name_r: 'Classico Italiano',
  order: function({startIndex, mainIndex, time, address}) {
    console.log(startIndex, time)
  }
};
// 调用
restaurant.order({
  time: '22:40',
  address: 'via del sole, 21',
  mainIndex: 2,
  startIndex: 2
})   #传入的是一个对象，当函数的参数没有赋默认值时，函数自动将传入的对象按名称解构
// ******************************************************************
const restaurant = {
  name_r: 'Classico Italiano',
  order: function({startIndex = 1, mainIndex = 0, time = ‘20’, address}) {
    console.log(startIndex, time)
  }
};  #可以给函数的参数赋默认值，当传入的参数中没有需要的参数名称时，该参数的值就等于默认值，
  #否则等于传入的值！！
// 调用
restaurant.order({
  time: '22:40',
  address: 'via del sole, 21'
}) 


```

### 扩展运算符 （...）---适用于所有可迭代对象，如<font style="color:#C41D7F;">数组、字符串、map和集合set</font>
#### 可以将数组中的每个元素或者对象中的每个键值对取出（变成独立的多个元素）
#### 在<font style="color:#E8323C;">模板字符串</font>中使用 ... 是<font style="color:#F5222D;">无效</font>的，通常适用于将<font style="color:#EB2F96;">参数</font>传递给<font style="color:#52C41A;">函数</font>或者<font style="color:#52C41A;">构建一个新数组</font>时。
```javascript
const arrOne = [7,8,9]
const arrTow = [1,2,3]
const newArry = [0,1,...arrOne]  # newArry=[0,1,7,8,9]
// 如果不写扩展符，那就变成嵌套数组了
```

```javascript
const restaurant = {
  name_r: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'] 
}
const newMenu = [...restaurant.mainMenu,"Gnocci"]
console.log(...newMenu) # 输出 'Pizza', 'Pasta', 'Risotto' ，'Gnocci'四个元素
```

#### 扩展运算符的两个重要应用： 1、浅拷贝（只拷贝了对象的引用，两个对象仍然指向同一个内存地址--堆）
```javascript
const mainMenuCopy = [...restaurant.mainMenu]  #这个操作比object.assign()更加容易操作
```

#### 2、合并两个数组 
```javascript
const menu = [...restaurant.startMenu, ...restaurant.mainMenu]
```

#### 自从ES2018以来，扩展运算符也适用于对象，即使对象不是迭代的----创建对象和浅拷贝！！
```javascript
const newRestaurant = {foundedIn :1998, ...restaurant, fonder: 'Guiseppe'}
```

```javascript
const restaurantCopy = {...restaurant}
restaurantCopy.name = 'Ristorante Roma'
console.log(restaurantCopy.name)
console.log(restaurant.name)
```

### rest pattern 和参数（...）和扩展运算符写法一样，但用在<font style="color:#DF2A3F;background-color:#FBDE28;">等号左边</font>--打包
#### rest----将多个单独的元素打包成一个数组
```javascript
const [pizza, , risotto, ...otherFood] = [
  ...restaurant.mainMenu,
  ...restaurant.starterMenu,
];
console.log(pizza, risotto, otherFood);   
// Pizza' ,'Risotto',和剩下的
```

```javascript
const { sat, ...weekdays } = restaurant.openingHours;
// 这里的名字必须是要和对象中的一样的，sat，但是...可以重新命名
console.log(sat, weekdays);

```

#### rest参数传入函数（可以实现传入任意数量的参数，...将传入的所有参数打包成一个列表）
```javascript
const add = function (one,...number) {
  console.log(one)  #第一个将会被存储在one里！
  console.log(number);  #[2]、[2,3]。。。。。
};
add(1, 2);
add(1, 2, 3);
add(9, 3, 4, 5);
// 或者
const x = [2,3,5,6,7,8,9]
add(...x)  #扩展运算符--拆开
```

#### 扩展运算法写在有值变量的前面，rest写在需要重新定义新的变量的名字前面
### 逻辑运算符的三个属性
#### 1、他们可以使用任何数据类型
#### 2、他们可以返回任何数据类型
#### 3、 他们的操作被称为短路求值 ( short circuting evaluation ) : 如果前面的条件满足了会立即范围前面的值
### &&（and） 运算符
**虚假值：****<font style="color:#531DAB;">0，'' ，undefined，null，NaN</font>**

返回第一个fake值或者最后一个值（如果前面的值都是真的的话）

### || (or) 运算符
|| 运算符作用的地方不一定是布尔类型的数据

返回第一个真值

这两种运算有时可以用来代替其他复杂的if判断语句

### 空值合并运算符（？？）---ES2020引入的运算符
#### 和or运算符的工作方式一样，<font style="color:#CF1322;">但是他的空值只包括：null，undefined，不包括0和空字符串''</font>
### 逻辑赋值运算符---ES2021引入  （??= 、||=、&&=）
```javascript
const rest1 = {
  name:'Capri',
  numGuests: 20}
const rest2 ={
  name: 'La Piazza',
  owner: 'Giovanni Rossi'
};

rest2.numGuests = rest2.numGuests || 10 ;#如果存在就等于存在的数，否则等于默认值
// 逻辑赋值运算符写法
rest2.numGuests ||= 10; #等价于上面的写法，但是更简洁
// 但上面应该设置成 ？？更合理，因为0是一个合理的数，在这里不应该被认为是虚假值

```

### 循环数组
```javascript
for (const item of menu) conslole.log(item)
```

这种循环数组的方式可以不用设置计数器、代码块等，直接遍历循环数组，更简洁

#### 获得索引 <font style="color:#C41D7F;">menu.entries()</font>
```javascript
for (const item of menu.entries()) {
  conslole.log(item);
}
// 解构返回的索引和值---第一个是索引，第二个是值
for (const[i,el] of menu.entries()) {
  console.log(`${i+1}: ${el};
  }
```

### 对象增强写法
#### 1、将外部的对象定义在某个对象内部，---写法简化
```javascript
const  openingHours =  {
    thu: {
      open: 12,
      close: 22,
    }
  };
const restaurant = {
  name_r: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  // 直接写外部对象的名字，要对应！
  openingHours
};
```

#### 2、定义在对象内部的函数写法简化
```javascript
const restaurant = {
  name_r: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  // test : function(){console.log('win!')}
  // 简化写法---直接省掉属性名和：和function
  test(){console.log('win!')}
};
```

#### 3、对象的属性名可以是变量，可计算！但必须要在每个名字前加上 <font style="color:#E8323C;"> [ ]</font>
```javascript
const name = ['name_r','location'];
const restaurant = {
  [name[0]]: 'Classico Italiano',
  [name[1]]: 'Via Angelo Tavanti 23, Firenze, Italy',
  [`day-${2-1}`]: 'happy',
};
```

### 可选链接  ?.   ----用于判断某个属性是否存在，如果属性不存在，直接返回undefined，执行终止，避免报错！常用于当使用对象中的某个属性，但是不确定该属性是否存在时。
#### ？. 通常与无效合并运算符一起使用
#### 多重属性判断是否存在
```javascript
const restaurant = {
  name_r: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto']，
  openingHours：{
    thu: {
      open: 12,
      close: 22,
    }
  }
}
console.log(restaurant?.openningHours?.open);
// 当？后面的属性存在时，继续执行，返回值；当？后面的属性不存在时，返回undefined，终止执行
```

#### 当使用变量作为对象中的属性名时，要用[ ]把变量包裹起来
```javascript
const days = ['mon','tue','wed']
for (const day in days) {
  const open = restaurant.openningHours[day]?.open ?? 'close'
}
// 当restaurant.openningHours[day]，open等于他的值，否则等于close
```

#### 方法: 判断某个调用的方法是否存在---总是要和 ？？一起工作
```javascript
console.log(restaurant.order?.(0,1) ?? 'Method dose not exits');
# 如果这个方法存在，就可以调用，否则返回后面的，如果后面没有东西，就返回undefined
```

#### 数组: 检查某个数组是否为空
```javascript
const usr =[{name: 'Jonas' , email: 'hello@jonas.io'}]
console.log(usr[0]?.name)
// 当usr[0]存在，就可以返回usr[0].name，否则返回undefined
```

### 循环对象：对象键、值和事件
#### <font style="color:#C41D7F;">Object.keys</font>：循环对象的键：得到一个包含对象中所有键名（<font style="color:#DF2A3F;">可枚举</font>）的数组
- [x] 返回的keys，可被认为是有序的
- [x] 数字---按大小升序排序
- [x] 非数组的字符串按照他们被添加到对象时的顺序排序
- [x] object.keys不会返回symbol类型的属性，需要通过Object.getOwnPropertySymbols获取

```javascript
const properties = Object.keys(openingHours)
console.log(properties) // [key,key,...]
// 得到一个包含对象中所有键名的数组
```

#### <font style="color:#C41D7F;">Object.values</font>：循环对象的值：得到一个包含对象中所有属性值的数组
```javascript
const values = Object.values(openingHours)
console.log(values) // [value,value,...]
// 得到一个包含对象中所有属性值的数组
```

#### <font style="color:#C41D7F;">Object.entries</font>：循环整个对象，得到一个包含所有属性的列表
```javascript
const entries = Object.entries(openingHours)
console.log(entries) //[[key,value],[key,value],[key,value]]
// 得到一个包含对象中所有属性的数组
```

#### for....in
#### Object.getOwnPropertyNames：返回对象自身的所有属性名数组（包括不可枚举属性）
#### 解构写法
```javascript
for (const[day,value] of entries) {
  console.log(day,value)
  // 分别得到了属性名列表和对应的值列表
  // 并且，const中的变量名可以任写
}
// 解构写法
for (const[day,{open,close}] of entries) {
  console.log(day,open，close)
// 对value中的对象进行了结构，得到open和close
}
```

### 集合（sets）--new Set(传入可迭代的对象)----可迭代的
#### 同一个集合中没有重复的值---同一个集合中的元素是独一无二的，并且元素与元素之间是无关的
```javascript
const orderSet = new Set([
  'Pasta',
  'Pizza',
  'pizza',
  'Risotto',
  'Pasta',
  'Pizza'
  ]);
console.log(orderSet)
// {'Pasata','Pizza','Risotto'} 重复的元素消失了
```

#### 集合中的元素是没有索引的，我们无法从集合中获值，没必要将set中的元素拿出来
- [x] 查看集合的大小：**<font style="color:#E8323C;">orderSet.size</font>**
- [x] 查看集合中是否有某个元素：**<font style="color:#E8323C;">orderSet.has('Pizza')</font>**
- [x] 往集合中增加元素：**<font style="color:#E8323C;">orderSet.add('Pizza')</font>**
- [x] 删除集合中的某个元素：**<font style="color:#E8323C;">orderSet.delete('Pizza')</font>**
- [x] 清除集合中的全部元素：**<font style="color:#E8323C;">orderSet.clear()</font>**

#### 只能知道这个集合中是否有某个元素
#### 集合是可迭代的，所以同样可以循环
#### 集合的一大应用：删除数组的重复值---<font style="color:#C41D7F;">const staffUnique = [...new Set(orderSet)]</font>
将数组转为集合再通过扩展运算符将集合转为数组，就可以得到没有重复元素的数组

```javascript
const orderSet = new Set([
  'Pasta',
  'Pizza',
  'pizza',
  'Risotto',
  'Pasta',
  'Pizza'
  ]);
const staffUnique = [...new Set(orderSet)];
// 长度
console.log(new Set('liaoyihuidexingming').size);

```

### Map----一种数据结构用来将值映射到键  ------new Map()----可迭代的
和对象不同的一点是，map中的键可以是任何类型的，而对象中的键只是字符串，并且map不能存储方法！！！

- [x] 通过**<font style="color:#C41D7F;">.set（）</font>**向map里添加元素

```javascript
const rest = new Map();
rest.set('name', 'yihui');
rest
  .set('year', 23)
  .set('country', 'china')
  .set(true, 'I am not so happy today')
  .set(false, 'I dont want sleep')
  .set(document.querySelector('h1'),'Heading');
```

- [x] 通过**<font style="color:#C41D7F;">.get（属性名）</font>**获得map对应属性的值
- [x] 通过.**<font style="color:#C41D7F;">has（属性名</font>**）判断该map中是否有这个属性
- [x] 通过**<font style="color:#C41D7F;">.delete（属性名）</font>**删除map对应的属性
- [x] 通过**<font style="color:#C41D7F;">.size</font>**获得这个map所拥有的属性个数

##### 甚至可以将事件、html元素作为键
##### 数组作为键的话，要定义一个变量存储这个数组，否则，无法从这样的map中获得该数组的值（因为数组的值在堆中而数组在栈中？？！！）
#### 向map中添加元素的新的方法
```javascript
const question = new Map([
  ['question', 'what is the best programming language in the world?'],
  [1, 'C'],
  [2, 'java'],
  [3, 'Javascript'],
  ['correct', 3],
  [true, 'Correct🎉'],
  [false,'Try again!😉']
]);
```

#### 通过<font style="color:#C41D7F;">new Map( Object.entries() )</font>将对象转为map
```javascript
const hoursMpa = new Map(Object.entries(openingHours))
```

#### 迭代，循环---[key,value]
```javascript
for (const [key, value] of question) {
  if (typeof key === 'number') console.log(`Answer ${key}: ${value}`);
}
```

#### 通过扩展运算符...将map转为数组
```javascript
console.log([...question]);
console.log([...question.keys()]);
console.log([...question.values()]);
console.log([...question.entries()]);
// 同样可以用.keys（），.values（），.entries（）
```

### 不同数据结构的应用场合
不同数据结构的优缺点以及何时用什么样的数据

![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1666091457403-7fddb2f0-a58e-41d8-8247-e10e3fe4eae4.jpeg)

#### 数据的来源
1. 源代码
2. UI界面，用户交互输入
3. API，从别的网页或者程序获得的数据

用不同的数据结构来存储不同的数据

最常见的四种数据结构：数组/集合，对象/maps

#### 数组 vs 集合  &&  对象 vs  maps
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1666092941417-5eb46479-0f57-417b-a921-f2cff8ed058b.jpeg)

##### 数组
- [x]  当你需要**<font style="color:#C41D7F;">有顺序的列表</font>**（可以包含重复值）
- [x] 当你需要**<font style="color:#C41D7F;">操纵/处理数据</font>**时---没法从集合中获得特定的数据，最多只能循环

##### 集合
- [x]  但你需要**<font style="color:#389E0D;">独一无二</font>**的值时（一个集合中没有重复的值）
- [x] 当**<font style="color:#389E0D;">高效、高性能</font>**非常重要时
- [x] 当需要从数组中**<font style="color:#389E0D;">去除重复值</font>**时

##### 对象
- [x] 更加**传统的key/value **的存储方式
- [x] 更容易使用**<font style="color:#CF1322;"> . </font>**或者 **<font style="color:#CF1322;">[] </font>**来写或者获取数据
- [x] 当你需要**<font style="color:#CF1322;">存储函数（方法）</font>**时 (可以使用this）
- [x] 当数据格式是<font style="color:#CF1322;">JSON格式</font>时

##### maps
- [x] **<font style="color:#531DAB;">性能更好</font>**
- [x] **<font style="color:#531DAB;">keys可以是任何的数据类型</font>**
- [x] **<font style="color:#531DAB;">可迭代</font>**
- [x] **<font style="color:#531DAB;">更容易计算大小（size)</font>**
- [x] 当只想<font style="color:#531DAB;">简单地将值和键对应起来</font>时
- [x] 当你需要**<font style="color:#531DAB;">非字符串格式的键</font>**时

### 字符串
#### 基本使用
- [x] 获值：类似于数组，通过**<font style="color:#C41D7F;">[index]</font>**来获值---**这里的index不能是负数**
- [x] 长度：**<font style="color:#C41D7F;"> .length</font>**函数
- [x] 获得索引函数：**<font style="color:#C41D7F;">.indexOf（），返回指定字符串首次出现的位置索引，如果没找到返回-1</font>**
- [x]  **<font style="color:#C41D7F;">.lastIndexOf（）</font>**
- [x] **<font style="color:#C41D7F;">.slice( 起始索引，结束索引 </font>**) 函数；**<font style="color:#DF2A3F;">提取字符串的部分</font>**，<font style="color:#22075E;">结束索引可以不写</font>，且索引可以是**<font style="color:#22075E;">变量</font>**；如果是**<font style="color:#22075E;">负数</font>**，那就表示从后往前

```javascript
const airline = 'tapa air protugal';
const plane = 'A230';

console.log(plane[0]);  // A
console.log(plane[1]);  // 2
console.log(plane.length);  // 4

console.log(airline.indexOf('r'));  // 7
console.log(airline.lastIndexOf('a')); // 15
console.log(airline.indexOf('air'));  //# 5

console.log(airline.slice(7));  // r protugal
console.log(airline.slice(2, 7)); // pa ai
// 利用空格通过 indexOf 和 lastIndexOf 以及 slice 来获得单词
// 获得第一个单词
console.log(airline.slice(0, airline.indexOf(' ')));  // tapa
// 获得最后一个单词
console.log(airline.slice(airline.lastIndexOf(' ') + 1)); // protugal
console.log(typeOf new String('yihui'));  // ---object 
```

#### string是原型，我们之所以可以对字符串进行上述的一系列操作，是因为js自动进行了<font style="color:#C41D7F;">装箱</font>（boxing）--将原始类型包装成了对象类型
#### 当将一个原始值（字符串类型、布尔类型或者数字类型）来当做this的绑定对象，这个原始值会被转化为它的对象形式（也就是 new String(....)等），这通常被称为<font style="color:#C41D7F;">装箱</font>。
#### 字符串的其他函数
- [x] 转小写： **<font style="color:#C41D7F;">.toLowerCase( )</font>**;
- [x] 转大写：**<font style="color:#C41D7F;"> .toUpperCase( )</font>**;
- [x] 获取**字符串指定位置字符的Unicode**编码：**<font style="color:#D22D8D;">.charCodeAt( )</font>**；
- [x] 修剪函数：**<font style="color:#C41D7F;">.trim( ）</font>**---去除字符串两边的非字符串内容，如空白、换行符\n，**<font style="color:#C41D7F;">但不会改变原字符串，返回新的字符串</font>**
- [x] 替换函数： **<font style="color:#C41D7F;">.replace( '被替换的字符'，‘字符’)</font>**
- [x] **<font style="color:#C41D7F;">.replaceAll( ) </font>**函数，将字符串中的所有这个字符串替换掉
- [x] 通过**<font style="color:#C41D7F;">正则表达式</font>**来实现replaceAll函数的功能---**<font style="color:#531DAB;">/door/g</font>**

```javascript
const announcement =
  'All passengers come to boarding door 23, Boarding door 23!';
console.log(announcement.replace(/door/g, 'gate')); //  /door/表示是字符串格式，
// g表示全局，也就是选择了该字符串中的所有door都被替换
```

- [x]  **<font style="color:#C41D7F;">.includes(字符串）</font>**函数，如果包含该字符串，返回true否则，返回false
- [x] **<font style="color:#C41D7F;">.startWith(字符串)</font>** 函数，如果是，则返回true，否则false
- [x] .endwith( )
- [x] **<font style="color:#C41D7F;">.split( ) 函数  ，</font>**可以将字符串分割为多个部分 --返回字符串数组

```javascript
console.log('a+b+liao+yi+hui'.split('+'));     //['a', 'b', 'liao', 'yi', 'hui']
// 直接将分割的结果存储在变量中
const [firstName, lastName] = 'yihui liao'.split(' ');

```

- [x] **<font style="color:#C41D7F;"> .join(字符串) 函数 </font>** ：将字符串数组里的**<font style="color:#1D39C4;">字符串元素通过‘字符串’整合为一个字符串 </font>** ，‘字符串`也可以不写
- [x] **<font style="color:#C41D7F;">.concat()方法：</font>**可以把多个参数（参数类型和个数没有限制）添加到指定字符串的**尾部**，会把所有的参数都转换为字符串，**该方法不会改变原字符串**。

```javascript
const newName = ['Miss.', firstName, lastName.toUpperCase()].join(' ');
console.log(newName); // Miss. yihui LIAO
```

- [x] **<font style="color:#C41D7F;"> .padStart(目标长度，'填充的字符' ) 函数</font>** ：往字符串前添加特定的字符，直到达到目标长度
- [x] **<font style="color:#C41D7F;"> .padEnd(目标长度，'填充的字符' ) 函数</font>** ：往字符串末尾添加特定的字符，直到达到目标长度
- [x] **<font style="color:#C41D7F;">.repeat(重复的数量)：返回指定重复数量拼接在一起的字符串</font>**
- [x] **<font style="color:#C41D7F;">.raw() 返回不转义的原始字符串</font>** 
- [x] **<font style="color:#C41D7F;">.search()方法</font>**：

#### 还有很多别的函数，可以自己去网站上查找
#### +号作用时，只要里面有一个元素是字符串，返回的整个结果就会是字符串；如 数字 + 字符串=字符串
##  函数
### 默认参数
```javascript
const creatBooking = function (
  flightNum,
  numPassengers = 1,   //这里设置了默认值
  price = 199 * numPassengers
) {
  const booking = {
    flightNum,
    numPassengers,
    price,
  };
};

creatBooking('LH123') //当没有传入参数时，保留默认值
creatBooking('LH123',undefined,1000) //传入undefined，保留该位置的默认值，
//可以跳过该位置设置后面的参数的值！！
    
```

#### js中都是按值传递，即使对象看起来是像按引用传递，其实还是按值传递，只不过这个传递的值是地址（<font style="color:#C41D7F;">js中没有按引用传递</font>）
## 一等函数（函数优先）和高阶函数
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1666529172564-ccdd1982-414d-4da1-9563-bba47dd9f2f3.jpeg)

#### 一等函数
1. **js将函数视为一等函数**
2. **一等函数意味着函数仅仅是一个简单的****<font style="color:#C41D7F;">值</font>**
3. **函数只是另外一种形式的****<font style="color:#C41D7F;">对象</font>****-----****<font style="color:#C41D7F;">它本身有各种属性，可以通过对象的方式操作</font>**

#### 高阶函数
1. **是一种****<font style="color:#C41D7F;">接收其函数作为参数（回调函数）</font>****，或者****<font style="color:#C41D7F;">返回一个新的函数</font>****，或者****<font style="color:#C41D7F;">两者</font>****都有的函数**
2. **只有拥有一等函数的语言才有高阶函数**

```javascript
const greet = function (greeting) {
  return function (name) {
    console.log(`${greeting} ${name}`);
  };
};
const greetHey = greet('hey');
greetHey('Jonas');

greet('Hello')('Liao');  //柯里化（需再了解学习）
```

#### 闭包：函数在定义时的词法作用域以外的地方被调用。闭包使得函数可以继续访问定义时的词法作用域。
## 立即执行函数表达式
#### 定义：（函数声明/匿名表达式、箭头函数）（）----函数申明被用一个括号包裹起来从而成为了一个函数表达式（function不在第一位），然后在函数表达式后面添加一个（），表示立即执行该函数，无需调用
#### 可以实现调用一次之后彻底消失，且不会污染作用域！（async和awit--后面要学）
```javascript
//写法1：一般函数声明写法
(function never() {
  console.log('this function will never run again');
})();
//写法2：不用写函数名
(function () {
  console.log('this function will never run again');
})();
//写法3：箭头函数
(() => console.log('this function will never run again'))();
```

- [x] 无法从外部访问（）内部的变量，是被封装在（）里的

## 闭包
#### 函数在定义时的词法作用域以外的地方被调用。闭包使得函数可以继续访问定义时的词法作用域。
**<font style="color:rgb(64, 64, 64);">闭包（Closure）</font>**<font style="color:rgb(64, 64, 64);"> </font><font style="color:rgb(64, 64, 64);">是指</font><font style="color:rgb(64, 64, 64);"> </font>**<font style="color:rgb(64, 64, 64);">一个函数</font>**<font style="color:rgb(64, 64, 64);"> </font><font style="color:rgb(64, 64, 64);">能够</font><font style="color:rgb(64, 64, 64);"> </font>**<font style="color:rgb(64, 64, 64);">记住并访问它被创建时的作用域</font>**<font style="color:rgb(64, 64, 64);">，即使这个函数在它原本的作用域之外执行。</font>

#### **<font style="color:rgb(64, 64, 64);">核心特点：</font>**
1. **<font style="color:rgb(64, 64, 64);">函数嵌套</font>**<font style="color:rgb(64, 64, 64);">：闭包通常发生在函数内部返回另一个函数时。</font>
2. **<font style="color:rgb(64, 64, 64);">变量保持</font>**<font style="color:rgb(64, 64, 64);">：内部函数可以访问外部函数的变量，即使外部函数已经执行完毕。</font>
3. **<font style="color:rgb(64, 64, 64);">私有变量</font>**<font style="color:rgb(64, 64, 64);">：闭包可以用来模拟私有变量，避免全局污染。</font>

![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1666622767131-cd7d9128-43a5-4783-a804-3c1276afc98f.jpeg)

#### 查看变量环境：console.dir(变量)
```javascript
const secureBooking = function () {
  let passengerCount = 0;

  return function () {
    passengerCount++;
    console.log(`${passengerCount} passengers`);
  };
};

const booker = secureBooking();

booker();
```

```javascript
let f;

const g = function () {
  const a = 23;
  f = function () {
    console.log(a * 2);
  };
};
f();
```

#### setTimeout(函数，时间)---这个函数会在'时间'后执行，独立于其他的函数，实现了闭包
```javascript
const boardPassengers = function (n, wait) {
  const perGroup = n / 3;

  setTimeout(function () {
    console.log(`We are now boarding all ${n} passengers`);
    console.log(`There are 3 groups, each with ${perGroup} passengers`);
  }, wait * 1000);

  console.log(`Will start boarding in ${wait} seconds`);
};

const perGroup = 1000;
boardPassengers(180, 3);
// 事件监听--当点击时，这个函数才运行！！竟然可以运行，这就是闭包吗！
(function () {
  const header = document.querySelector('h1');
  header.style.color = 'red';

  document.querySelector('body').addEventListener('click', function () {
    header.style.color = 'blue';
  });
})();
// 本来是一个即刻执行表达式，但是添加了事件，实现了闭包，
```

## 数组
### 数组方法
数组本身也是对象，他们可以访问一些特殊的内置方法

- [x] **<font style="color:#C41D7F;">.slice( 起始索引，结束索引 </font>**) 函数取值，不包括结束索引；<font style="color:#22075E;">结束索引不写默到数组结尾</font>，且索引可以是**<font style="color:#22075E;">变量</font>**；如果是**<font style="color:#22075E;">负数</font>**，那就表示从后往前。**<font style="color:#08979C;">slice不会改变原来的数组</font>**，会返回一个新的数组，可以利用slice，做<font style="color:#08979C;">浅拷贝（不传递参数）</font>
- [x] **<font style="color:#C41D7F;">.splice（index, length,新元素（可选））拼接函数</font>**；用于添加或删除数组中的元素。**<font style="color:#E8323C;">splice会直接改变原来的数组</font>**；index是从该位置（包括该位置）开始删除，length是要删除的长度，新元素是在index位置插入的新元素。

```javascript
arr.splice(-1)
```

- [x] **<font style="color:#C41D7F;">.reverse( )函数</font>**：数组元素顺序反向，改变原始数组！
- [x] **<font style="color:#C41D7F;">.concat( ) 函数：</font>**按顺序拼接两个数组，不改变原数组
- [x] **<font style="color:#C41D7F;"> .join(字符串) 函数 </font>** ：将数组里的**<font style="color:#1D39C4;">元素通过‘字符串’整合为一个元素 </font>** 

#### 2023新操作函数
##### <font style="color:#D22D8D;">with（index，value）</font>：用新值替换数组指定索引处的值，返回一个新数组
+ index：要修改的数组索引（从 0 开始），将会转换为整数。
        * <font style="color:#DF2A3F;">负数索引会从数组末尾开始计数——即当 index < 0 时，会使用 index + array.length</font>。
        * 如果规范化后的索引超出数组边界，会抛出 RangeError。
+ value：要分配给指定索引的任何值。

##### <font style="color:#D22D8D;">toSpliced（start，deleteCount，item1，item2）</font>：与splice相同，但结果不改变原数组，返回一个新数组
##### <font style="color:#D22D8D;">toReversed</font>：与reverse相同，但不改变原数组，返回一个新数组
##### <font style="color:#D22D8D;">toSorted</font>：与sort相同，但不改变原数组，返回一个新数组
#### **<font style="color:#C41D7F;">.at ( index )方法</font>**（ES2022的新方法）--index可以为负数，负数表示从后往前---该方法同样适用于字符串！
```javascript
// arr.at(0)等价于 arr.at(0)
//当不知道数组长度时
arr.at(-1) 等价于 arr[arr.length-1]
```

#### <font style="color:#08979C;">数组forEach（function(mov , i , arr )）</font>循环---mov是循环的当前元素，i 是当前索引，arr 是整个数组元素--命名不重要，顺序不能变
```javascript
// Looping Arrays: forEach
const movements = [200, 450, -400, 3000, -650, -130, 70, 1300];

// for (const movement of movements) {
for (const [i, movement] of movements.entries()) {
  if (movement > 0) {
    console.log(`Movement ${i + 1}: You deposited ${movement}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(movement)}`);
  }
}
//math.abs表示返回输入参数的绝对值
console.log('---- FOREACH ----');
movements.forEach(function (mov, i, arr) {
  if (mov > 0) {
    console.log(`Movement ${i + 1}: You deposited ${mov}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(mov)}`);
  }
});
```

#### <font style="color:#08979C;">forEach</font> 同样适用于<font style="color:#08979C;">map（映射）和集合</font>
+ map，<font style="color:#E8323C;">有value和key（顺序不可变</font>）
+ set，没有key，因此前<font style="color:#E8323C;">两个变量都是value</font>

```javascript
// Map
const currencies = new Map([
  ['USD', 'United States dollar'],
  ['EUR', 'Euro'],
  ['GBP', 'Pound sterling'],
]);

currencies.forEach(function (value, key, map) {
  console.log(`${key}: ${value}`);
});

// Set
const currenciesUnique = new Set(['USD', 'GBP', 'USD', 'EUR', 'EUR']);
console.log(currenciesUnique);
currenciesUnique.forEach(function (value, _, map) {
  console.log(`${value}: ${value}`);
});
*/
```

### 操作返回数组方法：MAP、FILTER、REDUCE
#### **<font style="color:rgb(232, 62, 140);background-color:rgb(246, 246, 246);">map()</font>**<font style="color:rgb(0, 0, 0);"> 方法---循环数组的另一中方法--</font><font style="color:#389E0D;">-创建一个新数组</font><font style="color:rgb(0, 0, 0);">，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。</font>
```javascript
const numbers = [1, 5, 10, 15];
const doubles = numbers.map(x => x * 2;);   //箭头函数表示方法
//const doubles = numbers.map(function(x) {
  // return x * 2;
//});
// doubles is now [2, 10, 20, 30]
// numbers is still [1, 5, 10, 15]
```

和forEach类似，function中也可以接受三个参数：**<font style="color:#389E0D;">当前元素、index索引和整个数组</font>**

##### <font style="color:#389E0D;">forEach的副作用是，原数组在改变，而map方法不会改变原数组，而是得到新的数组，新数组是原始数组中每个元素进行函数计算之后的一对一映射</font>
##### 并且，要想存储forEach操作后得到的数组只能在循环过程中用push方法一个个添加得到新的数组


#### <font style="color:#C41D7F;">filter() </font><font style="color:rgb(77, 77, 77);">方法--过滤满足条件的元素，创建一个</font><font style="color:rgb(254, 44, 36);">新的数组（不改变原数组）</font><font style="color:rgb(77, 77, 77);">，</font><font style="color:rgb(77, 168, 238);">原数组的</font><font style="color:rgb(77, 77, 77);">每个元素传入</font>[回调](https://so.csdn.net/so/search?q=%E5%9B%9E%E8%B0%83&spm=1001.2101.3001.7020)<font style="color:rgb(77, 77, 77);">函数中，回调函数中有return返回值，若返回值为true，这个元素保存到新数组中；若返回值为false，则该元素不保存到新数组中；原数组不发生改变。</font>
```javascript
const withdrawal = movements.filter(function (mov) {
  return mov < 0;
});
// const withdrawal = movements.filter(mov => mov < 0;);
//返回小于mmovement中小于0的元素，放入withdrawal中
```

#### <font style="color:rgb(77, 77, 77);">  
</font><font style="color:#C41D7F;">reduce()</font><font style="color:rgb(85, 85, 85);background-color:rgb(245, 245, 245);">方法用于对数组元素进行迭代（累加），会对数组中的所有元素调用指定的回调函数作为累加器，数组中的每个值（从左到右）开始缩减，最终计算为一个值。---将数组简化为一个值 </font>
```javascript
const balance = movement.reduce(function(previousValue,currentValue,curretIndex,arry){
  return previousValue+currentValue},0);
// 0 表示设置初始值为0，从0开始加
```

```javascript
const max = movements.reduce(function (acc, mov) {
  if (acc > mov) return acc;
  else return mov;
});//此时的acc就是每次比较的最大值
```

1. <font style="color:rgb(43, 51, 59);">previousValue：通过上一次调用回调函数获得的值。如果向 reduce() 方法提供 initialValue，则在首次调用函数时，previousValue 默认为数组第一个元素的值。</font>
2. <font style="color:rgb(43, 51, 59);">currentVaule：当前元素数组的值。</font>
3. <font style="color:rgb(43, 51, 59);">currentIndex：当前数组元素的数字索引。</font>
4. <font style="color:rgb(43, 51, 59);">array：包含该元素的数组对象。</font>
5. <font style="color:rgb(43, 51, 59);">initialValue：可省略的参数，传递给函数的初始值。省略的话，默认从数组的第一个元素开始加。</font>

### find方法--基于条件来检索元素（循环数组）
和filter类似但是有两个根本上的不同

- [x] find方法不会创建新数组，而只会返回数组中第一个满足条件的元素
- [x] find方法只会返回元素本身，而不是数组
- [x] 没找到返回undefined

### findIndex方法--返回找到元素的索引，没有找到对应元素，返回-1
和find方法类似

### some方法----判断数组中是否有满足条件的值，如果有返回true，否则返回false
和includes作用类似，可以实现includes

```javascript
const anyDeposits = movements.some(mov => mov > 1500);
```

### every方法--如果数组中所有的元素都满足条件则返回true
```javascript
const result = movements.every(mov => mov > 0);
```

### 分离调用------把条件（函数）存储在变量里，调用变量
```javascript
const request = mov => mov > 0;
console.log(movements.some(request));
console.log(movements.every(request));
console.log(movements.filter(request));
```

### .flat(展平的层数n)方法：将嵌套m层的数组的前n层展平为一个数组
### flatMap（fun）方法：只能<font style="color:#D22D8D;">展平一层</font>，循环，展开map
```javascript
const overalBalance2 = accounts.flatMap(acc => acc.movements)
// 将5个accounts中的每一个账户数组展开为一个
```

### .sort(fun() )方法：将字符串数组元素按照a-z、（A-Z)、0-9、负-正，重新排序--改变原数组。
#### .sort((a,b) => {}); 如果返回小于0的值，A排在B前（保持原序）；如果返回大于0的值，则B排在A前（变换顺序）---改变条件实现递增排序和递减排序
```javascript
// 递增排序
movements.sort((a,b) => {
  // if(a>b) return 1;
  // if (a<b) return -1;
  // 等价于返回
  a-b;
})
// 递减排序
movements.sort((a,b) => {
  // if(a>b) return -1;
  // if (a<b) return 1;
  // 等价于返回
  b-a；
})
```



## bankist项目
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1666683893812-f5a5ba22-4f5c-496d-9bbc-d9ceb9c3b2b6.jpeg)

### 1、通过forEach函数和insertAdjacentHTML函数和innerHTML函数实现js，根据获得的动态控制HTML页面movement的数量、内容以及顺序(提前先写好html和css模板)
// 最好不要在全局变量中直接做某件事情，最好要在一个函数里做！！不然会特别混乱

```javascript
const displayMovement = function (movements) {
  // 利用innerHTML将原HTML元素的值设置为空白
  containerMovements.innerHTML = '';//删除了原来的HTML元素
  movements.forEach(
    function (mov, i) {
      // 通过分析知道页面中存在可控的变量：type是deposit或者withdrawal，以及data和value的值
      const type = mov > 0 ? 'deposit' : 'withdrawal';
      const html = `
    <div class="movements__row">
    <div class="movements__type movements__type--${type}">${i + 1} ${type}</div>
    <div class="movements__value">${mov}</div>
  </div>`;
      containerMovements.insertAdjacentHTML('afterbegin', html);
    }
    // 通过.insertAdjacentHTML将html元素添加到我们想要添加的html位置中去
  );
};
displayMovement(account1.movements);
```

- [x] **<font style="color:#389E0D;">.innerHTML函数：</font>**<font style="color:rgb(77, 77, 77);">JS是双向功能：</font>**<font style="color:rgb(77, 77, 77);">获取对象的内容  或  向对象插入内容</font>**<font style="color:rgb(77, 77, 77);">；</font>
- [x] .**<font style="color:#389E0D;">insertAdjacentHTML函数：</font>****<font style="color:#C41D7F;">将指定的文本解析为HTML或XML，并将结果节点插入到DOM树中的指定位置</font>**<font style="color:rgb(0, 0, 0);">。它不会重新解析它正在使用的元素，</font><font style="color:#C41D7F;">因此它不会破坏元素内的现有元素</font><font style="color:rgb(0, 0, 0);">。这避免了额外的序列化步骤，使其比直接innerHTML操作更快。</font>
+ 用法：**<font style="color:#096DD9;">element.insertAdjacentHTML(position, text)</font>**;  <font style="color:#389E0D;">text:一段字符串，此方法会将其解析为节点对象，然后插入目标元素指定位置</font><font style="color:rgb(0, 0, 0);">；</font><font style="color:#389E0D;">positon:规定被插入的位置的关键字；</font>
    1. <font style="color:rgb(0, 0, 0);">beforebegin：插入到当前元素前面，作为前一个同胞节点。</font>
    2. **<font style="color:#9254DE;">afterbegin：插入当前元素内部，作为新的子节点或放在第一个子节点前面。</font>**
    3. **<font style="color:#9254DE;">beforeend：插入当前元素内部，作为新的子节点或放在最后一个子节点后面。</font>**
    4. <font style="color:rgb(0, 0, 0);">afterend：插入当前元素后面，作为下一个同胞节点。</font>

### 2、给log in的箭头添加click事件，实现用户名、密码登录显示、计算
- [x] e.preventDefault( ) :防止网页重新提交表单
- [x] inputLoginPin.blur( ) :  移除文本域的焦点（光标位置）

```javascript
// 给每个用户对象中添加一个user属性，是owner的每个单词第一个字母的小写缩写
accounts.forEach(function (acc) {
  acc.user = acc.owner
    .toLocaleLowerCase()
    .split(' ')
    .map(word => word[0])
    .join('');
});
// console.log(account1);
// displayMovement(account1.movements);
// balance---计算movements中所有数据的总和
const displayBlance = function (movements) {
  const sum = movements.reduce((acc, mov) => acc + mov);
  labelBalance.textContent = `${sum}€`;
  // console.log(sum);
};
const displaySummary = function (accont) {
  // in
  const income = accont.movements
    .filter(mov => mov > 0)
    .reduce((acc, mov) => acc + mov);
  labelSumIn.textContent = `${income}€`;
  // out
  const outcome = accont.movements
    .filter(mov => mov < 0)
    .reduce((acc, mov) => acc + mov);
  labelSumOut.textContent = `${Math.abs(outcome)}€`;
  // interst
  const interest = accont.movements
    .filter(mov => mov > 0)
    .map(deposit => (deposit * accont.interestRate) / 100)
    .filter((int, i, arr) => {
      // console.log(arr);
      return int >= 1;
    })
    .reduce((acc, int) => acc + int, 0);
  labelSumInterest.textContent = `${interest}€`;
};
// 为login的箭头添加click事件
let account;
btnLogin.addEventListener('click', function (e) {
  // preventDefault 防止自动重新提交表单
  e.preventDefault();
  account = accounts.find(acc => acc.user === inputLoginUsername.value);
  // 因为如果没有找到，find会返回false，此时acount.pin会报错，加一个？.，可以优雅地解决报错问题！妙蛙！
  if (account?.pin === Number(inputLoginPin.value)) {
    // 清除log in文字
    inputLoginUsername.value = inputLoginPin.value = '';
    // login之后的鼠标光标还是在pin上，所以清除一下
    inputLoginPin.blur();
    labelWelcome.textContent = `Welcome back, ${account.owner.split(' ')[0]}`;
    containerApp.style.opacity = 100;
    displayMovement(account.movements);
    displayBlance(account.movements);
    displaySummary(account);
  }
});
```

## 以编程方式创建和填充数组
### Arry.from( )方法：将一个类数组对象或者可遍历对象转换成一个真正的数组。
- [x] **<font style="color:#E8323C;background-color:rgb(238, 240, 244);">Array.from(arrayLike， mapFn， thisArg)</font>**
1. **<font style="color:#4C16B1;">arrayLike：</font>**<font style="color:rgb(77, 77, 77);">想要转换成数组的</font>**<font style="color:rgb(77, 77, 77);">伪数组对象或可迭代对象</font>**<font style="color:rgb(77, 77, 77);">。</font>
2. **<font style="color:#4C16B1;">mapFn 可选函数</font>****<font style="color:rgb(77, 77, 77);">：</font>**<font style="color:rgb(77, 77, 77);">如果指定了该参数，</font>**<font style="color:rgb(77, 77, 77);">新数组中的每个元素会执行该回调函数</font>**<font style="color:rgb(77, 77, 77);">。</font>
3. **<font style="color:#4C16B1;">thisArg 可选</font>****<font style="color:rgb(77, 77, 77);">：</font>**<font style="color:rgb(77, 77, 77);">可选参数，</font>**<font style="color:rgb(77, 77, 77);">执行回调函数 mapFn 时 this 对象</font>**<font style="color:rgb(77, 77, 77);">。</font>
4. **<font style="color:rgb(77, 77, 77);">返回值：</font>****<font style="color:#4C16B1;">一个新的s数组实例。</font>**

```javascript
let arrayLike = {
    0: 'tom', 
    1: '65',
    2: '男',
    3: ['jane','john','Mary'],
    'length': 4
}
let arr = Array.from(arrayLike)
console.log(arr) // ['tom','65','男',['jane','john','Mary']]
```

从UI界面获得数据的同时处理好，返回得到一个干净的数组

```javascript
const movementsUI =Array.from(document.querySelectorAll('.movements_value'),
                              el=> Number(el.textContent.replace('€','')));
// 另外也可以用扩展数组的方法实现从ui界面获得数据数组
const movementsUI2 = [...document.querSelectorAll('.movements_value')];
```

#### 将类数组对象转化为真正的数组对象
- [x] <font style="color:rgb(0, 0, 0);">要将一个类数组对象转换为一个真正的数组，必须具备以下条件：</font>  
<font style="color:rgb(0, 0, 0);">1、该类数组对象必须具有</font>**<font style="color:#0C68CA;">length属性</font>**<font style="color:rgb(0, 0, 0);">，</font>**<font style="color:rgb(0, 0, 0);">用于指定数组的长度</font>**<font style="color:rgb(0, 0, 0);">。如果没有length属性，那么转换后的数组是一个</font>**<font style="color:rgb(0, 0, 0);">空数组</font>**<font style="color:rgb(0, 0, 0);">。</font>  
<font style="color:rgb(0, 0, 0);">2、该类数组对象的属性名必须为</font>**<font style="color:rgb(0, 0, 0);">数值型</font>**<font style="color:rgb(0, 0, 0);">或</font>**<font style="color:rgb(0, 0, 0);">字符串型</font>**<font style="color:rgb(0, 0, 0);">的</font>**<font style="color:#AD1A2B;">数字</font>**  
<font style="color:rgb(0, 0, 0);">ps: 该类数组对象的属性名可以加引号，也可以不加引号</font>

### <font style="color:#D22D8D;">.fill( value,start ,end) </font><font style="color:rgb(0, 0, 0);">填充数组：用一个固定值填充一个数组中从起始索引到终止索引内的全部元素。不包括终止索引。返回修改后的原始数组，</font><font style="color:#D22D8D;">不创建新数组</font><font style="color:rgb(0, 0, 0);">。</font>
1. <font style="color:rgb(0, 0, 0);">value </font><font style="color:#AD1A2B;">用来填充数组元素的值，必填</font><font style="color:rgb(0, 0, 0);">。</font>
2. <font style="color:rgb(0, 0, 0);">start </font><font style="color:#AD1A2B;">可选起始索引，默认值为0。</font>
3. <font style="color:rgb(0, 0, 0);">end </font><font style="color:#AD1A2B;">可选</font><font style="color:rgb(0, 0, 0);">终止索引，默</font><font style="color:#AD1A2B;">认值为 this.length</font><font style="color:rgb(0, 0, 0);">。</font>

## 总结
![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1667397315908-0a27999e-9861-4d2b-af4a-789adf7619e7.jpeg)

#### <font style="color:rgb(0, 0, 0);">a++ ：先执行返回a再执行+1  ====所以执行一次a++，返回的仍然是a</font>
#### ++a : 先执行加1再返回 a  ====需要执行++a，才能立刻返回得到加一之后的值
# <font style="color:rgb(0, 0, 0);">DOM</font>
### DOM的工作方式
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1667805743254-8d0fbc3f-0ae9-40b8-a800-257360ca5a2c.png)

#### DOM基本上是所有浏览器和js代码之间的接口
- [x] 可以实现和浏览器的js交互
- [x] 可以通过写js去创造、修改以及删除html元素；设置样式、类以及属性；对事件进行监听和响应
- [x] DOM树是从一个我们可以交互的HTML文档生成的
- [x] DOM是一个非常复杂的API（<font style="color:#4C16B1;">application programming interface</font> <font style="color:#4C16B1;">应用程序编程接口</font>），它包含了许多与DOM树交互的方法和属性

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1667980196408-e57255ba-e4da-485e-adae-e1be33d57d40.png)

### 任何HTM/Xml文档都可以用DOM表示为一个由节点构成的层级结构，节点分很多类型，每种类型对应着文档中不同的信息和（或）标记，也都有自己不同的特性、数据和方法。
#### Node类型
DOM中共有12种节点类型，但所有节点都继承Node类型，所有节点都继承Node的基本属性和方法。

- [x] .textContent
- [x] .childNodes
- [x] .parentNode
- [x] .cloneNode（）

Node类型又继承EventTarget节点

- [x] .addEventListener（）
- [x] .removeEventListener（）

Window类型节点是Node类型的同胞节点，它是全局对象，有许多和DOM不相关的方法和属性

#### Element类型表示HTML元素
- [x] .innerHTML
- [x] .classList
- [x] .children
- [x] .parentElement
- [x] .append( )
- [x] .remove( )
- [x] .insertAdjacentHTML( )
- [x] .querySelector( )
- [x] .closest( )
- [x] .matches( )
- [x] .scorllIntoView( )
- [x] .setArrtibute( )

#### Document类型表示文档类型
- [x] .querySelector( )
- [x] .createElement( )
- [x] .getElementById( )

#### Comment类型表示注释
#### Text类型表示文本
### 选择、创建和删除元素
DOM树通过各种关系指针维系，一个节点不会 在文档中同时出现或者出现在两个或者更多个地方。

#### 选择----通过<font style="color:#4C16B1;">document</font>来实现
- [x] **document.documentElement（返回整个html页面）**
- [x] **document.head**
- [x] **document.body**
- [x] document.anchors（返回Nodelist，包含文档中所有带name属性的<a>元素）
- [x] document.forms（返回文档中所有<form>元素，与document.getElementByTagName(“form”）一样）
- [x] document.images（返回文档中所有<img>元素，与document.getElementByTagName(“img”）一样）
- [x] document.links（返回文档中所有带herf属性的<a>元素）
- [x] **<font style="color:#4C16B1;">document.querySelector('.liu') （选择类名为 liu 的第一个元素）</font>**
- [x] **<font style="color:#4C16B1;">document.querySelector('#liu') （选择id名为 liu 的元素）</font>**
- [x] **<font style="color:#4C16B1;">document.querySelectorAll(.liu') （选择类名为 liu 的所有元素，返回Nodelist）</font>**
- [x] **<font style="color:#AE146E;">document.getElementById('liu') （选择id名为 liu 的元素）</font>**
- [x] **<font style="color:#AE146E;">document.getElementByTagName('button')（选择名称为 button 的所有元素，返回HTMLCollection）</font>**
- [x] **<font style="color:#AE146E;">document.getElementByClassName('btn')（选择类名为 btn 的所有元素，返回HTMLCollection）</font>**

#### HTMLCollection是一种实时集合，如果DOM发生变化，name这个集合会自动更新，而已经返回的NodeList不会更新。
#### 创造、插入和删除元素
- [x] **<font style="color:#8CCF17;">.insertAdjacentHTML( ) </font>****<font style="color:#5C8D07;"> </font>**  [链接](#ueQnB)

> - [ ] .**<font style="color:#389E0D;">insertAdjacentHTML函数：</font>****<font style="color:#C41D7F;">将指定的文本解析为HTML或XML，并将结果节点插入到DOM树中的指定位置</font>**<font style="color:rgb(0, 0, 0);">。它不会重新解析它正在使用的元素，</font><font style="color:#C41D7F;">因此它不会破坏元素内的现有元素</font><font style="color:rgb(0, 0, 0);">。这避免了额外的序列化步骤，使其比直接innerHTML操作更快。</font>
>

- [x]  **<font style="color:#8CCF17;">document.createElement( 'div')  </font>** ：创建了一个div元素（<font style="color:#7E45E8;">在HTML文档中，标签名是不区分大小写的</font>）

```javascript
const div = document.createElement('div')
```

- [x] **<font style="color:#8CCF17;">.innerHTML：</font>**<font style="color:#7E45E8;">将字符串解析为文本格式</font>：---会替换原来的元素

```javascript
div.innerHTML = 'HELLO WORLD!. <button class="btn-btn--close--cookie">Got it!</button>'
// 给div内部添加了文本以及一个按钮
// 就算这个div内部原来有东西，也会被替换成现在的东西
```

- [x] 在新元素上添加<font style="color:#7E45E8;">新的属性</font>：**<font style="color:#8CCF17;">div.id = 'myNewDiv'</font>**
- [x] <font style="color:#7E45E8;">添加已有类属性</font>：**<font style="color:#8CCF17;">div.classList.add('cookie-message')</font>**
- [x] 添加<font style="color:#7E45E8;">文本内容</font>：**<font style="color:#8CCF17;">div.textContent = 'hello world!'</font>**

#### 将元素节点添加到DOM树的指定位置
- [x] **<font style="color:#7E45E8;">appendChild( )</font>**：在<font style="color:#7E45E8;">子节点列表末尾</font>添加该节点
- [x] **<font style="color:#5C8D07;">insertBefore(要插入的节点，参照节点)</font>**：要插入的节点变成参照节点的<font style="color:#7E45E8;">前一个同胞节点</font>，并被返回
- [x] **<font style="color:#5C8D07;">replaceChild(要插入的节点，要替换的节点)</font>**：要替换的节点会被返回，并从DOM树中完全移除，要插入的节点会取而代之
- [x] **<font style="color:#7E45E8;">cloneNode(true/false)</font>**：会返回与调用它的节点一模一样的节点。如果传入true，会进行深度复制，即赋值节点及其整个子DOM树。如果传入false，则只会复制调用该方法的节点，返回的节点没有父节点，会变成孤儿节点。
- [x] **<font style="color:#7E45E8;">header.prepend( div )</font>****<font style="color:#5C8D07;">：</font>**将div添加到header的<font style="color:#7E45E8;">第一个子节点位置</font>
- [x] **<font style="color:#7E45E8;">header.append( div )</font>****<font style="color:#5C8D07;">：</font>**将div添加到header的<font style="color:#7E45E8;">最后一个子节点位置</font>
- [x] **<font style="color:#7E45E8;">header.before( div )</font>**：将div作为header的<font style="color:#7E45E8;">同胞节点插入到header之前</font>
- [x] **<font style="color:#7E45E8;">header.after( div )</font>****<font style="color:#5C8D07;">：</font>**将div作为header的<font style="color:#7E45E8;">同胞节点插入到header之后</font>
- [x] **<font style="color:#7E45E8;">div.remove()</font>**：在DOM树中删除这个节点

### style、attributes 和 classes
#### css样式---style
##### 获取、改变内嵌样式
```javascript
<div class="cookie-message" style="background-color:rgb(55,56,61);width:120%"></div>
const message = document.queruSellector('.cookie-message')
```

- [x] **<font style="color:#5C8D07;">message.style.backgroundColor = '#37383d' </font>**

##### 获取、改变外联样式---css文件中的样式
- [x] **<font style="color:#07787E;">getComputedStyle(message).height</font>**

```javascript
console.log(getComputedStyle(message).height)   //返回的是带单位的字符串，mabey '1489px'
```

- [x] **<font style="color:#07787E;">parseInt() / Number.parseFloat(字符串，进位制)</font>**：提取出最前面的数字部分；没提取出来，那就返回 NaN。
- [x] **<font style="color:#4C16B1;">document.documentElement.style.setProperty('--color-primary' , 'orangered')</font>**
- [x] **<font style="color:#4C16B1;">获得、修改HTML元素的一些标准属性，比如scr、alt等</font>**

```javascript
const logo = document.querySelector('.nav__logo');
console.log(logo.alt);
console.log(logo.src);
console.log(logo.className);
logo.alt='Beatiful minimalist logo' //修改
```

- [x] **<font style="color:#4C16B1;">.getAttribute----获得、修改HTML元素的一些属性（包括标准和自定义的）</font>**
- [x] **<font style="color:#4C16B1;">.setAttibute-----设置或者修改属性（包括标准和自定义的）</font>**

```javascript
<img src="img/logo.png" alt="Bankist logo" class="nav__logo" id="logo" change="Liao"
/>
const change = logo.getArttibute('designer')
logo.setAttribute('company','Liu') //新设置了一个自定义属性，并赋值
```

- [x] **对于****<font style="color:#4C16B1;">地址、链接</font>****（比如，****<font style="color:#4C16B1;">src、href的值</font>****），通过上述两种获得值的方式得到的结果是不一样的，通过****<font style="color:#4C16B1;">getAttribute得到的地址是在HTML中写的地址</font>****（如：img/logo.png）,而第一种方法得到的是****<font style="color:#4C16B1;">绝对地址</font>**
- [x] **<font style="color:#4C16B1;">数据属性：是一种以data开头的特殊数据---这些属性始终存储在dataset中，通过.dataset获得</font>**

```javascript
<img src="img/logo.png" alt="Bankist logo" class="nav__logo" id="logo" change="Liao" data-
  version-Number
/>
console.log(logo.dataset.versionNumber);
```

- [x] **<font style="color:#4C16B1;">classList.add('a', 'j')  ------可以一次处理多个</font>**
- [x] **<font style="color:#4C16B1;">classList.remove('a', 'j') </font>**
- [x] **<font style="color:#4C16B1;">classList.toggle('j') : 如果元素不包含某个类，则向他添加这个类，否则删除这个类</font>**
- [x] **<font style="color:#4C16B1;">classList.contains('a', 'j')  ：</font>**<font style="color:rgb(77, 77, 77);">确定元素中是否包含指定的类名，返回值为true 、false；</font>

### bankist项目2
#### 导航按钮，设置跳转到导航的页面--通过html中的a标签中的链接实现
```javascript
<li class="nav__item">
  <a class="nav__link" href="#section--1">Features</a>
</li>
//这里的href中填的链接是应该要导航到的模块的标签的id
```

#### JS 实现点击按钮，跳转到页面的指定位置
##### 老方法---计算距离----//当前元素到视口的距离+当前视口到html页面顶部的距离
- [x] **window.pageXoffset , window.pageYoffset**：返回页面（整个文档）顶部（左边）距离当前视口顶部（左边）的像素距离（可以理解为向下滚动的像素距离）
- [x] **<font style="color:#01B2BC;">document.documentElement.clientHeight , document.documentElement.clientWidth</font>** : **返回当前视口宽度和视口高度**
- [x] **<font style="color:#07787E;">e.target.getBoundingClientRect( )</font>**：<font style="color:rgb(51, 51, 51);">用于获得页面中</font>**<font style="color:#AE146E;">某个元素</font>**<font style="color:rgb(51, 51, 51);">(</font>**<font style="color:#07787E;">e.target表示的是‘click’事件发生的地方，</font>**~~**<font style="color:#07787E;">而不是当前添加事件的这个元素</font>**~~<font style="color:rgb(51, 51, 51);">）的左，上，右和下分别相对</font>**<font style="color:#07787E;">浏览器视窗</font>**<font style="color:rgb(51, 51, 51);">的位置，以</font>**<font style="color:#07787E;">及元素本身的宽高</font>**
- [x] **<font style="color:#07787E;">slcollTo({left：数值，top：数值，behavior：‘smooth’}</font>**）：实现window滚动----<font style="color:rgb(64, 64, 64);">第一个为X坐标，也就是左右滚动方向，第二个是Y坐标，就是上下滚动坐标  // 滚动数值单位是css 像素单位</font>

```javascript
const btnScrollTo = document.querySelector('.btn--scroll-to');
btnScrollTo.addEventListener('click', function (e) {
  // console.log(window.pageXOffset, window.pageYOffset);
  console.log(
    document.documentElement.clientHeight,
    document.documentElement.clientWidth
  );
  const section1 = document.querySelector('#section--1');
  const sloords = section1.getBoundingClientRect();
  console.log(sloords);
  window.scrollTo({
    left: sloords.left + window.pageXOffset,
    top: sloords.top + window.pageYOffset,
    behavior: 'smooth',
  });
  //当前元素到视口的距离+当前视口到html页面顶部的距离
  // 更先进的方法
  section1.scrollIntoView({behavior:'smooth'})
});
```

##### 现代用法
- [x] **<font style="color:#AE146E;">.scrollIntoView(true/false)</font>**：**<font style="color:rgb(0, 0, 0);background-color:rgb(238, 238, 238);">滚动某个元素，进入浏览器的可见区域（视口）</font>**
+ <font style="color:rgb(0, 0, 0);background-color:rgb(238, 238, 238);">该方法可以接受一个布尔值作为参数。</font>
+ <font style="color:rgb(0, 0, 0);background-color:rgb(238, 238, 238);">如果为true，表示元素的顶部与当前区域的可见部分的顶部对齐（前提是当前区域可滚动）；</font>
+ <font style="color:rgb(0, 0, 0);background-color:rgb(238, 238, 238);">如果为false，表示元素的底部与当前区域的可见部分的尾部对齐（前提是当前区域可滚动）。</font>
+ <font style="color:rgb(0, 0, 0);background-color:rgb(238, 238, 238);">如果没有提供该参数，默认为true</font>
+ **<font style="color:#AE146E;">.scrollIntoView({behavior:'smooth'})</font>**----让滚动更丝滑

### 事件类型和事件句柄（envent handlers）
#### MDN网站上可以查到各种事件
#### 事件句柄，又称为事件处理函数。
指事件发生时要进行的操作；将相应函数或语句指定给事件句柄，则在该事件发生时，浏览器便执行指定的函数或语句，从而实现网页内容与用户操作的交互。

#### 过去常用的一种添加事件的方法：h1.mouseenter = function(e){alert('GREAT!')}
```javascript
const h1 = document.querySelector('h1')
h1.click = function(e){
  alert('GREAT!')}
h1.mouseenter = function(e){
  alert('GREAT!')}
```

### 现在常用.addEventListener方法、
#### 1. 允许同时添加多个事件监听器，而第二种方法，如果添加两个，后一个会覆盖前一个
```javascript
const h1 = document.querySelector('h1');
h1.addEventListener('mouseout', function (e) {
  alert('what1?');
});
h1.addEventListener('click', function (e) {
  alert('what12?');
});
```

#### 2.  当我们不需要某个操作函数或者语句，我们可以删除它
```javascript
const alertH1 = function (e) {
  alert(`what H1!`);
  h1.removeEventListener('click', alertH1);
};
h1.addEventListener('click', alertH1);
```

### 事件传递机制
1. **<font style="color:rgb(64, 64, 64);">一个完整的js事件流是从window开始，最后回到window的过程；</font>**
2. <font style="color:rgb(64, 64, 64);">从window开始到事件（</font>**<font style="color:rgb(64, 64, 64);">事件捕获</font>**<font style="color:rgb(64, 64, 64);">）；</font>
3. <font style="color:rgb(64, 64, 64);">从事件到window（</font>**<font style="color:rgb(64, 64, 64);">事件冒泡</font>**<font style="color:rgb(64, 64, 64);">），这个过程会按顺序执行该事件的所有父级，于是</font>**<font style="color:#AE146E;">强大的处理诞生了</font>**<font style="color:rgb(64, 64, 64);">（我们还可以在它的父级设计一些操作，冒泡就能执行！）</font>

![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1668320226880-42f49e9b-4b18-4d6a-9e86-a29758985872.jpeg)

#### 事件冒泡
- [x] **<font style="color:#07787E;">Math.floor() </font>**<font style="color:rgb(77, 77, 77);">返回小于或等于一个给定数字的最大整数。</font>

```javascript

// 实现给定范围内的随机整数
const randomInt = (min, max) =>
  Math.floor(Math.random() * (max - min + 1) + min);
const randomColor = () =>
  `rgb(${randomInt(0, 255)},${randomInt(0, 255)},${randomInt(0, 255)})`;
document.querySelector('.nav').addEventListener('click', function (e) {
  this.style.backgroundColor = randomColor(); //这里的this指代的是添加click事件的元素！
  console.log(e.target, e.currentTarget);
  // 这里的e.target指的是click事件发生的地方，在冒泡过程中e.target都一样，
  //而e.currentTarget和this表示的相同，在冒泡过程中不一样
	e.stopPropagation()
});
document
  .querySelector('.nav__links')
  .addEventListener('click', function (e) {
    this.style.backgroundColor = randomColor(); //这里的this指代的是添加click事件的元素！
    console.log(e.target, e.currentTarget);
    // 这里的e.target指的是click事件发生的地方，在冒泡过程中e.target都一样，而e.currentTarget和this表示的相同，在冒泡过程中不一样
  });
document.querySelector('.nav__link').addEventListener('click', function (e) {
  this.style.backgroundColor = randomColor(); //这里的this指代的是添加click事件的元素！
  console.log(e.target, e.currentTarget);
  // 这里的e.target指的是click事件发生的地方，在冒泡过程中e.target都一样，而e.currentTarget和this表示的相同，在冒泡过程中不一样
});

```

- [x] **<font style="color:#07787E;">e.target</font>****表示的是事件发生的地方，****在冒泡过程中e.target都一样**
- [x] **<font style="color:#07787E;">e.currentTarget和this</font>****表示的相同，在冒泡过程中不一样**
- [x] **<font style="color:#07787E;">事件监听中的this指代的都是添加click事件的元素</font>**！
- [x] **e.stopPropagation()停止事件传播**，就不会改变父级元素的背景颜色----一般不用
- [x] **.addEventListener(e, function(){}, true)**：传入true参数，事件处理程序不再监听冒泡事件，而监听捕获过程（也可以改变父元素，但是顺序不一样）----一般用冒泡

### 事件委托
#### <font style="color:rgb(51, 51, 51);">是在DOM上层（也就是在触发事件的元素的</font><font style="color:#AD1A2B;">父元素</font><font style="color:rgb(51, 51, 51);">上）定义事件的处理程序，而不是定义在触发事件的元素本身上。</font>
```javascript
// 当页面中有很多元素都需要这个效果时，不适用，处理效率太低
// document.querySelectorAll('.nav__link').forEach(function (btn) {
//   btn.addEventListener('click', function (e) {
//     e.preventDefault(); //添加了这个之后，原来在html a标签中写的href跳转就不起作用了
//     // 直接获得每个元素的href值，它就是想要跳转到的页面的id
//     const id = this.getAttribute('href');
//     document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
//   });
// });
// 方法2，事件委托，找到共同的父级元素，只要在这个父级元素上添加语句即可实现
document.querySelector('.nav__links').addEventListener('click', function (e) {
  e.preventDefault();
  // 这个父级元素可能还会包含许多不需要这个操纵的元素，所以这里需要进行元素筛选匹配
  // e.target是事件发生的地方，也就是点击了哪个按钮
  if (e.target.classList.contains('nav__link')) {
    const id = e.target.getAttribute('href');
    document.querySelector(id).scrollIntoView({ behavior: 'smooth' });
  }
});
```

### DOM元素的遍历
#### 子节点、子元素
```javascript
const h1 = document.querySelector('h1)
```

- [x] **<font style="color:#AE146E;">h1.querySelectorAll('.highlight')</font>**; //返货nodelist，获得相应的子元素
- [x] **<font style="color:#AE146E;">h1.childNodes</font>**; //返回nodelist，子节点
- [x] **<font style="color:#AE146E;">h1.children</font>**; //返回HTMLCollection,返回h1里包含的HTLM元素
- [x] **<font style="color:#AE146E;">h1.lastChild;</font>** //返回节点
- [x] **<font style="color:#AE146E;">h1.lastElementChild;</font>** //返回HTML元素：**h1.firstElementChild.style.color='orangered'**

#### 父元素
- [x] **<font style="color:#AE146E;">h1.parentNode</font>**
- [x] **<font style="color:#AE146E;">h1.parentElement</font>**
- [x] **<font style="color:#AE146E;">closest(' ') </font>**：**<font style="color:#4C16B1;">方法返回被选元素的第一个父级元素</font>**
+ h1.closest('.header').style.background = 'var(--gradient-secondary)'
+ h1.closest('h1')返回的是它自己

#### 同胞节点、同胞元素
- [x] **<font style="color:#AE146E;">h1.previousElementSibling;</font>**--如果没有则返回null
- [x] **<font style="color:#AE146E;">h1.nextElementSibling;</font>**
- [x] **<font style="color:#AE146E;">h1.previousSibling;</font>**
- [x] **<font style="color:#AE146E;">h1.nextSibling;</font>**
- [x] **<font style="color:#AE146E;">h1.parentElement.children-</font>**---返回所有他的同胞元素，返回HTMLCollection，可以解构成[...h1.parentElement.children]

### 标签组件效果
#### 卫语句：[https://blog.csdn.net/ljl86400/article/details/79885093](https://blog.csdn.net/ljl86400/article/details/79885093)
<font style="color:rgb(77, 77, 77);">如果条件语句极其复杂，就应该将条件语句拆解开，然后逐个检查，并在条件为真时立刻从函数中返回，这样的单独检查通常被称之为“卫语句”（guard clauses）</font>

#### closest函数
### 导航效果
```javascript
nav.addEventListener('mouseover', handleHover.bind(0.5));
nav.addEventListener('mouseout', handleHover.bind(1));
// 这里俺也不知道为什么e是怎么传递进去的，难道真的是bind复制原来的函数，原来的函数本来就有e！！
//好像也很有道理
```

### 实现导航栏始终保持在页面上方（当滚动页面时）
#### 方法1：实际上<font style="color:#AE146E;">在滚动事件上执行一些语句非常不可行</font>，因为滚动时刻发生（发生密集），处理太过频繁，性能不好，尤其是在移动设备上。要做防抖或节流
- [x] **window.scrollY：页面向下滚动的距离**

```javascript
const initialCoords = section1.getBoundingClientRect();
window.addEventListener('scroll', function (e) {
  // 当页面向下滚动的距离超过section1最开始距离视口的距离时，添加sticky类
  if (window.scrollY > initialCoords.top) nav.classList.add('sticky');
  else nav.classList.remove('sticky');
});
```

#### 方法二：通过 <font style="color:#E8323C;">IntersectionObserver API</font><font style="color:rgb(34, 34, 38);"> 来实现</font>
###  <font style="color:#E8323C;">IntersectionObserver API</font>
####  提供了一种异步观察<font style="color:#4C16B1;">目标元素</font>与其<font style="color:#4C16B1;">祖先元素</font>或<font style="color:#4C16B1;">顶级文档视窗(viewport)交叉状态</font>的方法。祖先元素与视窗(viewport)被称为根(root)。---可以实现懒加载、内容无限滚动等功能
简单来说是监听目标元素与其祖先或视窗交叉状态的手段，其实就是**<font style="color:#E8323C;">观察一个元素是否在视窗可见</font>**。

[https://www.ruanyifeng.com/blog/2016/11/intersectionobserver_api.html](https://www.ruanyifeng.com/blog/2016/11/intersectionobserver_api.html)

```javascript
// 创建实例
const observer = new IntersectionObserver(callback, 
                                          option);
 
// 开始观察element1
observer.observe(element1);
 
// 开始观察element2
observer.observe(element2);
 
// 停止观察
observer.unobserve(element);
 
// 关闭观察器
observer.disconnect();
```

#### callback参数---可见性变化时的可见函数
当以下情况发生时会调用回调函数：

<font style="color:rgb(17, 17, 17);background-color:#FFC0CB;">callback</font><font style="color:rgb(17, 17, 17);background-color:rgb(245, 245, 213);">一般会触发两次。一次是目标元素刚刚进入视口（开始可见），另一次是完全离开视口（开始不可见）。--所以语句中需要用到卫语句-----当isIntersecting是真的时候，才执行下面的语句</font>

- [x] observer第一次监听目标元素的时候
- [x] 每当目标元素与设备视窗或者其他指定元素发生交集的时候执行（移入和移除都会触发）

**callback函数的参数（entries，observer）**

- [x] **entries**：是一个**数组，每个成员都是一个IntersectionObserverEntry对象**。举例来说，如果<font style="color:#00346B;">同时有两个被观察的对象的可见性发生变化</font>，entries数组就会有<font style="color:#00346B;">两个成员</font>。

每个IntersectionObserverEntry对象属性含义如下：

+ **boundingClientRect**：目标元素的矩形区域的信息
+ **intersectionRatio**：目标元素的可见比例，即intersectionRect占boundingClientRect的比例，完全可见时为1，完全不可见时小于等于0
+ **intersectionRect：**目标元素与视口（或根元素）的交叉区域的信息
+ **rootBounds：**根元素的矩形区域的信息，getBoundingClientRect()方法的返回值，如果没有根元素（即直接相对于视口滚动），则返回null
+ **isIntersecting：**目标元素是否与视口（或根元素）交叉
+ **isVisible**：并未查阅到相关资料，且经过测试其并不会发生变化
+ **target：**被观察的目标元素，是一个 DOM 节点对象
+ **time：**可见性发生变化的时间，是一个高精度时间戳，单位为毫秒

#### option--可选参数---配置对象
IntersectionObserver构造函数的第二个参数是一个配置对象。它可以设置以下属性。

+ **<font style="color:#AE146E;">root</font>**：指定根元素，用于检查目标是否与根元素相交。必须是目标元素的父级元素。如果**未指定或者为null**，则默认为**<font style="color:#AE146E;">浏览器视窗</font>**。
+ **<font style="color:#AE146E;">rootMargin</font>**：根元素的外边距，类似于 CSS 中的margin属性，单位可以用“px”或者百分比（如果root有固定的数值？）。
+ **<font style="color:#AE146E;">threshold</font>**：**<font style="color:#AE146E;">目标元素与根元素的交叉比例</font>**，可以是单一的 number 也可以是 number 数组，比如，[0, 0.25, 0.5, 0.75, 1]就表示当目标元素 0%、25%、50%、75%、100% 可见时（**<font style="color:#AE146E;">交叉</font>**），**<font style="color:#AE146E;">会触发回调函数</font>**

#### 注意点
+ **<font style="color:rgb(51, 51, 51);">IntersectionObserver API</font>****<font style="color:rgb(51, 51, 51);"> </font>**<font style="color:rgb(51, 51, 51);">是异步的，不随着目标元素的滚动同步触发。</font>
+ <font style="color:rgb(51, 51, 51);">注册的回调函数将会在主线程中被执行，所以该函数执行速度要尽可能的快。如果有一些耗时的操作需要执行，建议使用 </font>[Window.requestIdleCallback()](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestIdleCallback)<font style="color:rgb(51, 51, 51);"> 方法。</font>

#### 页面懒加载
- [x] 注意是：entry.target 以及当所有页面都加载出来之后，就可以不用观察了，**<font style="color:#07787E;">observer.unobserve(entry.target</font>**)---停止观察

```javascript
  entry.target.classList.remove('section--hidden');
  observer.unobserve(entry.target);
```

#### 图片懒加载-----load事件
```javascript
  entry.target.src = entry.target.dataset.src; //这里会触发加载事件-load
  // 如果在这里直接去除lazy类，当网速很慢时，加载还未完成，blur就去掉了，不好看，
//所以需要用到load事件，当load事件完成之后再去掉blur，用户体验感更好
  // entry.target.classList.remove('lazy-img');
  entry.target.addEventListener('load', function (e) {
    entry.target.classList.remove('lazy-img');
  });
```

#### 滑块组件实现----13-Advwanced-DOM-Bankist
```javascript
document
    .querySelector(`.dots__dot[data-slide="${curSlider}"]`)
//在这里选择了含有dots__dot类的组件中有data-slide="${curSlider}"属性的组件
```

```javascript
const imgTargets = document.querySelectorAll('img[data-src]'); 
//选择了所有的img标签中有data-src属性的标签！！
```

### DOM生命周期   
[https://deepin.lolimay.cn/2021/01/20/web/DOM%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E4%BA%8B%E4%BB%B6/](https://deepin.lolimay.cn/2021/01/20/web/DOM%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E4%BA%8B%E4%BB%B6/)

<font style="color:rgb(47, 47, 47);">时间先后关系：</font>

1. **<font style="color:#07787E;background-color:rgb(246, 248, 250);">DOMContentLoaded</font>**<font style="color:rgb(47, 47, 47);"> ——通过 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">document.addEventListener('DOMContentLoaded', handler)</font><font style="color:rgb(47, 47, 47);"> 监听。当浏览器已完全加载 HTML，并构建了 DOM 树时触发，但像 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);"><img /></font><font style="color:rgb(47, 47, 47);"> 和 css 样式表这些外部资源可能还未加载完成。 注意：当文档中遇到 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);"><script /></font><font style="color:rgb(47, 47, 47);"> 标签时，</font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">DOMContentLoaded</font><font style="color:rgb(47, 47, 47);"> 事件会等待脚本完全执行结束后再触发。除非带有是 </font>[async/defer](https://javascript.info/script-async-defer)<font style="color:rgb(47, 47, 47);"> 属性的脚本或者通过 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">document.createElement('script')</font><font style="color:rgb(47, 47, 47);"> 创建的脚本（这些脚本会异步加载并执行，不会阻塞 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">DOMContentLoaded</font><font style="color:rgb(47, 47, 47);"> 事件）。</font>
2. **<font style="color:#07787E;background-color:rgb(246, 248, 250);">load</font>**<font style="color:rgb(47, 47, 47);"> ——通过 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">window.onload</font><font style="color:rgb(47, 47, 47);"> 监听。当浏览器不仅完全加载 HTML，图片样式表这些外部资源也加载完成后触发。</font>
3. **<font style="color:#07787E;background-color:rgb(246, 248, 250);">beforeunload</font>**<font style="color:rgb(47, 47, 47);"> ——通过 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">window.onbeforeunload</font><font style="color:rgb(47, 47, 47);"> 监听。表示用户正在离开，我们可以检查用户是否保存了更改，并询问他是否真的要离开。</font>
4. **<font style="color:#07787E;background-color:rgb(246, 248, 250);">unload </font>**<font style="color:rgb(47, 47, 47);">——通过 </font><font style="color:rgb(47, 47, 47);background-color:rgb(246, 248, 250);">window.onunload</font><font style="color:rgb(47, 47, 47);"> 监听。表示用户已经离开，我们可以做一些善后工作。</font>

## 加载script脚本的不同方式：常规、async、defer
#### [中文详解](https://juejin.cn/post/6908315682404843528)
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1669642451824-1f47861d-206d-4234-ba24-3f198f4de59e.png)

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1669642833650-e24d981c-177d-4393-98b0-3e78c460438c.png)

- [x] **<font style="color:#AE146E;">defer</font>**可以保证head中的js脚本**按照书写的顺序执行**
- [x] **<font style="color:#AE146E;">async</font>**当head中js脚本与**执行先后顺序无关**时，可以使用
- [x] defer和async**不支持老的浏览器**，老的浏览器需要用常规方法将js脚本放到body的最后，减小阻塞
- [x] defer和async加载js文件时都**不会阻塞页面渲染**（也就是**<font style="color:#07787E;background-color:rgb(246, 248, 250);">DOMContentLoaded阶段</font>**）

# 面向对象编程
[js面向对象编程详解](https://juejin.cn/post/6844904082210045965)

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1670136259254-cf38dcc5-ef77-4bc2-a09d-80c902e147be.png)

### 四个基本原则
- [x] **<font style="color:#5C8D07;">抽象：</font>**忽略或者隐藏不重要的细节，以至于我们可以对我们正在实施的事情有一个总览  (而不是搞乱那些对我们的实施并不重要的细节)
- [x] **<font style="color:#5C8D07;">封装</font>**：在类中保持属性和方法私有，以至于他们不能从类的外部访问。一些方法可以被暴露作为公共界面（API）
- [x] **<font style="color:#5C8D07;">继承</font>**：基于类之间的继承关系，可以使某个类的所有属性和方法对子类可用。这允许我们重用一些公共的逻辑并模拟现实世界的关系
- [x] **<font style="color:#5C8D07;">多态性</font>**：子类可以覆盖它从父类继承的方法

##  js中三种实现面向对象编程的方法
- [x] **<font style="color:#AE146E;">构造函数</font>**
- [x] **<font style="color:#AE146E;">ES6引入的 class</font>**
- [x] **<font style="color:#AE146E;">object.create( )</font>**

![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1670140330633-aa444897-0940-495d-84d8-85c8c9a9fcae.png)

### 构造函数
- [x] 构造函数**名字总是大写字母开头**
- [x] 构造函数可以是**<font style="color:#4C16B1;">函数申明式</font>**也可以是**<font style="color:#4C16B1;">函数表达式</font>**，但是不能是箭头函数，因为箭头函数没有自己的this，而我们需要（一般用**函数申明式**）
- [x] 通过关键字**<font style="color:#AE146E;">new</font>**调用构造函数
- [x] 通过这种方式调用构造函数会执行以下5个重要步骤！
1. 在内存中创建一个**新对象**
2. 构造函数内部的**this被赋值为这个新对象（****<font style="color:#AE146E;">即 this 指向新对象）</font>**
3. **这个新对象内部的[[prototype]]特性被复制为构造函数的prototype**（也就是**<font style="color:#AE146E;">通过.__proto__链接到原型对象</font>**）
4. 执行构造函数内部的代码（给新对象添加属性--属性名一般和传入的参数名匹配）
5. **如果构造函数返回非空对象，则返回该对象，****<font style="color:#AE146E;">否则，返回刚创建的新对象！</font>**

```javascript
const Person = function (firstName, birthDay) {
  this.firstName = firstName;
  this.birthDay = birthDay;
};
const Liao = new Person('YiHui', 18);
console.log(Liao);

// Person {firstName: 'YiHui', birthDay: 18}
// birthDay: 18
// firstName: "YiHui"
// [[Prototype]]: Object
// constructor: ƒ (firstName, birthDay)
// [[Prototype]]: Object
```

#### <font style="color:#74B602;">instanceof</font>  ----- 用来判断某个对象是否是某个构造函数的实例，如果是，返回true，否则返回，false
```javascript
console.log(Liao instanceof Person);
```

#### 永远也不要在构造函数内为实例添加方法。因为每构建一个实例就需要创建一次函数！通常通过原型和原型链来解决。----把函数创建放在原型上
### 原型
js中的每个函数都有一个原型属性（prototype） 

#### <font style="color:#AE146E;">Person.prototype </font>=> Person构造函数的<font style="color:#AE146E;">原型</font>
#### <font style="color:#AE146E;">Person.prototype.constructor</font> => Person构造函数
#### <font style="color:#AE146E;">Liao.__proto__</font> => Person构造函数的<font style="color:#AE146E;">原型</font>（Liao是person的一个实例）
#### 实例与构造函数原型之间有直接的联系，但实例与构造函数之间没有！
#### <font style="color:#74B602;">isPrototypeOf</font>（）函数：<font style="color:rgb(37, 41, 51);">用于判断</font><font style="color:#C75C00;">当前对象</font><font style="color:rgb(37, 41, 51);">是否为</font><font style="color:#C75C00;">另外一个对象的原型</font><font style="color:rgb(37, 41, 51);">，如果是就返回 true，否则就返回 false。</font>
```javascript
console.log(Person.prototype.isPrototypeof(Liao));
```

#### <font style="color:#74B602;">.hasOwnProperty( )</font> <font style="color:rgb(37, 41, 51);">判断一个对象</font><font style="color:#E746A4;">是否包含自定义属性（自定义或者写在构造函数里的）</font><font style="color:rgb(37, 41, 51);">而</font><font style="color:#E746A4;">不是原型链上本身拥有的属性</font>
```javascript
console.log(Liao.hasOwnProperty('birthDay'));
```

#### 原型链
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1670151326081-18ab70e2-389c-4547-862d-7a4ebefb9da1.png)

- [x]  <font style="background-color:rgb(252, 252, 250);">console.dir()可以显示一个对象所有的属性和方法。</font>

### ES6 class-----更方便的语法，但是原理还是原型链
<font style="color:rgb(51, 51, 51);">class 声明创建一个</font>**<font style="color:rgb(51, 51, 51);">基于原型继承</font>**<font style="color:rgb(51, 51, 51);">的</font>**<font style="color:rgb(51, 51, 51);">具有给定名称的</font>****<font style="color:#5C8D07;">新类</font>**

<font style="color:rgb(51, 51, 51);">类是块作用域</font>

#### class表达式
```javascript
class PersonCl = class{}
```

#### class申明式
```javascript
class PersonCl {
  constructor(firstName, birthYear) {
    // 写在constructor内的属性或者方法
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
  // 写在constructor外的属性或者方法将被加在原型上，也被称为在命名空间内。
  // 实例方法
  calAge() {
    console.log(2022 - this.birthYear);
  }
} 
// 使用class
const Liao = new PersonCl('yihui',18)
```

##### <font style="color:#AE146E;">constructor（构造方法）</font>
1. 构造方法在创建新对象时会自动执行
2. 构造方法用于初始化对象属性
3. 如果不定义构造方法，js会自动添加一个空的构造方法

##### <font style="color:#AE146E;">写在constructor之外的属性或者方法将被加在原型上！！</font>
#### 1、不能在申明类之前使用类！！
#### 2、class也是一等函数
#### 3、class中定义的代码都在严格模式下执行
### 访问器属性：setter和getter属性
js中的所有对象都有两种属性：数据属性和访问器属性

#### <font style="color:rgb(77, 77, 77);">在 Class 内部可以使用</font><font style="color:#DF2A3F;">get</font><font style="color:rgb(77, 77, 77);">和</font><font style="color:#DF2A3F;">set</font><font style="color:rgb(77, 77, 77);">关键字， 对某个属性设置</font><font style="color:#DF2A3F;">存值函数</font><font style="color:rgb(77, 77, 77);">和</font><font style="color:#DF2A3F;">取值函数</font><font style="color:rgb(77, 77, 77);">， 拦截该属性的存取行为。---适用于</font><font style="color:#74B602;">数据验证</font><font style="color:rgb(77, 77, 77);">。</font>
```javascript
class MyClass {
	constructor() {
		// ...
	}
	get prop() {
		return 'getter';
	}
	set prop(value) {
		console.log('setter: ' + value);
	}
}
let inst = new MyClass();
inst.prop = 123;
// setter: 123
inst.prop
	// 'getter'
```

**<font style="color:#4C16B1;">prop在</font>****<font style="color:#D22D8D;">实例对象</font>****<font style="color:#4C16B1;">上是作为</font>****<font style="color:#AE146E;">属性值</font>****<font style="color:#4C16B1;">存在而不是方法                                                                                    </font>**

### 静态方法---只有<font style="color:#AE146E;">类本身</font>可以拥有并调用(不能被实例继承）
用关键词”**<font style="color:#4C16B1;">static</font>**

```javascript
class PersonCl {
  constructor(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
  // 写在constructor外的属性或者方法将被加在原型上--实例成员
  calAge() {
    console.log(2022 - this.birthYear);
  }
  // 静态方法，实例都不能继承
  static hey() {
    console.log(`liu k pig 🤞`);
  }
}
```

### <font style="color:#4C16B1;">Object.create(原型对象)</font>--<font style="color:rgb(27, 27, 27);">用于创建一个新对象，使用</font><font style="color:#4C16B1;">现有的对象来作为新创建对象的原型</font>
可以把任意一个对象作为原型！---他返回一个有继承但是内容为空的对象

```javascript
// object.creat方法没有定义函数！而是写了一个对象
const PersonProto = {
  calcAge() {
    console.log(2022 - this.birthYear);
  },
  init(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  },
};
const liao = Object.create(PersonProto);
// console.log(liao);
liao.name = 'yh';
liao.birthYear = '1998';
// liao.calcAge();
const liu = Object.create(PersonProto);
liu.init('k', '1997');
liu.calcAge();
```

```javascript
const Car = function (make, speed) {
  this.make = make;
  this.speed = speed;
};
Car.prototype.accelerate = function () {
  this.speed += 10;
  console.log(`${this.make} is going at ${this.speed}km/h`);
};
const EV = function (make, speed, charge) {
  // 通过构造函数定义时直接绑定this调用
  // 这里只是调用，不是继承
  Car.call(this, make, speed);
  this.charge = charge;
};
// 这里的EV并没有和Car绑在一起，没有继承Car中的任何属性，
// 通过Object.create使得EV的原型对象继承Car的原型对象，才能继承Car中的属性，此时EV才能被称为Car的子类
// EV是构造函数，Tesla是实例
EV.prototype = Object.create(Car.prototype);
EV.prototype.chargeBattery = function (chargeTo) {
  this.charge = chargeTo;
};
const Tesla = new EV('Tesla', 120, 23);
Tesla.accelerate();
```

### CLASS之间的继承---object.create()--ES6 Classes方法
#### 当原型链中有相同名字的方法或者属性时，js会使用他最先找到的那一个
<font style="color:rgb(77, 77, 77);"></font>

#### <font style="color:#DF2A3F;">通过extends和super实现继承</font>
- [x] <font style="color:#AD1A2B;">ES6 先将父类实例对象的属性和方法，加到this上面（所以必须先调用super方法），然后再用子类的构造函数修改this。</font>
- [x] <font style="color:#AD1A2B;">子类的构造函数中，只有调用super之后，才可以使用this关键字，否则会报错</font>

```javascript
class PersonCl {
  constructor(firstName, birthYear) {
    this.firstName = firstName;
    this.birthYear = birthYear;
  }
  calAge() {
    console.log(2022 - this.birthYear);
  }
}

class StudentCL extends PersonCl {
  // 这里需要写和父级相同的参数，以及其他参数
  constructor(fullName, birthYear, course) {
    super(fullName, birthYear);
    // super继承，写父类的参数
    this.course = course;
  }
  // calAge() {
  //   console.log(`${2022 - this.birthYear},and new!!`);
  // }
}

const liao = new StudentCL('YIHUI', 1998, 'computer');
console.log(liao.course);
liao.calAge();
```

#### 当子类中没有定义其他参数或者方法,super方法会被默认添加
```javascript
class StudentCL extends PersonCl {
  // constructor(fullName, birthYear, course) {
  //   super(fullName, birthYear);
  //   this.course = course;
  // }
  // calAge() {
  //   console.log(`${2022 - this.birthYear},and new!!`);
  // }
}

// const liao = new StudentCL('YIHUI', 1998, 'computer');
const liao = new StudentCL('YIHUI', 1998);
console.log(liao);
```

## 数据隐私和数据封装
### 封装--保护属性和方法（使其无法从外部被访问或者修改）
- [x] <font style="color:#DF2A3F;">this._movement</font>（约定俗成，下划线开头的属性表示是需要保护的属性）

#### 类的私有属性和方法(4种）---私有域和私有方法以 <font style="color:#DF2A3F;">#</font> 为标记符
##### <font style="color:rgb(4, 12, 40);">私有属性不能继承</font><font style="color:rgb(32, 33, 36);">，但是可以</font><font style="color:#DF2A3F;">通过子类继承父类的方法来访问父类的私有属性</font>
- [x] 公共域
- [x] 私有域
- [x] 公共方法
- [x] 私有方法

```javascript
class Account {
  // 1、公共域（被每个实例继承，跟写在constructor里是一样的）
  locale = navigator.language;
  // 2、私有域---以#为标识符，设为私有属性，无法在类外访问
  #movement = [];
  #pin;
  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.#pin = pin;
  }
  // 3、公共方法，一般的写法都是公共方法
  requestLoan(val) {
    console.log(`wow! test!`);
  }
  // 4、私有方法，以#为标记
  #approveLoan(val) {
    return true;
  }
}
```

#### 区分类的静态属性（方法）和私有属性（方法）----没有理解的特别好
[https://blog.csdn.net/m0_73888268/article/details/127007880](https://blog.csdn.net/m0_73888268/article/details/127007880)

##### 静态方法和静态属性------关键词：<font style="color:#DF2A3F;">static</font>
1. 通过关键词static定义的属性/方法是类自己的属性/方法，而不是定义在实例对象（this）上的属性/方法
2. 存放在类（构造函数）的键值对中，与类的原型prototype同级
3. **<font style="color:#DF2A3F;">类可以直接在类上进行调用(可以在外部调用访问），子类可以继承与调用，但是类的实例不能继承与调用</font>**
4. 如果静态方法包含**<font style="color:#2F4BDA;">this关键词，这个this指的是类，而不是实例</font>**

##### 私有属性和私有方法-------关键词：<font style="color:#DF2A3F;"> #</font>
1. 私有属性和方法，只能在**类的内部访问，外部不能访问，this指向实例对象**
2. **<font style="color:#DF2A3F;">在实例中，无法继承访问私有方法</font>**，可以通过继承的方法来访问私有属性和私有方法
3. **<font style="color:#DF2A3F;">子类不能继承私有属性和私有方法</font>**，无法直接调用，可以通过继承方法来访问私有属性和私有方法

### 方法链
```javascript
class Account {
  constructor(owner, currency, pin) {
    this.owner = owner;
    this.currency = currency;
    this.movements = [];
    this.pin = pin;
  }
  deposit(val) {
    this.movements.push(val);
    // 在这里加一个return this，可以实现方法链
    return this;
  }
  withdraw(val) {
    this.deposit(-val);
    return this;
  }
acc1.deposit(-300).withdraw(20).withdraw(80).deposit(900)
```

## Class总结
[https://juejin.cn/post/7168762384000122888](https://juejin.cn/post/7168762384000122888)

![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1672145612811-bbc46133-7c63-4fbf-b311-21f50aec200d.jpeg)

#### class中的<font style="color:#DF2A3F;">public、private、protected</font>关键词
[https://blog.csdn.net/weixin_43334673/article/details/137915063](https://blog.csdn.net/weixin_43334673/article/details/137915063)

# Mapty项目
### <font style="color:rgb(64, 64, 64);">Geolocation API---获取用户地理位置信息</font>
[Geolocation API介绍](https://www.jianshu.com/p/74c73e3d10c2)

### lefleaft---地理位置信息可视化（地图）
[lefleaft介绍](https://zhuanlan.zhihu.com/p/27012917)

[官方网站和教程文档](https://leafletjs.com/reference.html)

#### 任意一个JS文件中的全局变量都可以在<font style="color:#213BC0;">该文件之前加载的js文件</font>中被访问
### 本地存储数据API----localStorage（仅适用于很小的数据）


# 异步（异步是什么？可以在后台运行的代码，不阻塞）
## AJAX调用(Asynchronous JavaScript And Xml)
#### 公共API（application programming interface）:[地址](https://github.com/public-apis/public-apis/blob/master/README.md)
CORS表示跨域资源共享，设置为yes或者unkown才能用，如果没有这个的话，那我们就无法访问第三方API

- [x] **异步代码在后台运行的任务完成后执行**
- [x] **异步代码是非阻塞的**
- [x] **执行不等待异步任务完成其工作**

 online api/第三方api

如今，大多数的api都是用json格式数据

#### 网页工作：请求和回应
请求-响应模型/客户端-服务器架构（P249class）

### 回调地狱（callback hell）
很多嵌套的函数调用

## Promises 和 Fetch API
#### promise不会阻塞代码的运行，而是会在后台加载，同步代码继续往前
![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676707751530-3c7a13e7-b287-4a09-9c49-3a749f46c2e8.jpeg)

解决回调地狱的问题---**<font style="color:#DF2A3F;">fetch</font>**方法！！

**<font style="color:#DF2A3F;">then方法</font>**可以传入两个函数======》**<font style="color:#DF2A3F;">then(成功函数，失败函数)</font>**

![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676707781519-cecf4afa-a0a9-4d42-bcde-73e9947b0757.jpeg)

#### promise请求成功
- [x]  json()方法将获得的response转化为可读的json格式的数据
- [x] data就是对应的获得的数据--但是为啥和返回的response.json()不一样呢？
- [x]  **<font style="color:#DF2A3F;">then</font>**每个then都获得上一步返回的数据

#### then收到的也是promise resolve或者reject的返回值
- [x] 不再是调用里面调用，调用嵌套调用导致调用地狱，而是，把调用的结果return出来，进行下一步！！明白！

```javascript
const getCountryData = function (country) {
  fetch(`https://restcountries.com/v3.1/name/${country}`)
    .then(response => response.json())
    .then(data => {
      console.log(data);
      renderCountry(data[2]);
      //   邻国
      const neighbour = data[2].borders[2];
      if (!neighbour) return;
      return fetch(`https://restcountries.com/v3.1/alpha/${neighbour}`);
    })
    .then(response => response.json())
    .then(data => {
      console.log(data);
      renderCountry(data[0], 'neighbour');
    });
};
getCountryData('china');
```

- [x] .then返回任意一个非promise对象都会被包装成，promise.solve对象，即使它是error
- [ ] ![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1715915439918-985823d4-971d-44d8-8443-333995603cd4.png)

#### 处理reject的promise---------在promise链的最后添加<font style="color:#DF2A3F;">catch方法</font>
- [x] 可以在then 里面传入失败函数，也可以用catch方法
- [x] catch方法可以捕捉发生在promise链中的任何地方的错误
- [x] catch方法只会在捕捉到错误后触发
- [x] **<font style="color:#DF2A3F;">console.erro</font>****（而不是console.log()）**可以追踪到是在哪一步捕捉到了错误
- [x] **<font style="color:#AE146E;">err.message</font>**显示具体原因

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1676131190105-7014f703-a6e2-49ff-8451-99c504fc4db0.png)

#### finally()方法---放在promise链的最后，不管是拒接还是接受，都会执行该方法
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1676187239520-cb87d039-a920-434f-a8f8-71848c58f8e3.png)

#### promise状态改变
- [x] **<font style="color:#DF2A3F;">只能是pending——>resolved 或者 pending——>rejected，改变过一次，状态就不可逆</font>**
- [x] **<font style="color:#DF2A3F;">promise的状态一经改变就会保留，不会再改变！！！</font>**

#### 自定义输出错误原因（有时catch不能捕捉到出错的真正原因）--<font style="color:#DF2A3F;">throw new Error('')</font>
- [x] **response.ok**表示请求成功状态

#### 值透传问题和catch透传
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1746430517575-ad406220-adfa-4561-988b-662b1a27a49f.png)

##### .then 或者 .catch 的参数期望是函数，传入非函数则会发生值透传。
##### 值透传是同步执行的
##### 当使用.catch时，会默认为没有指定失败状态回调函数的.then添加一个失败回调函数。
#####  .catch所谓的异常透传并不是一次失败状态就触发catch,而是一层一层的传递下来的。
#####  异常透传的前提条件是所有的.then都没有指定失败状态的回调函数。 如果.catch前的所有.then都指定了失败状态的回调函数，.catch就失去了意义。
原文链接：[https://blog.csdn.net/u013448372/article/details/110863799](https://blog.csdn.net/u013448372/article/details/110863799)

[Promise 值穿透 特性_promise值穿透-CSDN博客](https://blog.csdn.net/u013448372/article/details/110863799)

#### <font style="color:rgb(255, 80, 44);background-color:rgb(255, 245, 245);">.then</font><font style="color:rgb(37, 41, 51);"> 或 </font><font style="color:rgb(255, 80, 44);background-color:rgb(255, 245, 245);">.catch</font><font style="color:rgb(37, 41, 51);"> 返回的值不能是 promise 本身，否则会造成死循环报错！</font>
### JS异步运行
#### JS是单线程的，永远不可能同时执行多个任务（不会发生多任务处理）
#### 事件循环
![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676707807155-9de08438-4efa-4b57-9b05-280e64d6d66e.jpeg)

![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676707820122-047f36dd-0118-4018-a367-ac7ca0560594.jpeg)

#### 微任务队列（promise 循环）
- [x] 它优先于常规回调队列，回调循环总是先执行微任务队列里的任务，然后再执行回调队列里的任务，如果一直向微任务队列里添加子任务，会导致回调队列饿死-------所以调用setTimeout函数有时并不能准确按时执行
- [x] 异步后台api环境里允许，事件触发后，进入callback队列，promise由自己的微任务队列，优先于常规回调函数队列执行
- [x] <font style="color:rgb(25, 27, 31);">对于一处于pending状态的Promise对象p，内部状态的resolve，会让p.then(fn)中的fn加入微任务队列</font>

#### Promise.resolve（）让某一个promise立刻执行
### <font style="color:rgb(31, 35, 40);">由浅入深探索 Promise 异步执行</font>
首先，看一下 event loop 的基础必备内容

event loop 执行顺序：

+ 首先执行 script 宏任务
+ **<font style="color:#DF2A3F;">执行同步任务，遇见微任务进入微任务队列，遇见宏任务进入宏任务队列</font>**
+ **<font style="color:#DF2A3F;">当前宏任务执行完出队，检查微任务列表，有则依次执行，直到全部执行完</font>**
+ 执行浏览器 UI 线程的渲染工作
+ 检查是否有Web Worker任务，有则执行
+ **<font style="color:#DF2A3F;">执行下一个宏任务，回到第二步，依此循环，直到宏任务和微任务队列都为空</font>**

**微任务包括：**<font style="background-color:#C1E77E;">MutationObserver</font>、<font style="background-color:#C1E77E;">Promise.then()</font>或<font style="background-color:#C1E77E;">catch()</font>、<font style="background-color:#C1E77E;">finally</font>、<font style="background-color:#C1E77E;">Promise</font>为基础开发的其它技术，比如fetch API、V8的垃圾回收过程、Node独有的process.nextTick 、 Object.observe（已废弃；Proxy 对象替代）

**宏任务包括**：<font style="background-color:#C1E77E;">script</font> 、<font style="background-color:#C1E77E;">setTimeout</font>、<font style="background-color:#C1E77E;">setInterval</font> 、<font style="background-color:#C1E77E;">setImmediate</font> 、<font style="background-color:#C1E77E;">I/O </font>、<font style="background-color:#C1E77E;">UI rendering</font> 、 <font style="background-color:#C1E77E;">postMessage</font> 、 <font style="background-color:#C1E77E;">MessageChannel</font>

### Promise构造函数
```javascript
const lotteryPromise = new Promise(function (resolve, reject) {
  console.log('Lotter draw is happing🌟🌟🌟');
  setTimeout(function () {
    if (Math.random() > 0.5) {
      resolve(`You win⛵⛵`);
    } else {
      reject(new Error(`You lost your money  🛤`));
    }
  }, 2000);
});

// lotteryPromise 就是一个promise函数
lotteryPromise.then(res => console.log(res)).catch(err => console.error(err));
```

```javascript
const wait = function (seconds) {
  return new Promise(function (resolve) {
    setTimeout(resolve, seconds * 1000);
  });
};

// wait返回的是一个promise函数
wait(1)
  .then(() => {
    console.log(`1 second passed`);
    return wait(1);
  })
  .then(() => console.log(`2 second passed`));
```

### Async_Await
[Async_Await详解](https://blog.csdn.net/lnmgmgggggdd/article/details/120616652)

#### async关键词创建一个promise，也总是返回一个promise
#### await------改进then()嵌套的写法，可以直接将resolve的结果存储为变量
- [x] 等待右侧表达式的结果，这个结果是promise对象或者其他值。
- [x] 如果它等到的不是一个 promise 对象，那 await 表达式的运算结果就是它等到的东西。
- [x] 如果它等到的是一个 promise 对象，await 就忙起来了，它会**<font style="color:#DF2A3F;">阻塞后面的代码，等着 promise 对象 resolve，然后得到 resolve 的值，作为 await 表达式的运算结果</font>**。
- [x] 但它不能使用catch的方法来处理错误，通常用try_catch（）
- [x] **<font style="color:#DF2A3F;">await 语句 后面的语句相当于.then里的内容，会被加入微任务队列</font>**

```javascript
const WhereAmI = async function () {
  const pos = await getPosition();
};
```

### try_catch 可以与Async_Await配套使用，处理错误
#### catch可以捕获在try中任何地方出现的错误，其内部操作与promise中的catch一样
```javascript
const WhereAmI = async function () {
  try {const pos = await getPosition();}
  catch(err){console.error(err)}
};
```

### async 函数的返回值
#### <font style="color:#DF2A3F;">如果直接return，返回的是一个promise</font>，因为async不阻塞代码，js在promise运行完之前是不知道最终要返回的是什么的
```javascript
const WhereAmI = async function () {
  try {const pos = await getPosition();
      retrue 'Great!'}
  catch(err){console.error(err)}
};
const info = WhereAnI()
```

#### 如果想要获得我们定义的返回值，要用<font style="color:#DF2A3F;">then()</font>的方法
```javascript
const WhereAmI = async function () {
  const pos = await getPosition();
  retrue 'Great!'；
};
WhereAnI().then(info=>console.log(info))
```

#### 另一种解决办法是用<font style="color:#DF2A3F;">顶层await</font>（ES2022才开始可以在模块中）！！
顶层await允许开发人员在异步函数之外使用await关键字

```javascript
const WhereAmI = async function () {
  const pos = await getPosition();
  retrue 'Great!'；
};
const result = await WhereAnI()
```



#### 在async函数中，就算出现的错误，返回的值也是从resolve处的代码中返回，而不会返回reject的结果，解决方法：在async函数的catch中添加 throw err；
##### 因为现实项目中，一个异步函数调用另外一个异步函数是很常见的事情，这样可以确保总是获得了正确的错误！
```javascript
const WhereAmI = async function () {
  const pos = await getPosition();
  retrue 'Great!'；
};
WhereAnI().then(info=>console.log(info))
  .catch(err=>console.error(err.message))
//这样在这里也能捕捉到真正的错误，而不是从resolve代码处返回的undefine
```

### <font style="color:#DF2A3F;">Promise.all</font>([异步函数1],[异步函数2],[异步函数3])-----<font style="color:rgb(77, 77, 77);">该方法用于将</font><font style="color:#DF2A3F;">多个</font><font style="color:rgb(77, 77, 77);">Promise实例，包装成</font><font style="color:#DF2A3F;">一个</font><font style="color:rgb(77, 77, 77);">新的Promise实例</font>
#### 当同时调用多个异步函数，而这些异步函数之间没有关系时，用await方法会拖慢运行速度（因为要等一个运行完才能下一个），而事实上这些可以同时进行，用Promise.all函数，让多个异步函数并行，返回数组
#### 但Promise.all中<font style="color:#AE146E;">只要有一个被reject，一整个都被reject</font>，**<font style="color:rgb(77, 77, 77);">失败的时候则返回</font>****<font style="color:#DF2A3F;">最先被reject失败状态的值</font>**
全部<font style="color:rgb(61, 70, 77);"> </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">fulfilled</font><font style="color:rgb(61, 70, 77);"> 才返回fulfilled的值！</font>

### <font style="color:#DF2A3F;">Promis.race----多个包装成一个</font>
#### **<font style="color:rgb(77, 77, 77);">Promse.race就是赛跑的意思，意思就是说，Promise.race([p1, p2, p3])</font>**<font style="color:rgb(77, 77, 77);">里面</font><font style="color:#AE146E;">哪个结果获得的快，就返回那个结果，不管结果本身是成功状态还是失败状态</font><font style="color:rgb(77, 77, 77);">。</font>
### Promise.allSettled---多个包装成一个
#### <font style="color:rgb(61, 70, 77);">方法返回一个在</font><font style="color:#AE146E;">所有</font><font style="color:rgb(61, 70, 77);">给定的 promise 都已经 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">fulfilled</font><font style="color:rgb(61, 70, 77);"> 或 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">rejected</font><font style="color:rgb(61, 70, 77);"> 后的 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">promise</font><font style="color:rgb(61, 70, 77);">，并带有一个对象数组，每个对象表示对应的 promise 结果。</font>
- [x] <font style="color:rgb(61, 70, 77);">该函数接受一个 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">promise</font><font style="color:rgb(61, 70, 77);"> 数组(通常是一个可迭代对象)作为参数</font>
- [x] <font style="color:rgb(61, 70, 77);">当所有的输入 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">promises</font><font style="color:rgb(61, 70, 77);"> 都被 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">fulfilled</font><font style="color:rgb(61, 70, 77);"> 或 </font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">rejected</font><font style="color:rgb(61, 70, 77);"> 时，</font><font style="color:rgb(199, 37, 78);background-color:rgb(249, 242, 244);">statusesPromise</font><font style="color:rgb(61, 70, 77);"> 会解析为一个具有它们状态的数组：</font>
+ <font style="color:rgb(61, 70, 77);"> 如果对应的promise已经fulfilled----{status:'fulfilled',value:value}</font>
+ <font style="color:rgb(61, 70, 77);">如果相应的promise已经被rejected----{status：‘rejected’，reason：reason}</font>

[深入解析Promise.allSettled()的使用方法-js教程-PHP中文网](https://www.php.cn/js-tutorial-482906.html)

### Promis.any---一样
#### <font style="color:rgb(77, 77, 77);">该方法接受一组 Promise 实例作为参数，包装成一个新的 Promise 实例返回。</font>
#### <font style="color:rgb(77, 77, 77);">只要参数实例</font><font style="color:#AE146E;">有一个变成 fulfilled 状态</font><font style="color:rgb(77, 77, 77);">，包装实例就会变成 </font><font style="color:#AE146E;">fulfilled 状态</font><font style="color:rgb(77, 77, 77);">；如果</font><font style="color:#DF2A3F;">所有</font><font style="color:#AE146E;">参数实例都变成rejected状态</font><font style="color:rgb(77, 77, 77);">，包装实例就会</font><font style="color:#AE146E;">变成rejected状态</font><font style="color:rgb(77, 77, 77);">。</font>
# 现代JS开发
#### npm：<font style="color:rgb(77, 77, 77);">NPM 的全称是 </font>[Node](https://so.csdn.net/so/search?q=Node&spm=1001.2101.3001.7020)<font style="color:rgb(77, 77, 77);"> Package Manager，是随同 NodeJS 一起安装的包管理和分发工具，它很方便让 JavaScript 开发者下载、安装、上传以及管理已经安装的包。</font>
<font style="color:rgb(77, 77, 77);">npm 之于 Node.js ，就像 pip 之于 Python， gem 之于 Ruby， pear 之于 PHP 。</font>

![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676812040381-1705872a-2242-4ea7-ac7a-3453022f1e2f.jpeg)

## 模块--拥有私有数据并有公开的api
#### ES6中一个文件就是一个模块（import和export）----<font style="color:#DF2A3F;">import的过程类似指针</font>而不是复制1!!!!<font style="color:#DF2A3F;">也就是说，被导入的变量会因计算而改变</font>。
#### 有与脚本文件相比，每个模块中的变量是其私有的，外部能访问其变量的唯一方法是模块导出，可以避免全局变量名污染。而js文件中的变量则是全局变量
#### 模块总是在严格模式下的，不需要手动添加
![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676813048026-07da1f4e-ed39-40b0-87f0-2ec92ffa2125.jpeg)

#### import的过程
![](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1676813865349-607dbd73-f832-4df8-aa48-bc756c88770f.jpeg)

### importing和exporting
#### HTML中关联用了模块的js文件，要在引入js代码的文件上加一个type='module'
#### export总是要在顶级环境中发生，否则不生效
#### import的各种情况
- [x] 从模块中import ana、anb、anc（变量或者函数）
- [x] 从模块中import并且将其中一个元素改名
- [x] 将模块中可以import的元素全部import（原模块中export的元素）
- [x] 从模块中import默认元素，一般一个模块只export一个默认元素，且最好不要与普通的import混写（大致的意思就是不推荐用）

```javascript
import './sleepEarlier.js';
// 从模块中import ana、anb、anc（变量或者函数）
import { ana, anb, anc } from './sleepEarlier.js';
// 从模块中import并且将其中一个元素改名
import { ana, anb as ab, anc } from './sleepEarlier.js';
// import a form './sleepEarlier.js';
// 将模块中可以import的元素全部import（原模块中export的元素）
import * as sE from './sleepEarlier.js';
```

#### export的各种情况
- [x] export单个
- [x] export多个，并且改名
- [x] default关键词，export默认值

```javascript
// export单个
export const ana = [3, 4, 5, 6];
const anb = [3, 4, 5, 6];
const anc = [3, 4, 5, 6];
const abc = [];
// export多个，并改名字
export { anb, anc as ac };
// default关键词，export默认
export default function (product, quantity) {
  abc.push({ product, quantity });
}
```

### 一级await（ES2022中，在<font style="color:#DF2A3F;">模块</font>中可以在异步函数之外用await关键词）
#### 缺点：如果js导入有顶层await的模块，那么js将要等待模块完成，会造成阻塞
### 模块模式---在一定程度上解决了每个模块必须是单独的文件，且要link到js的问题（管理困难）。IIFE立即执行函数实现（闭包）
#### 将立即执行函数中的某些元素返回给外部的一个新的变量！！
```javascript
const newAdd = (function () {
  const a = 10;
  const b = 100;
  const add = function (a, b) {
    const c = a + b;
    console.log(c);
    return c;
  };

  return { a, b, add };
})();
console.log(newAdd);
console.log(newAdd.a);
console.log(newAdd.add(1, 1));

```

### CommonJS模块
[https://zhuanlan.zhihu.com/p/549278120](https://zhuanlan.zhihu.com/p/549278120)

```javascript
// Export
export.addTocart = function (product, quantity) {
  cart.push({ product, quantity });
  console.log(
    `${quantity} ${product} added to cart (sipping cost is ${shippingCost})`
  );
};
// Import
const { addTocart } = require('./shoppingCart.js');
```

### NPM(node package manager)
### 项目中重要的package.json
[https://zhuanlan.zhihu.com/p/510845130](https://zhuanlan.zhihu.com/p/510845130)

[https://zhuanlan.zhihu.com/p/510845130](https://zhuanlan.zhihu.com/p/510845130)

### 模块绑定器（webpack或者parcel）
[前端模块化知多少 - 掘金](https://juejin.cn/post/6921258049369964558)

[为什么我们需要模块打包工具_火鸡面多放火鸡的博客-CSDN博客_前端为什么要使用打包工具](https://blog.csdn.net/weixin_45047039/article/details/110088450)

#### parcel
[【翻译】打包工具？Parcel！最新官方英文文档学习 - 掘金](https://juejin.cn/post/6882573759027347469#heading-0)

用paecel打包后的js文件是动态的，即如果我们改变js代码，该文件会一起改变

解决办法：在js文件后加入

```javascript
if (module.hot)
{module.hot.accept()}
```

#### 导入模块
```javascript
import cloneDeep from 'lodash-es'
```

### babel
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677045255164-e0e56adb-3b47-4007-8f5b-b8455b5d1ad3.png)

[webpack，babel，babel-loader的关系_Wyyyy1024的博客-CSDN博客_babel和babel-loader](https://blog.csdn.net/weixin_44389562/article/details/110449909)

## 总结
### 代码编写原则
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677045988612-182f26c7-71e4-4204-a3ab-711d37c92d79.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677046203965-844caebd-9cb3-493c-a851-b48c8caac746.png)

###  编写代码的两种范式
#### 命令式VS声明式
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677320240025-2924cd1a-2acb-4560-9564-a6523bfb7c88.png)

###  函数式编程
其本质是基于声明式

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677320928858-8326f99a-1855-477e-8fdd-8d0982f969e9.png)

### Object.freeze
#### <font style="color:rgb(64, 64, 64);">Object.freeze() 方法可以冻结一个对象。一个被冻结的对象再也不能被修改；</font>
+ 冻结了一个对象则不能向这个对象<font style="color:#DF2A3F;">添加新</font>的属性
+ <font style="color:#DF2A3F;">不能删除</font>已有属性
+ 不能修改该对象已有属性的可枚举性、可配置性、可写性，
+ 以及**<font style="color:#DF2A3F;">不能修改已有属性的值</font>**。此外，冻结一个对象后**<font style="color:#DF2A3F;">该对象的原型也不能被修改</font>**
+ **<font style="color:#DF2A3F;">但可以修改属性的值的属性值（值）的值！！！（如果属性的值仍然是一个对象的话---数组or列表）</font>**
+ freeze() 返回和传入的参数相同的对象

## 项目--forkify
### 项目流程
![画板](https://cdn.nlark.com/yuque/0/2023/jpeg/2587809/1677332025506-d0f540e4-5ab3-4ba9-9f0e-f9e875d27284.jpeg)

#### 用户需求
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677332803120-b57b8de8-018f-4500-adea-b47bd130c83b.png)

#### 功能
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677332837005-ac5f7796-b231-4d1c-b097-6428676d2462.png)

#### 流程图
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677332887324-a48c104f-d25f-4622-b719-3e82003cd3c2.png)





# [从url到页面](https://zhuanlan.zhihu.com/p/133906695) 
## [原型和原型链详解](https://www.jianshu.com/p/ddaa5179cda6)
[JavaScript：函数function与方法method的区别？_大只兔的博客-CSDN博客](https://blog.csdn.net/qq_44179024/article/details/119934785)

[前端基础进阶（十）：深入详解函数的柯里化](https://www.jianshu.com/p/5e1899fe7d6b)

