## 1、基础认知
### 1.1网页的认识
+ 网页的组成：文字、图片、音频、视频、超链接
+ 前端的代码通过浏览器的转化（**渲染和解析**）成用户看到的网页

**<font style="color:#531DAB;">渲染引擎（浏览器内核）不同，会导致解析相同代码时的速度、性能、效果不同</font>**

| 浏览器 | IE | 火狐 | 谷歌 | 苹果 | opera |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 内核 | Trident | Gecko | webkit | Blik | Blik |


#### web标准：保证不同浏览器打开效果一样
### 1.2五大浏览器
浏览器：网页显示、运行的平台，前端必备

**IE、火狐、谷歌、苹果（safari）、opera**

### 1.3web标准的构成
| 结构（内容） | HTLM | 页面元素和内容 |
| :---: | :---: | :---: |
| 表现（外观） | CSS | 网页元素的外观位置等页面样式 |
| 行为 | Javascript | 网页模型的定义与页面交互 |


web标准要求页面实现：结构、表现、行为三层分离

## 2、HTML认知与基础
#### 超文本标记语言HTML(hypertext markup language) 
提供了一种用标记“标示”文本的方法，来告诉浏览器文本的结构是怎样的。&超文本  /HTML--结构/CSS--样式

专门用于网页开发的语言，主要通过**<font style="color:#C41D7F;">HTML标签</font>**对网页中的文本、音频、图片、视频等内容进行描述

### 2.1 HTML页面的固定结构
网页中的固定结构主要是通过固定的<font style="color:#389E0D;">HTML标签</font>进行描述的

#### 骨架结构标签
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1650587000604-5b96d23a-64be-4009-8b3f-ace457f96c01.png)

+ 一般由开发工具自动给出（vscode------创建html文件后，快捷键：**<font style="color:#C41D7F;">！+回车</font>** 出现骨架）
+ 写完后：**右键-open in default browser=****<font style="color:#C41D7F;">ALT+B</font>**（在默认浏览器中打开）

开发工具：**VSCODE**、webstorm、sublime、Dreamwaber、Hbuilder

### 2.2语法规范
#### 2.2.1HTML的注释（给自己或者给其他程序员）
vscode：**<font style="color:#C41D7F;">ctrl+/</font>**（注释的快捷键）----加注释或者取消注释同

#### 2.2.2 HTML标签的结构
1. 常见标签由两部分主城，中间包裹内容，称为<font style="color:#C41D7F;">双标签</font>
2. 少数标签由一部分组成，称为<font style="color:#EB2F96;">单标签</font>

HTML标签与标签之间的关系可分为：父子（嵌套关系）、兄弟（并列关系）

## 3、HTML标签学习
### 3.1排版标签学习
#### 3.1.1 标题标签：code：h系列标签
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1650588469675-60c1f695-1494-45f5-b0ce-cddd9ed5e6c8.png)                                    ![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1650588469691-914677b7-ce02-40f5-bb5e-a0025a8ab46d.png)

+ 1-6级标题，重要程度依次递减，字体依次减小
+ 文字都有加粗，独占一行

快速选中多个相同的字母或数字或单词：**<font style="color:#EB2F96;">选中+ctrl+d</font>****，ctrl+d,ctrl+d（ctrl几次，就会自动选中几个）**

#### 3.1.2,段落标签：<p> 内容</p>
##### 要设置多个段落时，可以直接p*m(m是一共有几个段落）---直接设置m个段落
![](https://cdn.nlark.com/yuque/0/2022/png/2587809/1650589553660-986effa2-9a49-4411-b035-5bf5d4cdc097.png)

+ 段落之间有间隔，每段独占一行
+ 如果标题下只有一个段落，可不用p标签，**标题标签自带段落属性 **

当但行文本过长，在vscode中不好编辑与查看时：**<font style="color:#EB2F96;">alt+z</font>**（查看自动换行）

#### 3.1.3 换行标签和水平线标签----单标签
1. 换行标签 **<font style="color:#389E0D;"><br></font>**：让文字强制换行表现（换行间隔与俩文本段落之间的间隔不一样）
2. 水平线标签**<font style="color:#389E0D;"><hr></font>**：在页面中显示一条水平线

#### 3.1.4 文本格式化标签(双标签-加粗、下划线、倾斜、删除线）
![画板](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1650590935201-88cafd68-2e7b-407a-953e-3f66cbbef493.jpeg)

**<font style="color:#1D39C4;">标签都是有语义的</font>**

### 3.2媒体标签
#### 3.2.1 图片标签 
![画板](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1650592638347-07640237-70cd-45fc-b137-bd355a329d45.jpeg)

- [x] **src属性：目标图片路径**
- [x] **alt属性：替换文本**；当图片加载**失败时出现**，图片加载成功时不会出现该文本
- [x] **title属性：提示文本**（当鼠标**<font style="color:#C41D7F;">悬停</font>**时，才显示的文本）--**不仅用于图片标签，还可用于其它标签**
- [x] **width和height属性：设置图片的高度和宽度（也可用于视频）**
    - 如果只设置其中一个，另一个会自动等比例缩放，此时图片不会变形
    - 如果同时设置两个，设置不当，图片可能会变形

##### 属性注意点
1. 标签的属性写在开始标签内部
2. 标签内可以同时存在多个属性
3. 属性之间以空格隔开（标签和属性同）
4. 属性没有顺序之分

#### 绝对路径和相对路径
##### 绝对路径：通常从盘符或者根目录开始
如：D:\day02\images\小兰.jpg

##### 相对路径（工作中常用）：从当前文件开始出发去找目标文件
相对路径分类：

+ 同级目录： <font style="color:#C41D7F;">.</font>**<font style="color:#C41D7F;">/也可以直接写文件名+后缀</font>**
+ 下级目录： **<font style="color:#C41D7F;">文件夹名/目标名字</font>**
+ 上级目录：**<font style="color:#C41D7F;"> ../(一级</font>**）  **<font style="color:#C41D7F;"> ../../（二级）</font>**
+ **例：**../images/map.jpg     ----- 返回上一级，并进入images文件夹，找到目标map.jpg

#### 3.2.2 音频标签 <audio src=''"  controls>  </audio>
- [x] **src属性 ：音频文件的路径**
- [x] **controls属性：显示播放的空间**
- [x] **autoplay 属性：自动播放（部分浏览器不支持）**
- [x] **loop属性：循环播放**

音频标签目前支持三种格式：**MP3**、WAV、Ogg

#### 3.2.2 视频标签<video src="" controls>  </video> 
- [x] **视频属性同音频属性**
- [x] **autoplay属**性：谷歌浏览器中需配合**<font style="color:#389E0D;">muted</font>**属性实现<font style="color:#389E0D;">静音自动播放</font>

视频标签目前支持三种个数：**MP4**、webm、Ogg

#### 3.2.3 超链接标签（a标签、锚标签）<a href="" >超链接</a>
场景：点击后，从一个页面跳转到另一个页面

- [x] **href属性：目标网页路径/网址，当开发网站初期，我们还不知道跳转的地址时，href的值书写****<font style="color:#C41D7F;">#--表示空连接</font>**
- [x] **target属性：目标网页的打开形式**
    - _self：默认值，在当前窗口中跳转（覆盖原网页）
    - _bank：在窗口中跳转（保留原网页）

#### <font style="color:#597EF7;">index.html是所有前端项目首页的名称</font>
### 3.3 列表标签
#### 能够使用<font style="color:#52C41A;">无序列表</font>、<font style="color:#52C41A;">有序列表</font>、<font style="color:#52C41A;">自定义列</font>表标签，实现网页中<font style="color:#52C41A;">列表结构</font>的搭建
应用场景：在网页中按照**<font style="color:#C41D7F;">行</font>**展示<font style="color:#C41D7F;">关联性</font>的内容，如新闻列表、排行榜（有序）、账单等

特点：按照**<font style="color:#C41D7F;">行</font>**的形式，整齐显示内容

![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1650607004921-edafe553-56ca-49f0-97ed-f730dada3080.jpeg)

#### 3.3.1 无序列表
在网页中表示一组<font style="color:#C41D7F;">无顺序之分</font>的列表，如新闻列表

| 标签名 | 说明 |
| :---: | :---: |
| ul | 表示无序列表的整体，用于包裹li |
| li | 表示无序列表的每一项，用于包含每一行的内容 |


+ 列表的每一项前默认**<font style="color:#C41D7F;">圆点</font>**标识
+ ul标签中只允许包含li标签
+ li标签中可以包含任意内容
- [x] **<font style="color:#E8323C;">去掉列表的符号：css里，选择列表标签：ul {list-style：none;}</font>**

#### 3.3.2 有序列表
在网页中表示一组**有顺序之分**的列表，如，排行榜

| 标签名 | 说明 |
| :---: | :---: |
| ol | 表示有序列表的整体，用于包裹li |
| li | 表示有序列表的每一项，用于包含每一行的内容 |


+ 列表的每一项前默认显示**<font style="color:#F759AB;">序号标识</font>**
+ 注意点同无序列表

#### 3.3.3 自定义列表
在**<font style="color:#F759AB;">网页的底部导航中</font>**通常会使用自定义列表实现

| 标签名 | 说明 |
| :---: | :---: |
| dl | 表示自定义的整体，用于包含dt/dd标签 |
| dt | 表示自定义列表的主题 |
| dd | 表示针对主题的每一项内容 |


+ dd前会默认显示缩进效果
+ dl只允许包含dd/dt标签
+ dd/dt可以包含任何内容

### 3.3 表格标签
能够使用表格相关标签和属性，实现网页中表格结构的搭建

#### 3.3.1 表格的基本标签
在网页中以行+列的单元格的方式整齐展示和数据：如学生成绩表

| 标签名 | 说明 |
| :---: | --- |
| table | 表格整体，用于包含多个tr |
| tr | 表格每行，可用于包裹td |
| td | 表格单元格，可用于包裹内容 |


#### 3.3.2 表格相关属性
设置表格基本展示效果

- [x] **border属性：数字---边框宽度**
- [x] **width属性：数字--表格宽度**
- [x] **height属性：数字--表格高度**
+ 注意点：**实际开发时针对于样式效果推荐用CSS设置**

#### 3.3.3 表格标题和表头单元格标签
场景：在表格中表示整体大标题和一系列小标题

| 标签名 | 名称 | 说明 |
| :---: | :---: | :---: |
| caption | 表格大标题 | 表格整体大标题，默认在表格整体顶部居中位置显示 |
| th | 表头单元格 | 一系列小标题，通常用于表格第一行，默认内部而文字加粗并居中显示 |


+ caption标签写在table内部
+ th标签写在tr内部用于替换td标签

#### 3.3.4 表格的结构标签 ：让代码的结构更加清晰，浏览器的执行效率会更高
场景：让表格的内容结构分组，突出表格的不同部分（头部、主体、底部），使语义更加清晰

| 标签名 | 名称 |
| :---: | :---: |
| thead | 表格头部 |
| tbody | 表格主体 |
| tfoot | 表格底部 |


+ 表格结构标签内容部用于包含tr标签
+ 表格的结构标签可以省略
- [x] Tab缩进往后走
- [x] **shift+Tab**缩进往前走

#### 3.3.4 合并单元格
场景：将水平或垂直多个单元格合并成一个单元格

+ 跨行合并（垂直合并成一个）
+ 跨列合并（水平合并成一个）

合并单元格步骤：

1. 明确合并哪几个单元格
2. 通过**<font style="color:#9254DE;">左上</font>**原则，确定保留谁删除谁
    - <font style="color:#9254DE;">上下合并---只保留最上的，删除其他</font>
    - <font style="color:#9254DE;">左右合并---只保留最左的，删除其他</font>
3. **<font style="color:#9254DE;">给保留的单元格设置属性</font>**：跨行合并（rowspan） 或者跨列合并（colspan）
- [x] **rowspan属性**----值：合并单元格的**个数**---将多行单元格垂直合并
- [x] **colspan属性**-----值：合并单元格的**个数**----将多列的单元格水平合并
+ 注意：**<font style="color:#389E0D;">只有同一个结构标签中的单元格才能合并，不能跨结构标签合并</font>**（不能跨：thead、tbody、tfoot）

### 3.4 表单标签
目标：能够使用表单相关标签和属性，实现网页中表单类网页结构搭建

#### 3.4.1 <font style="color:#389E0D;">input</font> 系列标签
场景：在网页中显示收集用户信息的表单效果，如：登录页、注册页

标签名：<font style="color:#389E0D;">input  （单标签）写法：<input /></font>

+ input标签可以通过**<font style="color:#F5222D;">type属性值</font>****的不同，展示不同效果**
- [x] **<font style="color:#597EF7;">number属性值</font>**
- [x] **<font style="color:#597EF7;">text属性值</font>****：文本框，用于输出单行文本**
    - [x] **placeholder属性：占位符。提示用户输入内容的文本（****<font style="color:#C41D7F;">可用于文本框、密码框等</font>****）**
- [x] **<font style="color:#597EF7;">password属性值</font>****：密码框，用于输出密码**
- [x] **<font style="color:#597EF7;">radio属性值</font>****：单选框，用于多选一**
    - [x] **name属性：分组**。**有相同name属性值的单选框为一组，一组同时只能有一个被选中**
    - [x] **checked属性：默认选中（还可用于多选框）**
        * name属性对于单选框有分组功能
- [x] **<font style="color:#597EF7;">checkbox属性值</font>****：多选框，用于多选多**
- [x] **<font style="color:#597EF7;">file属性值</font>****：文件选择：用于之后上传文件**
    - [x] **multiple：多文件选择**
+ 在网页中显示不同功能的按钮表单控件
- [x] **<font style="color:#597EF7;">submit属性值</font>**** ：提交按钮，点击之后提交数据给后端服务器**
- [x] **<font style="color:#597EF7;">reset属性值</font>****：重置按钮，点击之后恢复表单默认值**
- [x] **<font style="color:#597EF7;">button属性值</font>****：普通按钮，默认无功能，之后配合js封装具体的功能**
    - [x] **value属性**：给普通按钮设置显示值（详情敲代码）--可用于多种按钮属性

##### 注意点
+ **如果需要实现以上按钮功能，需配合****<font style="color:#C41D7F;">form标签</font>****使用**
+ **form使用方法：用****<font style="color:#C41D7F;">form标签把想要实现功能的表单标签一起包裹起来</font>****即可**

#### 3.4.2<font style="color:#389E0D;"> button</font>按钮标签
场景：在网页中显示用户点击的按钮

- [x] **<font style="color:#597EF7;">type属性值同input的按钮系列：submit、reset、button</font>**

##### 注意点
+ **谷歌浏览器中button默认是****<font style="color:#C41D7F;">提交</font>****按钮**
+ **button标签是****<font style="color:#C41D7F;">双标签</font>****，更便于包裹其他内容：****<font style="color:#C41D7F;">文字、图片等</font>****（比input的功能更强大）**

#### 3.4.3 <font style="color:#389E0D;">select </font>下拉菜单标签
场景：在网页中提供多个选择项的下拉菜单表单控件

| 标签名 | 说明 |
| :---: | :---: |
| select | 下拉菜单的整体 |
| option | 下拉菜单的每一项 |


- [x] selected：下拉菜单的默认选中

#### 3.4.4 <font style="color:#389E0D;">textarea</font>文本域标签
场景：在网页中提供可输入多行文本的表单控件

- [x] **clos：规定了文本域内可见宽度**
- [x] **row：规定了文本域内可见行数**

##### 注意点：
+ 右下角可以拖拽改变大小
+ 实际开发时正针对样式效果<font style="color:#CF1322;">推荐使用CSS设置</font>

#### 3.4.5 <font style="color:#389E0D;">label</font>标签
场景：常用于绑定内容与表单标签的关系

##### 使用方法①--（复杂）
1. 使用label标签把内容（如：文本）和表单标签一起包裹起来
2. 在表单标签上添加id属性
3. 在label标签的for属性中设置对应的id属性值

##### <font style="color:#389E0D;">使用方法②--（简单）</font>
1. 直接使用<font style="color:#389E0D;">label标签把内容（如：文本）和表单标签一起包裹起来</font>
2. 需要把label标签的<font style="color:#389E0D;">for属性删除</font>即可

## 4、语义化标签
目标：能够认识开发中常用的**<font style="color:#CF1322;">没有语义的布局标签（div、span）</font>**和有语义的布局标签

### 4.1 没有语义的布局标签-div和span（用于网页布局）
场景：实际开发网页时会大量频繁的使用到**<font style="color:#CF1322;">div和span</font>**这两个没语义的布局标签

| 标签名 | 说明 |
| :---: | :---: |
| div | **一行只显示一个（独占一行）** |
| span | **一行可以显示多个（**多个span显示在一行**）** |


### 4.2 有语义的布局标签（了解）---<font style="color:#08979C;">手机端</font>的网页会用


场景：在**HTML5新版本**中，退出了一些有语义的布局标签共开发者使用

| 标签名 | 名称 |
| :---: | :---: |
| header | 网页头部 |
| nav | 网页导航 |
| footer | 网页底部 |
| aside | 网页侧边栏 |
| section | 网页区块 |
| artricle | 网页文章 |


![](https://cdn.nlark.com/yuque/0/2022/jpeg/2587809/1650782044375-60b752ce-d2f9-448c-9afe-73903b2d7556.jpeg)

## 5、实体字符
目标：能够通过**<font style="color:#531DAB;">字符实体</font>**在网页中显示特殊符号

### 5.1 常见字符实体
场景：在网页中展示**<font style="color:#389E0D;">特殊符号效果</font>**时，需要使用**<font style="color:#389E0D;">字符实体</font>**代替

结构：&英文；

**网页不认识多个空格，只认识一个空格**

只记空格字符实体：**<font style="color:#389E0D;">&nbsp:</font>**







