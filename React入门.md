# React18+Next.js13+ant5+ts4全栈开发复杂低代码项目（仿问卷星）
[https://juejin.cn/post/7220274775913381925](https://juejin.cn/post/7220274775913381925)

## react介绍
[快速入门 – React 中文文档](https://zh-hans.react.dev/learn)

+ 核心价值：组件化+数据驱动视图

#### 组件化（造轮子、拼整体）
+ 拆分页面结构，通过组件拼装页面，复用组件
+ 易开发维护，尤其对于多人协作开发的大型项目

#### 数据驱动视图：UI=f(state)
+ 定义好数据和UI的显示规则，即UI=f(state)
+ 只关注业务数据的修改，不再操作DOM，增加开发效率
+ 尤其对于DOM结构复杂的大型项目

## 创建react项目开发环境
+ 了解react常见的脚手架工具（创建工具）
+ 创建react项目，配置编码规则
+ 提交到git仓库

### 使用Create-React-App创建项目
+ 官网：[https://create-react-app.bootcss.com/](https://create-react-app.bootcss.com/)

```javascript
npx create-react-app demo1 --template typescript
```

+ tsx文件是什么：[https://juejin.cn/post/7220274775913381925](https://juejin.cn/post/7220274775913381925)

### 使用Vite创建项目
+ 官网：[https://cn.vite.dev/](https://cn.vite.dev/)

#### 本项目选择使用create-react-app
原因：

1. create-reacta-app是react官网推荐
2. create-reacta-app使用时间更久，可查找的资源更多
3. 选择工具首先要考虑稳定性，求稳不求新

### <font style="color:#DF2A3F;">使用eslint检查语法问题</font>
[https://juejin.cn/post/7385747507954663462](https://juejin.cn/post/7385747507954663462)

[eslint中文网](https://link.juejin.cn/?target=https%3A%2F%2Feslint.nodejs.cn%2F)

+ 安装eslint（npm安装&vscode安装）
+ 
+ 安装所需依赖
    1. **<font style="color:#117CEE;background-color:rgb(248, 248, 248);">适配typesctipt</font>**<font style="color:#117CEE;background-color:rgb(248, 248, 248);">：</font>**<font style="color:#117CEE;background-color:rgb(248, 248, 248);">@typescript-eslint/parser</font>**<font style="color:#117CEE;background-color:rgb(248, 248, 248);">：将ts解析成等价的js语法树，然后传递给ESLint进行处理---</font><font style="background-color:rgb(248, 248, 248);">typescript官方AST（抽象语法树）解析库，保证解析的准确性和兼容性</font>
    2. **<font style="color:#117CEE;background-color:rgb(248, 248, 248);">在vite中使用：</font>**`**<font style="color:#117CEE;background-color:rgb(248, 248, 248);">vite-plugin-eslint</font>**`<font style="color:#117CEE;background-color:rgb(248, 248, 248);">：</font><font style="color:rgb(43, 43, 43);">在</font>**<font style="color:rgb(43, 43, 43);">启动项目和打包代码</font>**<font style="color:rgb(43, 43, 43);">时进行</font>**<font style="color:rgb(43, 43, 43);">代码检查</font>**<font style="color:rgb(43, 43, 43);">, 默认配置是如果检查有</font>`<font style="color:rgb(38, 198, 218);">error</font>`<font style="color:rgb(43, 43, 43);">类型的问题就启动或打包失败, </font>`<font style="color:rgb(38, 198, 218);">warn</font>`<font style="color:rgb(43, 43, 43);">类型的问题不影响启动和打包 </font>

```typescript
npm install vite-plugin-eslint@latest -D
```

        * <font style="color:rgb(43, 43, 43);">安装好该依赖后，在</font>**<font style="color:#117CEE;">vite.config.ts文件中将eslint引入</font>**<font style="color:rgb(43, 43, 43);">！！！</font>

```typescript
import eslint from 'vite-plugin-eslint'

export default defineConfig({
  plugins:[vue(),eslint()]
})
```

        * <font style="color:#DF2A3F;">导入eslint时报错解决方式</font>：[https://blog.csdn.net/m0_53022813/article/details/137379480](https://blog.csdn.net/m0_53022813/article/details/137379480)



+ 初始化：<font style="background-color:#FBDE28;"> </font>**<font style="background-color:#FBDE28;">npx eslint --init  </font>****或者 ****<font style="background-color:#FBDE28;">yarn create @eslint/config@latest</font>**
+ **<font style="background-color:#FBDE28;"></font>**
+ 配置：

#### yarn 编译react项目报错
安装依赖

```tsx
yarn add -D eslint-config-react-app eslint
```

[yarn 编译react-app项目时报错[eslint] Failed to load config... - ayatip - 博客园](https://www.cnblogs.com/miwa441/p/17190326.html)

### <font style="color:#DF2A3F;">使用prettier</font>
+ 安装prettier（npm安装&vscode安装）

```tsx
yarn add prettier -D
```

+ 安装相关依赖
    - **<font style="color:#2F4BDA;">eslint-config-prettier(eslint版本<9.0）</font>**：禁用eslint与prettier冲突的eslint规则，确保两者的代码格式化规则保持一致，避免二者之间的冲突
    - **<font style="color:#2F4BDA;">eslint-plugin-prettier</font>**：将prettier应用到eslint中。他会使用prettier来格式化diamagnetic，并将格式化结果作为eslint的一项规则来检查代码。<font style="color:#1DC0C9;">即在检查代码的同时，自动格式化代码，使其符合prettier的规则</font>。
+ eslint 9.0以上的版本自动兼容prettier，不用手动安装eslint-config-prettier依赖
+ 手动新建**<font style="background-color:#FBDE28;">prettierrc.js</font>**，并将代码格式写入其中
+ **<font style="background-color:#FBDE28;">一定别忘了把以下两行prettier写入eslint.config.js中，才能把在prettierrc.js中自定义的格式规范导入进来</font>**
+ 或者：[https://blog.csdn.net/u013344993/article/details/139967343](https://blog.csdn.net/u013344993/article/details/139967343)

```javascript
import globals from 'globals'
import pluginJs from '@eslint/js'
import tseslint from 'typescript-eslint'
import pluginReact from 'eslint-plugin-react'
import eslintPluginPrettierRecommended from 'eslint-plugin-prettier/recommended'
import eslintConfigPrettier from 'eslint-config-prettier'

export default [
  { files: ['**/*.{js,mjs,cjs,ts,jsx,tsx}'] },
  { languageOptions: { globals: globals.browser } },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  pluginReact.configs.flat.recommended,
  eslintPluginPrettierRecommended,
  eslintConfigPrettier
]
```

+ 配置完之后遇见不生效的情况，关闭vscode窗口，重启一下！！！

### vscode配置保存自动修改格式
```javascript
{
      "editor.codeActionsOnSave": {
        "source.fixAll.eslint": "always"
    },
}
```

### 在page.json中配置相关的script命令
+ eslint命令

```javascript
"lint": "eslint 'src/**/*+(js|ts|tsx|jsx)'",
```

+ prettier命令

```javascript
"format": "prettier --write 'src/**/*+(js|ts|tsx|jsx)'"
```

### git提交


### husky--流程规范工具
[https://github.com/typicode/husky](https://github.com/typicode/husky)

+ 一个git hook工具
+ 在git commit 之前执行自定义的命令
+ 如执行代码风格的检查，避免提交非规范代码

#### 使用
1. 安装

```javascript
npm install --save-dev husky
```

```javascript
yarn add --dev husky
# Add pinst ONLY if your package is not private
yarn add --dev pinst
```

2. 初始化

```javascript
npx husky init
```

3. 配置命令

在项目的pre-commit文件中配置想要执行的命令

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1730555259801-59dac328-97da-44ab-99b2-5ef79ce2f702.png)

### commit lint -- 限制commit描述的规范
![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1730555660793-58c04f24-57d0-4975-b20c-c59766bc52c8.png)

#### 使用
[https://commitlint.js.org/guides/getting-started.html](https://commitlint.js.org/guides/getting-started.html)

+ 安装
+ 配置
+ Add hook：结合husky一起使用 [https://commitlint.js.org/guides/local-setup](https://commitlint.js.org/guides/local-setup)

```tsx
echo "yarn commitlint --edit \$1" > .husky/commit-msg
```

#### commit描述规范
- [x] **<font style="color:#117CEE;"><类型>: (类型的值见下面描述) <主题> (最多50个字)</font>**
    - 解释为什么要做这些改动
    - 提供相关文章和其它资源的链接和关键字。例如: Github issue #23
- [x] 类型值包含
1. **feat** (新特性)
2. **fix** (bug修复)
3. **docs** (文档改动)
4. **style** (格式化, 缺失分号等; 不包括生产代码变动)
5. **refactor** (重构代码)
6. **test** (添加缺失的测试, 重构测试, 不包括生产代码变动)
7. **chore** (更新grunt任务等; 不包括生产代码变动)

```markdown
'build',
'chore',
'ci',
'docs',
'feat',
'fix',
'perf',
'refactor',
'revert',
'style',
'test'
```

- [x] 注意
+ 主题和内容以一个空行分隔
+ 主题限制为最大50个字
+ 主题行大写
+ 主题行结束不用标点
+ 主题行使用祈使名
+ 内容每行72个字
+ 内容用于解释为什么和是什么,而不是怎么做
+ 内容多行时以'-'分隔

### 问题&解决
- [x] JS中的export、export default、module.exports、exports

**<font style="color:rgb(79, 79, 79);background-color:rgb(255, 217, 0);">默认的js文件是不支持es6种的export和export default语法的</font>**

**<font style="color:rgb(79, 79, 79);background-color:rgb(255, 217, 0);">需要在 package.json 文件中，配置添加 "type": "module"属性使用，</font>**

[JavaScript第 30 篇，JavaScript中的export、export default、exports 和 module.exports使用详细-CSDN博客](https://blog.csdn.net/weixin_65793170/article/details/136476532)

### vite和webpack的区别
- [x] webapck是一个非常传统的打包工具
    - 递归解析项目中所有的依赖模块，并将其合并打包为一个或多个包
    - [https://developer.aliyun.com/article/1271978](https://developer.aliyun.com/article/1271978)
- [x] create-react-app内部就是用webpack进行打包的
- [x] vite即是构建工具，又是打包工具（通过es module实现）
    - [https://blog.csdn.net/zhongqw_00/article/details/136733111](https://blog.csdn.net/zhongqw_00/article/details/136733111)
    - <font style="color:rgb(36, 41, 46);">vite利用了ES module这个特性，使用vite运行项目时，首先会用esbuild进行预构建，将所有模块转换为es module，</font><font style="color:#D22D8D;">不需要对我们整个项目进行编译打包</font><font style="color:rgb(36, 41, 46);">，而是在浏览器import某个模块时，发送一个HTTP请求去加载文件，vite启动一个 koa 服务器拦截这些请求，拦截浏览器发出的请求，</font><font style="color:#D22D8D;">根据请求进行按需编译，然后返回给浏览器</font>

## JSX语法和组件基础
### JSX语法
#### 标签
1. 首字母大小写的区别，**<font style="color:#DF2A3F;">大写为自定义组件（自定义组件小写会报错！！！</font>**）
2. 标签必须闭合，否则是非法的
3. **<font style="color:#D22D8D;">每段JSX必须只有一个根节点</font>**，可以用div包也可以用**<font style="color:#D22D8D;background-color:#FBDE28;"><></></font>**包，表示一个片段(fregment)

#### 属性
1. 标签的class要改为**<font style="color:#D22D8D;">className</font>**（class与js中的类关键字冲突）
2. 写在标签上的style的值要是**<font style="color:#D22D8D;">对象</font>**（不能是字符串的形式），且其中的key名要用**<font style="color:#D22D8D;">驼峰式</font>**写法

```markdown
<a
  className="App-link"
  href="https://reactjs.org"
  target="_blank"
  rel="noopener noreferrer"
  style={{ color: 'red', backgroundColor: 'blue' }}
>
```

3. lable标签的for属性要改为htmlFor

#### 事件
1. 使用**<font style="color:#D22D8D;">onXxx</font>**的形式
2. 必须传入一个**<font style="color:#D22D8D;">函数</font>**（fn而非fn()）
3. **注意typescript类型（如：从react中引入的MouseEvent类型）**

```typescript
import type { MouseEvent } from 'react'

function App() {
  function fn(event: MouseEvent<HTMLButtonElement>) {
    event.preventDefault()
    console.log('事件')
  }

  //-----------------------------------------

  <button onClick={fn}>点击按钮</button>
```

#### 插入JS变量---- <font style="color:#D22D8D;">{ }</font>
+ 使用**<font style="color:#D22D8D;"> { }</font>** 可以插入js**<font style="color:#D22D8D;">变量、对象、表达式、函数</font>**
+ 可插入普通文本、属性
+ 可用于注释 

#### 条件判断
1. 使用 **<font style="color:#D22D8D;">&&</font>**
2. 使用**<font style="color:#D22D8D;">三元表达式</font>**
3. 使用**<font style="color:#D22D8D;">函数</font>**

```tsx
const flag = true
function Hello() {
  if (flag) {
    return <p>hello</p>
  } else {
    return <p>你好</p>
  }
{/*-----------------------------------------*/}
<div>
  {flag && <p>hello</p>}
  {flag ? <p>hello</p> : <p>你好</p>}
  <Hello></Hello> {/*标签、自定义组件，首字母大写，变成小写会报错！！ */}
</div>
```

#### 循环
+ 使用数组**<font style="color:#D22D8D;">map</font>**
+ 每个item元素需要**<font style="color:#D22D8D;">key</font>**属性
+ key在同级别唯一**（不能用index**）

```tsx
<ul>
  {list.map(item => {
    return <li key={item.name}>{item.mood}</li>
  })}
</ul>
```

#### <font style="color:#D22D8D;">&nbsp; </font>   表示空格
```tsx
import './App.css'
{/* 样式写在另外一个文件中，引入之后可以直接用，写样式名 */}
return (
  <div>
    {queryList.map(item => {
      const { id, name, isPublished } = item
      return (
        <div key={id} className="list-item">
          <strong>{name}</strong>
          &nbsp;
          {isPublished ? <span style={{ color: 'pink' }}>已发布</span> : <span>未发布</span>}
          &nbsp;
          <button onClick={() => edit(id)}>编辑问卷</button>
        </div>
      )
    })}
  </div>
)
```

### 组件----React 一切皆组件！
+ 组件就是一个UI片段
+ 拥有独立的逻辑和显示
+ 组件可大可小，可嵌套

#### 意义
1. 组件嵌套来组织页面结构，和html一样，无学习成本
2. 组件拆分、利于代码维护和多人协作开发
3. 可封装公共组件（或者第三方组件），复用代码，提高开发效率

### react开发工具--chrom插件--react developer tools
![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1731131564407-1ec533a1-2612-4141-94cf-cc14c71706b0.png)

+ 组件层级结构
+ 各个组件props
+ 选中查看页面组件

### JSX和VUE的区别（部分）
+ react--能用js就用js语法（vue自定义了许多指令，如v-for、v-if）
+ vue--自定义很多指令，方便初学者学习和记忆
+ 不过，现在vue3也能很好的支持jsx语法

## ReactHooks--处理逻辑监听状态，让页面动起来
#### 目标
1. 内置hook
2. 自定义hook
3. 第三方hook
4. hook使用规则

hooks有很多规则，遇到错误时，要先看看是否违反规则

### useState --<font style="color:rgb(35, 39, 47);">在组件的顶层调用 </font>`useState`<font style="color:rgb(35, 39, 47);"> 来声明一个 </font>[状态变量](https://zh-hans.react.dev/learn/state-a-components-memory)<font style="color:rgb(35, 39, 47);"></font>
[https://zh-hans.react.dev/reference/react/useState](https://zh-hans.react.dev/reference/react/useState)

我的理解---相当于实现vue中的响应式数据

```tsx
import { useState } from 'react';

function MyComponent() {
  const [age, setAge] = useState(28);
  const [name, setName] = useState('Taylor');
  const [todos, setTodos] = useState(() => createTodos());
```

### state的特点
[https://zh-hans.react.dev/learn/managing-state](https://zh-hans.react.dev/learn/managing-state)

+ props--父组件传递过来的数据
    - react中父传值给子组件是通过传递函数参数一样传的

```tsx
<QuestionCard
  key={id}
  id={id}
  name={name}
  isPublished={isPublished}
  publishOperate={handlePublish}
  deleteOperate={handleDelete}
></QuestionCard>
```

```tsx
const QuestionCard: FC<propsType>
  = props => {
  const { id, 
          name, 
          isPublished, 
          publishOperate, 
          deleteOperate } 
          = props
```

+ state-组件内部的状态信息，可作为数据传递给子组件
+ state变化，触发组件更新，重新渲染页面

#### 异步更新----无法直接拿到最新的值
```tsx
function handleClick() {
  setAge(age + 1); // setAge(42 + 1)
  console.log(age)
}
```

```tsx
function handleClick() {
  setAge(age =>age + 1); // setAge(42 + 1)
  console.log(age)
}
```

+ `set`<font style="color:rgb(35, 39, 47);"> 函数 </font>**<font style="color:rgb(35, 39, 47);">仅更新 </font>**_**<font style="color:rgb(35, 39, 47);">下一次</font>**_**<font style="color:rgb(35, 39, 47);"> 渲染的状态变量</font>**<font style="color:rgb(35, 39, 47);">。如果在调用 </font>`set`<font style="color:rgb(35, 39, 47);"> 函数后读取状态变量，则 </font>[<font style="color:#117CEE;">仍会得到在调用之前显示在屏幕上的旧值</font>](https://zh-hans.react.dev/reference/react/useState#ive-updated-the-state-but-logging-gives-me-the-old-value)<font style="color:rgb(35, 39, 47);">。</font>
+ <font style="color:rgb(35, 39, 47);">如果一个变量不写在JSX中显示，就不用useState管理</font>

#### 多个set被合并
#### 合并
```tsx
function handleClick() {
  setAge(age + 1); // setAge(42 + 1)
  setAge(age + 1); // setAge(42 + 1)
  setAge(age + 1); // setAge(42 + 1)
}
// 结果只会为43
```

- [x] <font style="color:rgb(35, 39, 47);">原因：调用 </font>`set`<font style="color:rgb(35, 39, 47);"> 函数 </font>[不会更新](https://zh-hans.react.dev/learn/state-as-a-snapshot)<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);background-color:#FBDE28;">已经运行代码</font><font style="color:rgb(35, 39, 47);">中的 </font>`age`<font style="color:rgb(35, 39, 47);"> 状态变量</font>

##### 解决合并---传入更新函数（而不是更新值）
```tsx
function handleClick() {
  setAge(a => a + 1); // setAge(42 => 43)
  setAge(a => a + 1); // setAge(43 => 44)
  setAge(a => a + 1); // setAge(44 => 45)
}
```

<font style="color:rgb(35, 39, 47);">这里，</font>`a => a + 1`<font style="color:rgb(35, 39, 47);"> 是更新函数。它获取 </font>待定状态<font style="color:rgb(35, 39, 47);"> 并从中计算 </font>下一个状态<font style="color:rgb(35, 39, 47);">。</font>

- [x] <font style="color:rgb(35, 39, 47);">React </font>**<font style="color:#DF2A3F;">将更新函数放入 </font>**[**<font style="color:#DF2A3F;">队列</font>**](https://zh-hans.react.dev/learn/queueing-a-series-of-state-updates)**<font style="color:#DF2A3F;"> 中</font>**<font style="color:rgb(35, 39, 47);">。然后，在下一次渲染期间，它</font>**<font style="color:rgb(35, 39, 47);">将按照相同的顺序调用它们</font>**<font style="color:rgb(35, 39, 47);">：</font>
1. `a => a + 1`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">将接收</font><font style="color:rgb(35, 39, 47);"> </font>`42`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">作为待定状态，并返回</font><font style="color:rgb(35, 39, 47);"> </font>`43`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">作为下一个状态。</font>
2. `a => a + 1`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">将接收</font><font style="color:rgb(35, 39, 47);"> </font>`43`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">作为待定状态，并返回</font><font style="color:rgb(35, 39, 47);"> </font>`44`<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">作为下一个状态。</font>
3. `a => a + 1`<font style="color:rgb(35, 39, 47);"> 将接收 </font>`44`<font style="color:rgb(35, 39, 47);"> 作为待定状态，并返回 </font>`45`<font style="color:rgb(35, 39, 47);"> 作为下一个状态。</font>

#### <font style="color:#D22D8D;">不可变数据！！（重要）--不能直接修改state的值，而是要用set方法传入一个新的值</font>
##### 对象
```tsx
const [info, setInfo] = useState({ name: 'liao', age: 18 })
function changeAge() {
    info.age++ //错误，不生效
    setInfo({ ...info, age: 20 }) //正确，传入新的值，生效
  }
```

##### 数组
```tsx
const [colors, setColors] = useState(['red', 'yellow', 'pink', 'blue'])

function changeColor() {
    colors.push('white') //错误，不生效,dom不更新
    setColors(colors.concat('white')) //正确，传入新的同类型的值，生效
    setColors([...colors, 'white']) //正确，传入新的同类型的值，生效
  }
```

#### 使用set函数的同时处理数据----要用<font style="color:#DF2A3F;">能返回新数据</font>的函数！！！
```tsx
  function handlePublish(id: number) {
    setQueryList(
      queryList.map(item => {
        if (item.id !== id) {
          return item
        } else {
          return {
            ...item,
            isPublished: true,
          }
        }
      })
    )
  }
  function handleDelete(id: number) {
    setQueryList(
      queryList.filter(item => {
        if (item.id === id) {
          return false
        } else {
          return true
        }
      })
    )
  }
```

#### 其他：在vscode中安装code spell checker插件
### immer--用produce函数解决state是不可变数据的麻烦
解决set函数里一定要用有返回值的函数的问题（可以不用返回值）

[Immer 入门 | Immer](https://immerjs.github.io/immer/zh-CN/)

#### 安装
```tsx
npm install immer --save
yarn add immmr --save
```

#### 使用----通过produce，直接改变state的值
```tsx
import { produce } from 'immer'

setQueryList(
  produce(queryList => {
    queryList.push({
      id: queryList[queryList.length - 1].id + 1,
      name: `问卷${queryList[queryList.length - 1].id + 2}`,
      isPublished: false,
    })
  })
)
```

### useEffect（处理函数，[依赖项]） ⭐⭐⭐⭐⭐
[深入理解 React 的 useEffect：全面指南_react useeffect方法-CSDN博客](https://blog.csdn.net/u012446963/article/details/143835060)

#### 用于处理️️️️函数组件中，与渲染无关的逻辑，避免重复执行（如api请求、定时器）
因为在react中，任何state的更新都会触发组件的更新（重新执行函数）

#### 用法
##### 不传入依赖数组（每次组件渲染后都会执行）
```tsx
useEffect(() => {
  console.log('每次组件渲染后都会执行');
});
 
```

##### 传入空依赖数组----组件初次渲染执行
```tsx
useEffect(() => {
  console.log('仅在组件挂载时执行一次');
}, []);

// 通过return执行，在销毁时执行
useEffect(() => {
  return ()=>{console.log('组件销毁时执行该条')}
}, []);

```

###### 注意
- [x] 在**开发环境**下，从2018年开始会执行**两次**
- [x] 是在模拟组件创建、销毁、再创建的完整流程，及早暴露问题
- [x] 生产环境下会执行一次

##### 传入特定依赖--当特定依赖值变化时，函数执行
```tsx
useEffect(() => {
  console.log(`计数值更新为: ${count}`);
}, [count]);
 
```

##### 监听多个依赖
```tsx
useEffect(() => {
  console.log(`count 或 otherState 发生了变化`);
}, [count, otherState]);
 
```

#### 应用
##### 清理事件监听
```tsx
useEffect(() => {
  const handleResize = () => console.log('窗口大小变化');
  window.addEventListener('resize', handleResize);
 
  // 返回清理函数
  return () => {
    window.removeEventListener('resize', handleResize);
  };
}, []); // 空数组表示只在挂载和卸载时运行
 
```

##### 清理定时器
```tsx
useEffect(() => {
  const timer = setInterval(() => {
    console.log('计时器运行中');
  }, 1000);
 
  // 返回清理函数
  return () => {
    clearInterval(timer);
  };
}, []); // 确保在组件卸载时清理定时器
```

### useRef
#### 一般用于操作Dom：赋值给组件的ref（inputRef.操作 都是dom的操作函数）
```tsx
const SelectDemo: FC = () => {
  const inputRef = useRef<HTMLInputElement>(null)
  function handleInputSelect() {
    const inputElement = inputRef.current
    if (inputElement) {
      inputElement.select()
    }
  }
  return (
    <div>
      <input ref={inputRef} defaultValue="这里是input的内容" />
      <button onClick={handleInputSelect}>选中input</button>
    </div>
  )
}
```

#### 也可以传入普通的js变量( useRef('liao'))，但是<font style="color:#DF2A3F;">更新不会触发rerenfder</font>(作为变量)
- [x] 如果需要再页面上rerender就用useState改变变量，否则用useRef！！

```tsx
const SelectDemo: FC = () => {
  const nameRef = useRef('liao')
  function handleChangeP() {
    nameRef.current = 'liu'
    console.log(nameRef)
  }
  return (
    <div>
      <p>我的名字是{nameRef.current}</p>
      <button onClick={handleChangeP}>改变p的值</button>
    </div>
  )
}
```

### useMemo（函数，依赖数组）----缓存没有渲染期间没有变化的<font style="color:#DF2A3F;">数据</font>（一般用于性能优化）
- [x] 可以缓存数据，不用每次执行函数都重新生成
- [x] 可用于计算量较大的场景，缓存提高性能
- [x] 可用于父子组件传值，避免父组件每次更新，子组件都重新渲染

[React Hooks大全—useMemo_51CTO博客_react hooks memo](https://blog.51cto.com/u_15295488/9144754)

- [x] 只有当依赖数组中的值发生变化时，memorizedValue的值才会发生改变，并重新渲染
- [x] useMemo返回的值是其中函数变量的返回值

```tsx
const memorizedValue = useMemo(Fn, 依赖数组);
```

### useCallback(函数、依赖数组)----用于缓存<font style="color:#DF2A3F;">函数</font>！
- [x] `<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useCallback</font>`<font style="color:rgb(25, 27, 31);">是对</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useMemo</font>`<font style="color:rgb(25, 27, 31);">的特化，它可以返回一个</font><font style="color:#DF2A3F;">缓存版本的函数</font><font style="color:rgb(25, 27, 31);">，只有</font><font style="color:#117CEE;">当它的依赖项改变时，函数才会被重新创建</font><font style="color:rgb(25, 27, 31);">。这意味着</font><font style="color:#117CEE;">如果依赖没有改变，函数引用保持不变</font><font style="color:rgb(25, 27, 31);">，从而避免了因函数引用改变导致的不必要的重新渲染。</font>

```tsx
const memoizedFn = useCallback(
  () => {
    // 函数体
  },
  [dependency1, dependency2, ...] // 依赖数组
);
```

#### 场景
1. **<font style="color:rgb(25, 27, 31);">子组件的性能优化</font>**<font style="color:rgb(25, 27, 31);">：当你将</font><font style="color:#117CEE;">函数作为 prop</font><font style="color:rgb(25, 27, 31);"> 传递给已经通过</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">React.memo</font>`<font style="color:rgb(25, 27, 31);">进行优化的子组件时，使用</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useCallback</font>`<font style="color:rgb(25, 27, 31);">可以确保子组件不会因为</font>[<font style="color:rgb(25, 27, 31);">父组件</font>](https://zhida.zhihu.com/search?content_id=238947310&content_type=Article&match_order=6&q=%E7%88%B6%E7%BB%84%E4%BB%B6&zhida_source=entity)<font style="color:rgb(25, 27, 31);">中的函数重建而进行不必要的重新渲染。</font>
2. **<font style="color:rgb(25, 27, 31);">Hook 依赖</font>**<font style="color:rgb(25, 27, 31);">：如果你正在传递的函数会被用作其他 Hook（例如</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useEffect</font>`<font style="color:rgb(25, 27, 31);">）的依赖时，使用</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useCallback</font>`<font style="color:rgb(25, 27, 31);">可确保函数的稳定性，从而避免不必要的副作用的执行。</font>
3. **<font style="color:rgb(25, 27, 31);">复杂计算与频繁的重新渲染</font>**<font style="color:rgb(25, 27, 31);">：在应用涉及很多</font>[<font style="color:rgb(25, 27, 31);">细粒度</font>](https://zhida.zhihu.com/search?content_id=238947310&content_type=Article&match_order=1&q=%E7%BB%86%E7%B2%92%E5%BA%A6&zhida_source=entity)<font style="color:rgb(25, 27, 31);">的交互，如绘图应用或其它需要大量操作和反馈的场景，使用</font>`<font style="color:rgb(25, 27, 31);background-color:rgb(248, 248, 250);">useCallback</font>`<font style="color:rgb(25, 27, 31);">可以避免因频繁的渲染而导致的性能问题。</font>

### 自定义Hook----公共逻辑的抽离和复用
#### 自定义获取鼠标坐标hook
- [x] 组件销毁时一定要解绑dom事件，否则可能会出现内存泄漏问题！！！（包括定时器之类的）
- [x] 解绑一定要传入相同的函数变量

```tsx
import { useState, useEffect } from 'react'
function useMouse() {
  const [x, setX] = useState(0)
  const [y, setY] = useState(0)
  //   鼠标事件
  const mouseMoveHandle = (e: MouseEvent) => {
    setX(e.clientX)
    setY(e.clientY)
  }
  //   监听鼠标事件
  useEffect(() => {
    document.addEventListener('mousemove', mouseMoveHandle)
    // 组件销毁时一定要解绑dom事件，否则可能会出现内存泄漏问题！！！（包括定时器之类的）
    // 解绑一定要传入相同的函数变量
    return () => {
      document.removeEventListener('mousemove', mouseMoveHandle)
    }
  }, [])
  return { x, y }
}

export default useMouse
```

- [x] useMouse中用了state，只要state数据变化，就会引起组件的重新渲染，即使他们不在同一个页面

```tsx
function App() {
  // useMouse中用了state，只要state数据变化，就会引起组件的重新渲染，即使他们不在同一个页面（只要引用了就会）
  const { x, y } = useMouse()
  return (
    <p>
      鼠标坐标{x},{y}
    </p>
  )
}

export default App
```

#### 模拟异步加载数据
```tsx
import { useEffect, useState } from 'react'

// 异步获取日期
function getDate(): Promise<string> {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(new Date().toString())
    }, 1500)
  })
}
function useGetDate() {
  const [isLoading, setLoading] = useState(true)
  const [date, setDate] = useState('')
  useEffect(() => {
    // 获取异步函数结果
    getDate().then(res => {
      setLoading(false)
      setDate(res)
    })
  }, [])
  return { isLoading, date }
}

export default useGetDate

```

```tsx
import useGetDate from './hooks/useGetDate'
function App() {
  const { isLoading, date } = useGetDate()
  return (
    <p>{isLoading ? '加载中...' : date}</p>
  )
}

export default App

```

### 第三方hooks
#### aHooks（国内常用）
[ahooks - React Hooks Library - ahooks 3.0](https://ahooks.js.org/zh-CN/)

##### 安装
```tsx
$ npm install --save ahooks
# or
$ yarn add ahooks
# or
$ pnpm add ahooks
# or
$ bun add ahooks
```

##### 常用
+ useTitle
+ useRequest

#### react-use（国外常用）
[react-use-chinese/README.md at master · zenghongtu/react-use-chinese](https://github.com/zenghongtu/react-use-chinese/blob/master/README.md)

### Hooks使用规则
#### 必须使用useXxx格式来命名
#### 只能在两个地方调用Hook（组件内，其他Hook内）
组件外、<font style="color:#DF2A3F;">普通函数内都不可以</font>调用Hook

#### 必须保证每次的调用顺序一样（<font style="color:#DF2A3F;">不能放在if、for中！！！</font>）
**<font style="color:#DF2A3F;">hook必须放在第一层，不能有前置执行条件！！！</font>**

### Hooks闭包陷阱
- [x] 当异步获取state时，可能不是最新的state（主要针对原始值类型的变量，包括<font style="color:rgb(71, 71, 71);">String、Number、Boolean、Undefined、Null以及ES6引入的Symbol）</font>
- [x] 可以使用**<font style="color:#DF2A3F;">useRef</font>**来解决（ref是引用类型）

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1732635502951-e64dc015-0c0c-4183-be1b-5f284034d9ba.png)

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1732635564113-f189d9fe-2bb2-4300-a1cc-0736926c2217.png)

## 在React中使用css
目标：

- [x] 学会在react中使用css的几种方案
- [x] 选择一个合适的css解决方案
- [x] 重构列表页，加入css样式

内容：

1. 内联style+引入css文件
2. css-Module + sass
3. css-in-js - Styled-components 和 Styled-jsx

### 常规使用方式
#### 内联css（尽量不要使用，性能差）
```tsx
<span style={{ color: 'pink' }}>已发布</span>
```

#### 引入外部css文件（单独缓存文件，可复用代码）
```tsx
import '.././App.css'
<div key={id} className="list-item"> //直接写App.css中的类名即可
    </div>
```

#### <font style="color:#DF2A3F;">classNames(</font>工具库)----根据条件动态设置类名
安装，然后直接使用即可

[Classnames by JedWatson](https://jedwatson.github.io/classnames/)

##### 使用一：传入多个变量
```tsx
  const itemClassNames = classNames('list-item', 
                                    { published: isPublished })
  return (
    <div key={id} className={itemClassNames}>
```

##### 使用二：将全部类名以对象的形式传入，用true和false来控制是否添加变量名
```tsx
  const itemClassNames = classNames({ 'list-item': true, 
                                      published: isPublished })
  return (
    <div key={id} className={itemClassNames}>
      <strong>{name}</strong>
```

##### 动态类名，用 [ ]
```tsx
  const publishedClassName = 'published'
  const itemClassNames = classNames({ 'list-item': true, 
                                      [publishedClassName]: isPublished })
```

#### clsx工具库
[GitHub - lukeed/clsx: A tiny (239B) utility for constructing `className` strings conditionally.](https://github.com/lukeed/clsx)

安装和使用方法基本和classNames一样！

[react 使用clsx库动态构建类名_react clsx-CSDN博客](https://blog.csdn.net/an_jia_ning/article/details/135817332)

### cssModule(解决不同组件类名冲突问题)
如果父子组件中都用了相同的css名称，css样式会出现问题

- [x] 在react中一般都是一个组件对应一个css文件
- [x] 原理：<font style="color:rgb(37, 41, 51);">在CSS Modules中，原始的CSS类名（选择器）会被转换成一个</font>**<font style="color:rgb(37, 41, 51);">独一无二</font>**<font style="color:rgb(37, 41, 51);">的类名。例如，</font>`<font style="color:rgb(255, 80, 44);background-color:rgb(255, 245, 245);">.class</font>`<font style="color:rgb(37, 41, 51);">可能会被转换成</font>`<font style="color:rgb(255, 80, 44);background-color:rgb(255, 245, 245);">.class_abc_123</font>`<font style="color:rgb(37, 41, 51);">这样的形式。这种转换是通过静态分析工具和构建工具在构建过程中</font>**<font style="color:rgb(37, 41, 51);">自动完成</font>**<font style="color:rgb(37, 41, 51);">的。</font>
- [x] Create-React-App原生支持css Module

#### 用法
1. 改文件名字：将css文件命名为：**<font style="color:#DF2A3F;">xxx.module.css</font>**
2. 引入 style，通过**<font style="color:#DF2A3F;">style['样式名']</font>**来实现

```tsx
import styles from './questioncard.module.css'
  const itemClassNames = classNames({
    [styles['list-item']]: true,
    [publishedClassName]: isPublished,
  })
```

- [x] 页面中的样式名称

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1733044936341-27b457d7-d344-4c1c-88cd-13d46d4c2ab5.png)

### 使用sass
- [x] css语法比较原始，如不能嵌套
- [x] 现代css一般用less、sass等预处理工具
- [x] CAR原生支持sass module，css文件后缀改为.scss即可

[Sass基础教程 Sass快速入门 Sass中文手册 | Sass中文网](https://www.sass.hk/guide/)

[Sass教程 Sass中文文档 | Sass中文网](https://www.sass.hk/docs/)

### Css-in-Js
- [x] 一种解决方案，而不是工具名称，有好几种工具
- [x] 在js中写css，带来极大的灵活性
- [x] 它和内联style完全不一样，也不会有内联style的问题（如，体积会增大，可读性差）

#### 工具一：styled-components
[styled-components](https://styled-components.com/)

##### 安装之后引入<font style="color:#DF2A3F;">styled</font>
```tsx
import styled from 'styled-components'

const Button = styled.button`
  height: 40px;
  width: 80px;
  background-color: pink;
  border: none;
  border-radius: 5px;
`
```

#### 工具二：styled-jsx和Emotion
[GitHub - vercel/styled-jsx: Full CSS support for JSX without compromises](https://github.com/vercel/styled-jsx)

[Emotion – Introduction](https://emotion.sh/docs/introduction)

- [x] 在typescript环境下，需要扩展jsx属性，带来麻烦

### 优点和缺点
1. 优点：用js写，有变量有逻辑，非常灵活
2. 缺点：jsx和样式代码混在一起，代码比较多；增加了编译成本
3. 适用场景：需要灵活变换样式

## tailwindcss
[Flex Basis - TailwindCSS中文文档 | TailwindCSS中文网](https://www.tailwindcss.cn/docs/flex-basis)

## 路由
[带你使用 React 路由 react-router-dom v6前言 在浏览器中页面的跳转是根据地址栏 url 的变化 - 掘金](https://juejin.cn/post/7298682235975270440#heading-11)

1. 路由设计、网页和页面的关系
2. 增加页面和layout模板
3. 使用React-router增加路由配置（react中唯一的路由管理工具）
- [x] 按设计，新建若干个页面（即react组件）
- [x] 为每个页面配置对应的路由
- [x] 分配相应的layout模板

### 路由设计
![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1734878066554-712a3dee-1131-4178-848f-21e6299538d1.png)

### layout模板（全局框架布局的概念？）
+ 大部分页面，除了编辑、统计，都需要header、footer----mainlayout
+ 问卷管理都需要左侧的导航菜单----manageLayout
+ 问卷编辑、统计-QuestionLayout（后面讲）

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1735978511635-639cc7fe-3e1d-45b5-9d5d-dded3d55338e.png)

### React-router（react-router-dom）--react路由管理工具
1. 新建若干个页面和layout
2. 使用React-router 配置路由并用于项目
3. 使用路由功能，如页面跳转、获取参数等

#### <font style="background-color:#FBDE28;">outlet（相当于vue中的插槽）</font>
TODO：了解更多

#### 常用Hooks
[React中常用的hook函数(四)——useRef、useNavigate、useLocation和useSearchParams-CSDN博客](https://blog.csdn.net/Mrs_Lupin/article/details/143666208)

#### 路由配置
##### 在route配置文件中使用<font style="color:#DF2A3F;">createBrowserRouter</font>([{}])
```tsx
const router = createBrowserRouter([
  {
    path: '/',
    element: <MainLayout />,
    children: [
      {
        path: '/',
        element: <Home />,
      },
      {
        path: 'login',
        element: <Login />,
      },
      {
        path: 'manage',
        element: <ManageLayout />,
        children: [
          {
            path: 'list',
            element: <MyQuestionList />,
          },
        ],
      },
      {
        path: '*', // 404 路由配置，都写在最后（兜底）
        element: <NotFound />,
      },
    ],
  },

]);
```

##### 在app.tsx中使用<font style="color:#DF2A3F;">RouterProvider</font>挂载路由
```tsx
import { RouterProvider } from 'react-router-dom';
import routerConfig from './router';

function App() {
  return <RouterProvider router={routerConfig}></RouterProvider>;
}
```

#### 路由跳转----<font style="color:#DF2A3F;">useNavigate和Link</font>
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737187907688-50831a7f-21bd-4d12-8ef1-9d616c1eb497.png)

[react-routerV6 路由传递参数的三种方式_react router v6路由传参-CSDN博客](https://blog.csdn.net/qq_43886365/article/details/131086279)

[https://juejin.cn/post/7154536292846403591](https://juejin.cn/post/7154536292846403591)

```tsx
import { useNavigate, Link } from 'react-router-dom';
const Home: FC = () => {
  const nav = useNavigate();
  function handleNavigate(path: string) {
    // nav(path);
    // 传递参数
    nav({
      pathname: path,
      search: 'b=100',
    });
  }
  return (
    <div>
      <div>首页</div>
      <button onClick={() => handleNavigate('/login')}>跳转至登陆页面</button>
      <br></br>
      <Link to={'/register?a=10'}>跳转至注册页面</Link>
    </div>
  );
};
```

#### 传递参数&获取
##### <font style="color:#DF2A3F;">param传参-</font>---路由配置---设置占位符
- [x] 配置

```tsx
{
  path: 'static/:id', // statistic 统计
  element: <Static />,
},
```

- [x] 传递参数

```tsx
  <Button
    type="text"
    icon={<EditOutlined />}
    onClick={() => navigate(`/question/edit/${_id}`)}
  >
    编辑问卷
  </Button>
```

- [x] 取参----**<font style="color:#DF2A3F;">useParams()</font>**

```tsx
import { useParams } from "react-router-dom";

const Login: React.FC = (props: any) => {
  const onFinish = () => {
  // 使用useParams 函数
  const params = useParams()
  console.log("params:",params);// 打印 {   "name": "Eula",    "age": "18"}
  };
}

```

##### searchParam传参----路由通过问号拼接
```tsx
<Link to={'/register?a=10'}>跳转至注册页面</Link>
或者
const nav = useNavigate();
function handleNavigate(path: string) {
  // 传递参数
  nav({
    pathname: path,
    search: 'b=100',
  });
}
```

- [x] 取参----**<font style="color:#DF2A3F;">useSearchParams( )</font>**

```tsx
import { useSearchParams } from 'react-router-dom';
  const [searchParams] = useSearchParams();
  console.log('搜索参数', searchParams.get('keywords'));
```

##### state传递参数----<font style="color:rgb(51, 51, 51);background-color:rgb(254, 251, 254);">useLocation </font>
- [x] **<font style="color:#DF2A3F;">useLocation</font>**：<font style="color:rgb(51, 51, 51);background-color:rgb(254, 251, 254);">获取当前路由的位置信息，包括</font>**<font style="color:#DF2A3F;background-color:rgb(254, 251, 254);">路径名、查询参数、状态</font>**<font style="color:rgb(51, 51, 51);background-color:rgb(254, 251, 254);">等</font>

### 设置网页标题和icon
#### 修改public/index.html----全局修改
#### 第三方hook----aHook中的hook函数（如useTitle....)
可单独修改某个页面的网页标题和icon

[https://ahooks.js.org/zh-CN/hooks/use-title](https://ahooks.js.org/zh-CN/hooks/use-title)

## antDesign UI组件库的使用
[Ant Design of React - Ant Design](https://ant.design/docs/react/introduce-cn)

+ 了解react相关的UI组件库
+ 学习使用ant-Design
+ 使用ant-design重构页面

#### react相关ui组件库
1. ant-design，国内最常用的react UI组件库，没有之一
2. material UI 国外非常流行
3. tailwind UI 国外流行，但收费
- [x] 样式穿透：[https://www.zhihu.com/question/606030243](https://www.zhihu.com/question/606030243)

### 表单组件
- [x] 学习react表单组件、**受控组件**
- [x] 学习ant-design表单组件，并实战
- [x] 表单组件的校验和错误提示，几种方案

#### 受控组件VS非受控组件
- [x] 受控组件：值同步到state，使用**<font style="color:#601BDE;">value</font>**属性
- [x] 非受控组件：值不同步state，使用**<font style="color:#601BDE;">defaultValue</font>**属性
- [x] React推荐使用受控组件，看似繁琐，但更加可控

#### <font style="color:rgb(0, 0, 0);">dangerouslySetInnerHTML----将富文本解析为html</font>
- [x] **<font style="color:#DF2A3F;">这种方式非常危险，不安全</font>**，容易被第三方嵌入链接、广告、视频等等非文本内容

[https://juejin.cn/post/6951334999920476191](https://juejin.cn/post/6951334999920476191)

```tsx
<p dangerouslySetInnerHTML={{ __html: text.replaceAll('\n', '<br>') }}></p>
```



#### react表单组件
##### label标签
[react教程，如何理解使用react中label的htmlFor属性？](https://newsn.net/say/react-htmlfor.html)

- [x] 使用htmlFor标签绑定html元素
- [x] 将html元素包括在label标签内

#### 用constant文件来管理项目全局常量
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737212839536-27b394a3-42e8-4710-a4c9-ce094249592d.png)

### 第三方表单校验工具----Formik、react-hook-form
[Overview | Formik](https://formik.org/docs/overview)

[React Hook Form - performant, flexible and extensible form library](https://react-hook-form.com/)

## Ajax网络请求
- [x] 搭建mock服务（作为临时服务）
- [x] 使用ajax和服务端通讯，并引用于现有功能
- [x] API设计，使用RestfulAPI

### mock数据
[Mock.js](http://mockjs.com/)

- [x] 使用mock.js
- [x] 使用nodejs服务+mock.js
- [x] 使用在线mock平台

#### mock.js-----不推荐在项目中直接使用mock.js
1. 前端代码中引入mock.js
2. 定义要模拟的路由，返回结果
3. mock.js劫持ajax请求，得到模拟的结果
- [x] mock.js只能劫持XMLXMLHttpRequest，不能劫持fetch
- [x] 要在生产环境中（上线时）注释掉，否则线上请求也将被劫持

#### <font style="color:#DF2A3F;">推荐----nodejs服务+mock.js（koa + mock.Random)</font>
+ mock.js两大功能：劫持Ajax+全面的Random能力
+ 把mock.js用于node.js服务端，使用random能力

[Mock.Random](https://github.com/nuysoft/Mock/wiki/Mock.Random)

##### 流程
1. 创建mock项目文件夹
2. 使用node init -y 来初始化项目
3. 安装mockjs来写mock接口----commonJs的语法，使用require来导入，module.export导出，并将写好的全部mock的api在index文件中导出

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737797344775-422d2894-be5f-4402-9e7e-9da70d02d15a.png)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737797308064-d20c3c11-9b9f-4cbf-9275-80d3ab2d4037.png)

4. 安装koa，在index中注册mock路由，挂载mock路由，监听端口

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737797733936-1159b30b-8a7b-4b62-8c51-09c6e30af6bc.png)

5. 在package.json中的script中补充启动脚本

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737797827058-737f8718-ea5d-49e1-9e48-8c6d98156469.png)

6. 运行脚本，启动服务

#### nodemon
[nodemon](https://link.juejin.cn/?target=http%3A%2F%2Fnodemon.io%2F)<font style="color:rgb(37, 41, 51);"> 是一种工具，可在检测到目录中的文件更改时通过</font>**<font style="color:rgb(37, 41, 51);">自动重新启动</font>**<font style="color:rgb(37, 41, 51);"> node 应用程序来帮助开发基于 node.js 的应用程序。</font>

#### koa-----web开发框架，启动mockjs写的api 服务
[Koa 中文网](https://koa.nodejs.cn/)

[https://juejin.cn/post/7208005547004919867](https://juejin.cn/post/7208005547004919867)

<font style="color:rgb(37, 41, 51);">Koa 作为 Web 开发微框架，可以用于传统 Web 应用开发、作为服务器端接口、作为独立的API层、网关等等场景。</font>

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737787389731-172cf7c8-d5d5-43ef-92fd-96b424d75009.png)

#### craco.js----解决mock跨域问题
[入门 | CRACO 中文](https://craco.reactjs.ac.cn/docs/getting-started/)

- [x] **使用craco.js扩展webpack配置**

Craco.js是一个基于Webpack的扩展框架，其主要目的是为React项目提供灵活的配置选项。它**允许你自定义Webpack的配置，而无需修改底层的构建工具**。Craco.js通过提供一个简单的接口来修改默认的Webpack配置，使得开发者能够轻松地调整项目的构建过程。

[AccessDeny](https://www.imooc.com/article/359737)

- [x] 配置跨域端口

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1737811160320-1ad72772-180e-4b66-845f-944d0f82b698.png)

#### koa中 ctx 获取请求参数
在mock路由注册页面，使用ctx，获取请求参数，控制返回数据！！

##### ctx.url
##### query参数：ctx.query
##### 路径参数：ctx.params
##### body参数：安装 koa-body插件，在文件中引入（require）、使用（use），参数（ctx.request.body）
```tsx
const { koaBody } = require("koa-body");

app.use(koaBody());

router.post("/", (ctx) => {
  const body = ctx.request.body;
  ctx.body = body;
});


```

#### 不推荐----在线mock平台
##### 存在风险
1. 网站不稳定、不维护
2. 存在敏感数据泄漏的风险

##### apifox（支持本地+云端）
[帮助中心 - Apifox 帮助文档](https://docs.apifox.com/)

[Apifox - API 文档、调试、Mock、测试一体化协作平台。拥有接口文档管理、接口调试、Mock、自动化测试等功能，接口开发、测试、联调效率，提升 10 倍。最好用的接口文档管理工具，接口自动化测试工具。](https://apifox.com/)

##### postman-----测试接口+mock接口数据
### API设计----使用restfal API规范
1. 使用restful API
2. 用户验证使用JWT
3. 返回统一格式：code、data、msg

### 实战
#### 配置axios基础功能
[axios 拦截器实现原理 - 蓓蕾心晴 - 博客园](https://www.cnblogs.com/beileixinqing/p/18175323)

- [x] response拦截器
- [x] request拦截器
1. 开发问卷功能，期间使用useRequest
2. 分页和LoadMore

#### useRequest
`<font style="color:rgb(213, 97, 97);background-color:rgb(246, 247, 249);">useRequest</font>`<font style="color:rgb(69, 77, 100);"> 的第一个参数是一个异步函数，在组件初次加载时，会自动触发该函数执行。同时自动管理该异步函数的 </font>`<font style="color:rgb(213, 97, 97);background-color:rgb(246, 247, 249);">loading</font>`<font style="color:rgb(69, 77, 100);"> , </font>`<font style="color:rgb(213, 97, 97);background-color:rgb(246, 247, 249);">data</font>`<font style="color:rgb(69, 77, 100);"> , </font>`<font style="color:rgb(213, 97, 97);background-color:rgb(246, 247, 249);">error</font>`<font style="color:rgb(69, 77, 100);"> 等状态</font>

`<font style="color:rgb(213, 97, 97);background-color:rgb(246, 247, 249);">useRequest</font>`<font style="color:rgb(69, 77, 100);"> </font><font style="color:rgb(69, 77, 100);">通过插件式组织代码，核心代码极其简单，并且可以很方便的扩展出更高级的功能。目前已有能力包括：</font>

+ <font style="color:rgb(69, 77, 100);">自动请求/手动请求</font>
+ <font style="color:rgb(69, 77, 100);">轮询</font>
+ <font style="color:rgb(69, 77, 100);">防抖</font>
+ <font style="color:rgb(69, 77, 100);">节流</font>
+ <font style="color:rgb(69, 77, 100);">屏幕聚焦重新请求</font>
+ <font style="color:rgb(69, 77, 100);">错误重试</font>
+ <font style="color:rgb(69, 77, 100);">loading delay</font>
+ <font style="color:rgb(69, 77, 100);">SWR(stale-while-revalidate)</font>
+ <font style="color:rgb(69, 77, 100);">缓存</font>

[ahooks 3.0](https://ahooks.js.org/zh-CN/hooks/use-request/index)

#### 分页
传递请求参数pageSize和pageNo

- [x] fixed定位只作用于视口，而不是父元素！

#### jwt（json web token）登陆鉴权
- [x] token处理方法
- [x] 添加请求拦截器，在每次发起请求之前，将token以固定格式放到header里的Authorization里去

## Redux状态管理
- [x] React内置功能Context和useReducer
- [x] 第三方工具Redux和Mobx
- [x] 使用Redux管理用户状态

为何要使用状态管理

+ 适用：页面足够复杂：组件很多，嵌套层级很深
+ 通过props层层传递不合适
+ 需要状态管理，即集中、统一管理页面数据

### Context ---- 类似于Vue的provide/inject
- [x] **<font style="color:#DF2A3F;">跨层级共享数据</font>**：可跨层级传递，而不像props层层传递

#### 场景
+ **<font style="color:rgb(35, 39, 47);">主题/语言：</font>**<font style="color:rgb(35, 39, 47);"> 如果你的应用允许用户更改其外观（例如暗夜模式），你可以在应用顶层放一个 context provider，并在需要调整其外观的组件中使用该 context。</font>
+ **<font style="color:rgb(35, 39, 47);">当前账户：</font>**<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">许多组件可能需要知道当前登录的用户信息。将它放到 context 中可以方便地在树中的任何位置读取它。某些应用还允许你同时操作多个账户（例如，以不同用户的身份发表评论）。在这些情况下，将 UI 的一部分包裹到具有不同账户数据的 provider 中会很方便。</font>
+ **<font style="color:rgb(35, 39, 47);">路由：</font>**<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">大多数路由解决方案在其内部使用 context 来保存当前路由。这就是每个链接“知道”它是否处于活动状态的方式。如果你创建自己的路由库，你可能也会这么做。</font>
+ **<font style="color:rgb(35, 39, 47);">状态管理：</font>**<font style="color:rgb(35, 39, 47);"> </font><font style="color:rgb(35, 39, 47);">随着你的应用的增长，最终在靠近应用顶部的位置可能会有很多 state。许多遥远的下层组件可能想要修改它们。通常</font><font style="color:rgb(35, 39, 47);"> </font>[将 reducer 与 context 搭配使用](https://zh-hans.react.dev/learn/scaling-up-with-reducer-and-context)<font style="color:rgb(35, 39, 47);">来管理复杂的状态并将其传递给深层的组件来避免过多的麻烦。</font>

<font style="color:rgb(35, 39, 47);">Context 不局限于静态值。如果你在下一次渲染时传递不同的值，React 将会更新读取它的所有下层组件！这就是 context 经常和 state 结合使用的原因。</font>

<font style="color:rgb(35, 39, 47);">一般而言，如果树中不同部分的远距离组件需要某些信息，context 将会对你大有帮助。</font>

[Context – React](https://zh-hans.legacy.reactjs.org/docs/context.html)

[使用 Context 深层传递参数 – React 中文文档](https://zh-hans.react.dev/learn/passing-data-deeply-with-context)

#### 使用方法
1. 定义context：使用**<font style="background-color:#FBDE28;">createContext()</font>**定义
2. 在父组件中引入context，使用**<font style="background-color:#FBDE28;"><context.provider value={要跨层级传的变量}> </context.provider></font>**

```tsx
import  {UserContext} from './userContext.tsx'

<UserContext.provider value={{name:'Liao'}}>
  <Sub></Sub>
</UserContext.provider>
```

3. 在被包裹的任意一个子组件中，引入定义的context，并使用**<font style="background-color:#FBDE28;">useContext(context)</font>**获取被传递的值

```tsx
import {useContext} from 'react'
import { UserContext} from './userContext.tsx'

const data = useContext(UserContext)  //data即为跨层传递的数据
```

### reducer管理状态
- [x] 将组件的事件处理逻辑整合到reducer函数中，事件触发时，通过 dispatch reducer 函数中对应的action，来实现数据更新，适用于复杂逻辑组件，可以增强代码可读性
- [x] 可将状态更新整合至外部文件中，独立于组件进行状态管理
- [x] 简单组件还是使用useState

[迁移状态逻辑至 Reducer 中 – React 中文文档](https://zh-hans.react.dev/learn/extracting-state-logic-into-a-reducer#)

#### 使用
1. <font style="color:rgb(35, 39, 47);">将设置状态的逻辑 </font>**<font style="color:rgb(35, 39, 47);">修改</font>**<font style="color:rgb(35, 39, 47);"> 成 dispatch 的一个 action</font>

```tsx
function handleAddTask(text) {
  setTasks([
    ...tasks,
    {
      id: nextId++,
      text: text,
      done: false,
    },
  ]);
}
```

```tsx
function handleAddTask(text) {
  dispatch(
    // 传递的为action对象
    {
    type: 'added',
    id: nextId++,
    text: text,
    }
  );
}
```

- [x] action对象的内容自定义，但是通常用一个**<font style="color:#DF2A3F;">type属性</font>**来描述行为
2. **<font style="color:rgb(35, 39, 47);">编写</font>**<font style="color:rgb(35, 39, 47);"> 一个 reducer 函数（自定义函数）：它接 受两个参数，分别为当前 state变量 和 action 对象，可以返回</font>**<font style="color:#DF2A3F;">新的 state</font>**<font style="color:rgb(35, 39, 47);">（不需要像一般函数一样获取返回值，只要返回了直接就是改变的state，改变对象和数组的方式与useState一样）</font>

```tsx
function yourReducer(state, action) {
  // 给 React 返回更新后的状态
}
```

3. <font style="color:rgb(35, 39, 47);">在你的组件中 </font>**<font style="color:rgb(35, 39, 47);">使用</font>**<font style="color:rgb(35, 39, 47);"> reducer：引入自定义的reducer函数，并通过const[tasks,dispatch] = useReducer(yourReducer, state)</font>

```tsx
const [tasks, dispatch] = useReducer(tasksReducer, initialTasks);
```

#### useReducer
- [x] useState的代替方案f
- [x] 数据结构简单时用useState，复杂时用useReducer

在组件的顶层作用域调用useReducer来创建一个用于状态管理的state

[useReducer – React 中文文档](https://zh-hans.react.dev/reference/react/useReducer)

#### 结合context解决跨组件问题
1. 创建state和dispatch的context，其中dispatch为函数

```tsx
const TestContext = createContext({
  state: initialState,
  dispatch: (action: any) => {},
})
```

2. 使用useReducer获取处理的state和dispatch

```tsx
const [state, dispatch] = useReducer(testReducer, initialState)
```

3. 通过context向子组件共享state和dispatch

```tsx
<TestContext.Provider value={{ state, dispatch }}>
  <TestReducerChild />
</TestContext.Provider>
```

4. 在子组件中通过useContext获取最新的state和dispatch

#### state dispatch默认没有模块化，数据混在一起
### Redux----react最流行的状态管理工具（第三方工具）
- [x] **<font style="color:#DF2A3F;">默认支持跨组件通讯，无需其他功能协助</font>**
- [x] **<font style="color:#DF2A3F;">store reducer可拆分模块</font>**，更适合复杂数据结构
- [x] 有开发者工具和插件
- [x] 单向数据流

[Redux 中文官网 - JavaScript 应用的状态容器，提供可预测的状态管理。 | Redux 中文官网](https://cn.redux.js.org/)

#### 使用
[快速开始 | Redux 中文官网](https://cn.redux.js.org/tutorials/quick-start)

1. 安装React-Reduce和Reduce-Toolkit

```tsx
npm install @reduxjs/toolkit react-redux
```

2. 创建src/stor文件夹，创建index.ts文件，并从redux toolkit引入configureStore API，创建一个空的redux store 并导出它

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1739783019792-f3d3730e-87b9-446c-9866-d0c780780c09.png)

3. 为react提供Redux Store：在src/index.js中引入刚刚创建的store，通过React-Redux中的<Provider>将APP包裹起来，并将store作为参数传入
- [x] provider实现数据跨组件传递

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1739783973157-a0af50d8-0b92-4e9a-adf5-328cd61ada7a.png)

4. 在store文件夹下创建逻辑模块文件（如count.ts），在该文件中，从redux-toolkit 引入 createSlice API，创建该模块的reducer，并导出reducer函数和该reducer
    - [x] name
    - [x] initialState
    - [x] reducers
    - [x] .actions
    - [x] .reduecer

```tsx
import { createSlice } from '@reduxjs/toolkit'

const countSlice = createSlice({
  name: 'count',
  initialState: 0,
  reducers: {
    increment(state) {
      return state + 1  //返回一个state，不可变数据
    },
    decrement(state) {
      return state - 1
    },
  },
})

export const { increment, decrement } = countSlice.actions
export default countSlice.reducer
```

5. 将该模块reducer添加到lindex.ts的reducer中，属性名字要和模块reducer 的name属性名字一致

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1739783606026-af0b4a87-736e-4ade-aa50-a652308b15a8.png)

6. 数据使用（useSelector+useDispatch）

```tsx
import React, { FC } from 'react'
import { useSelector, useDispatch } from 'react-redux'
import { reducerType } from './store/index'
import { increment, decrement } from './store/count'

const DemoRedux: FC = () => {
  // 此处的state时store/index中写的reducer!!
  const count = useSelector((state: reducerType) => state.count)
  const dispatch = useDispatch()
  return (
    <>
      <h1>demo redux</h1>
      <div>
        <span>{`count:${count}`}</span>
        <button onClick={() => dispatch(increment())}>+</button>
        <button onClick={() => dispatch(decrement())}>-</button>
      </div>
    </>
  )
}

export default DemoRedux

```

#### useSelector 和 useDispatch
[Hooks | React Redux 中文文档](https://cn.react-redux.js.org/api/hooks/#%E5%9C%A8-react-redux-%E5%BA%94%E7%94%A8%E4%B8%AD%E4%BD%BF%E7%94%A8-hooks)

#### createSlice中的reducer函数，传递额外参数（payload）
- [x] 参数名<font style="background-color:#FBDE28;"> </font>**<font style="color:#DF2A3F;background-color:#FBDE28;">actions：PayloadAction<实际参数类型></font>**；
- [x] import { PayloadAction } from '@reduxjs/toolkit'
- [x] 通过**<font style="color:#DF2A3F;background-color:#FBDE28;"> actions.payload </font>**获取传递进来的参数

```tsx
import { createSlice, PayloadAction } from '@reduxjs/toolkit'

const todoListSlice = createSlice({
  name: 'todoList',
  initialState: INIT_STATE,
  reducers: {
    addTodo(state: TodoType[], actions: PayloadAction<TodoType>) {
      return [...state, actions.payload]
    },
    removeTodo(state: TodoType[], actions: PayloadAction<{ id: string }>) {
      const { id: removeId } = actions.payload
      return state.filter(item => item.id !== removeId)
    },
    toggleComplete(state: TodoType[], actions: PayloadAction<{ id: string }>) {
      const { id: toggleId } = actions.payload
      return state.map(item => {
        if (item.id === toggleId) {
          return { ...item, completed: !item.completed }
        }
        return item
      })
    },
  },
})
```

#### Redux DevTools----redux开发者工具（谷歌浏览器插件）
### MobX----声明式的修改数据，像vue一样
## 开发问卷编辑器
- [x] 目标
    1. 完成问卷编辑器的设计和开发
    2. 体验复杂系统的UI组件拆分
    3. 体验复杂系统的数据结构设计
- [x] 内容
    1. 需求分析
    2. 技术方案设计
    3. 开发（内容较多）
- [x] 注意事项
    1. 需求指导设计，设计指导开发。前两步很重要
    2. 但是页面较复杂，要边设计边开发，否则容易脱节
    3. 内容较多，要跟随一起练习

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1739958794939-4d74ca3b-3a43-4cd2-b008-cbd63a02e644.png)

#### 实用
- [x] css实现屏蔽鼠标点击事件！

```tsx
.component{
    pointer-events: none;   //屏蔽鼠标行为！！！！
}
```

```tsx
<div className={styles.component}>
  <QuestionInput></QuestionInput>
</div>
```

- [x] 绑定键盘快捷键----ahooks中的useKeyPress

[useKeyPress - ahooks 3.0](https://ahooks.js.org/zh-CN/hooks/use-key-press)

- [x] ahooks中的**<font style="color:#DF2A3F;">useDebunceEffect </font>**自动监听变换，防抖执行函数！！！
- [x] 选择第三方插件

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1743666298477-be553a9f-47e0-44d0-9f69-4f6916cd37d6.png)

- [x] 第三方拖拽组件：dnd-kit：[https://docs.dndkit.com/presets/sortable](https://docs.dndkit.com/presets/sortable)
- [x] 撤销重做功能实现原理

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1743754955914-ebdc00e1-c79a-4a48-8177-38a091ec664d.png)

- [x] redux中的撤销重做插件：redux-undo：[https://github.com/omnidan/redux-undo](https://github.com/omnidan/redux-undo)

## 开发统计问卷统计页面
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1743776838318-97b33d8c-901c-4bbe-9107-7e5d09762621.png)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1743777003269-2efebed2-116e-4506-9375-ce2e90a59f86.png)

### 第三方图表库选择：综合选择Recharts
[https://recharts.org/](https://recharts.org/)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744171603527-4d9be833-769e-4d76-ac81-fb3153f177ba.png)

## C端：使用Next.js来开发问卷H5	
- [x] 掌握SSR
- [x] 掌握Next.jsh使用
- [x] 开发H5，并和问卷发布、统计功能打通

### SSR介绍（serve side render）服务端渲染
+ SSR介绍（serve side render）服务端渲染
+ CSR-Client side render 客户端渲染

##### 对比
- [x] 优点
    1. 性能好
    2. 易于SEO搜索引擎优化（但搜索引擎也在不断进化）
- [x] 缺点
    1. 开发成本高（前端框架+ Node.js，全栈）

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744206262152-d538d205-27e6-4ece-9e0d-63ecb3227367.png)

##### 应用场景
+ 对性能要求高的系统，如移动端、弱网环境
+ 操作交互简单的系统，否则复杂度会更高
+ 如B端，不适合用ssr，（性能要求不高，操作复杂）

##### 常见框架
+ react：Next.js
+ vue: Nuxt.js

### Next.js ----[中文官方网站](https://www.nextjs.cn/docs/getting-started)
#### 创建项目并启动
[Next.js里app和pages文件夹的区别_nextjs app pages-CSDN博客](https://blog.csdn.net/AshleyXM/article/details/139211982)

[Next.js 开发指南 路由篇 | App Router - Ready! - 博客园](https://www.cnblogs.com/silva/p/17948723)

#### 路由规范
[https://juejin.cn/post/7292299401224667145](https://juejin.cn/post/7292299401224667145)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744600563300-6b0938b9-fc22-43cb-9d2c-dc8ffae0240b.png)![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744350661827-210c637d-fe1c-4a16-8051-dcb335590d0e.png)

#### api接口----全部接口都以api开头
[Next.js提供api接口_nextjs api 接口代理配置api key 调用接口-CSDN博客](https://blog.csdn.net/zSY_snake/article/details/146232999)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744356003315-7abec826-ae9d-47a6-9e4d-d771a4505b6c.png)

#### public文件夹----静态文件和数据，可直接通过浏览器访问
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744356222189-6bb7adcc-135a-4b4e-817d-ce1cc5f6d8e3.png)

### 两种形式的pre-render，都是ssr
[Making Sense of React Server Components • Josh W. Comeau](https://www.joshwcomeau.com/react/server-components/)

<font style="color:rgb(64, 64, 64);"></font><font style="color:rgb(64, 64, 64);">Next.js 13+ 的 App Router 中，渲染策略更加自动化：</font>

1. **<font style="color:rgb(64, 64, 64);">默认静态</font>**<font style="color:rgb(64, 64, 64);">：除非使用动态函数或明确选择动态渲染</font>
2. **<font style="color:rgb(64, 64, 64);">动态检测</font>**<font style="color:rgb(64, 64, 64);">：使用</font><font style="color:rgb(64, 64, 64);"> </font>`**<font style="color:rgb(64, 64, 64);background-color:rgb(236, 236, 236);">cookies()</font>**`<font style="color:rgb(64, 64, 64);">,</font><font style="color:rgb(64, 64, 64);"> </font>`**<font style="color:rgb(64, 64, 64);background-color:rgb(236, 236, 236);">headers()</font>**`<font style="color:rgb(64, 64, 64);">,</font><font style="color:rgb(64, 64, 64);"> </font>`**<font style="color:rgb(64, 64, 64);background-color:rgb(236, 236, 236);">searchParams</font>**`<font style="color:rgb(64, 64, 64);"> </font><font style="color:rgb(64, 64, 64);">等会自动启用动态渲染</font>
3. **<font style="color:rgb(64, 64, 64);">混合渲染</font>**<font style="color:rgb(64, 64, 64);">：同一路由中不同组件可以采用不同策略</font>

#### static generation 项目构建时，直接产出HTML文件 （用getStaticProps）
    1. 新方法，直接在文件中调用函数请求数据（该函数只会在项目构建时触发一次）（默认静态）
    2. 新方法：**<font style="color:#DF2A3F;background-color:rgb(247, 247, 247);">generateStaticParams</font>**

##### <font style="color:rgb(23, 23, 23);background-color:rgb(247, 247, 247);">generateStaticParams</font>
[https://nextjs.org/docs/app/api-reference/functions/generate-static-params](https://nextjs.org/docs/app/api-reference/functions/generate-static-params)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744605144799-83fb8709-deb9-44e9-902c-80201ed86437.png)

`**<font style="color:rgb(64, 64, 64);background-color:rgb(236, 236, 236);">generateStaticParams</font>**`<font style="color:rgb(64, 64, 64);"> </font><font style="color:rgb(64, 64, 64);">是一个异步函数，用于：</font>

+ <font style="color:rgb(64, 64, 64);">指定哪些动态路由参数组合应该被静态生成</font>
+ <font style="color:rgb(64, 64, 64);">在构建时(pre-render)为这些参数组合生成静态页面</font>
+ <font style="color:rgb(64, 64, 64);">支持增量静态再生(ISR)模式</font>
- [x] **<font style="color:rgb(64, 64, 64);">基本语法</font>**

<font style="color:rgb(255, 255, 255);background-color:rgb(255, 255, 255) !important;">t</font>

```plain
// app/[slug]/page.tsx
export async function generateStaticParams() {
  return [
    { slug: 'article1' },
    { slug: 'article2' },
    // 更多参数...
  ];
}
```

- [x] <font style="color:rgb(64, 64, 64);"> </font>**<font style="color:rgb(64, 64, 64);">返回格式要求</font>**
+ <font style="color:rgb(64, 64, 64);">必须返回对象数组</font>
+ <font style="color:rgb(64, 64, 64);">每个对象的键必须</font>**<font style="color:rgb(64, 64, 64);">精确匹配</font>**<font style="color:rgb(64, 64, 64);">动态路由段名称</font>
+ <font style="color:rgb(64, 64, 64);">值必须是字符串或字符串数组(对于捕获所有路由)</font>

#### server side rendering 每次请求时动态拼接出HTML（用getServerSideProps）
    3. 新方法：自动接收**<font style="color:#DF2A3F;">searchParam</font>**，<font style="color:#DF2A3F;">该函数在每次请求都触发一次</font>

```tsx


// import getString from '../api/hello/route'
interface propsType {
  info: string
}

export default async function About({
  searchParams,
}: {
  searchParams: Promise<propsType>
}) {
  const {info} =  await searchParams // 获取查询参数 info
  const data:propsType = await getStaticProps111(info);
  return (
    <div>
      About1111
      <p>{data.info}</p>
    </div>
  );
}

async function getStaticProps111(searchParams: string) {
  console.log("只在构建的时候执行吗？", searchParams)
  return ({
      info: `测试一下在页面上获取数据,${searchParams}`

  })
}
```

1. 后者一般需要动态获取数据（如从数据库）并计算整合

### 获取数据(next.js 13以上）
获取数据的异步函数一般写在组件内或者拆分到公共的uitls工具文件夹中

#### 服务端
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744361812004-3a2d0e2e-01a5-4e07-a7da-8ea38c676944.png)

##### fetch
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744358569337-5e02524b-44cd-4c4f-86b6-33a6d63a34bb.png)

##### 直接查询数据库
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744358590820-c13fa267-45d1-4de7-bedf-14729df0e48b.png)

##### 动态路由获取参数（params和searchParams）
[https://nextjs.org/docs/app/building-your-application/data-fetching/fetching](https://nextjs.org/docs/app/building-your-application/data-fetching/fetching)

[https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes](https://nextjs.org/docs/app/building-your-application/routing/dynamic-routes)

```tsx
type Params = Promise<{ slug: string }>
type SearchParams = Promise<{ [key: string]: string | string[] | undefined }>
 
export async function generateMetadata(props: {
  params: Params
  searchParams: SearchParams
}) {
  const params = await props.params
  const searchParams = await props.searchParams
  const slug = params.slug
  const query = searchParams.query
}
 
export default async function Page(props: {
  params: Params
  searchParams: SearchParams
}) {
  const params = await props.params
  const searchParams = await props.searchParams
  const slug = params.slug
  const query = searchParams.query
}
```

###### params
###### searchParams


#### 客户端
##### 使用react中的use hook ：[https://zh-hans.react.dev/reference/react/use](https://zh-hans.react.dev/reference/react/use)
##### 第三方库，如<font style="color:rgb(23, 23, 23);"> </font>[SWR](https://swr.vercel.app/)<font style="color:rgb(23, 23, 23);"> or </font>[React Query](https://tanstack.com/query/latest)
### 用<form>来提交数据（不用js）
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744708402641-b4caec5b-c868-4e5d-9b73-e569d269f891.png)

[<form>：表单元素 - HTML（超文本标记语言） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Reference/Elements/form)

[form标签有哪些属性？【form标签5大属性用法】](https://www.itheima.com/news/20231017/103938.html)

1. ajax提交
2. 使用<form>提交 （基础的HTML功能，不用JS）--更简单，c端兼容性更好，性能更好

c端表单提交的数据格式：

```tsx
{
  'c1':'value1',  // fe_id: value
  'c2':'value2',
}
```

### API（GET、POST等项目内写的api）
#### API数据处理
[Routing: Route Handlers | Next.js](https://nextjs.org/docs/app/building-your-application/routing/route-handlers#request-and-response)

##### POST
- [x] 请求正文

```tsx
export async function POST(request: Request) {
  const res = await request.json()
  return Response.json({ res })
}
```

- [x] 请求主体 FormData ----<font style="color:rgb(23, 23, 23);background-color:rgb(247, 247, 247);">request.formData()</font>

```tsx
export async function POST(request: Request) {
  const formData = await request.formData()
  const name = formData.get('name')
  const email = formData.get('email')
  return Response.json({ name, email })
}
```

#### 重定向
[Routing: Redirecting | Next.js](https://nextjs.org/docs/app/building-your-application/routing/redirecting)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744779950196-f5c6b4bc-3261-4cf2-9395-0f404cd5920d.png)

- [x] redirect用在try catch中会跑出错误，在try catch中重定向要用NextResponse.redirect，注意要return

#### 错误处理
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1744703002733-dfbd5406-4236-4c29-ad88-ab9e8191ed9d.png)

## react性能优化
### 缓存数据，减少计算（可以，但不一定必要，视情况而定）
- [x] 用于缓存一些依赖项不咋变化的数据部分

#### useState传入函数
- [x] useState传入普通变量，每次组件更新都会执行
- [x] useState传入函数，只在组件渲染时执行一次
- [x] 适合数据结构复杂，计算成本高的场景

#### useMemo
- [x] 函数组件每次stat更新都会重新执行函数，useMemo可以缓存数据，不用每次执行函数都重新生成
- [x] 可用于计算量大的场景，缓存提高性能

#### useCallback
- [x] 和useMemo一样
- [x] 专门用于缓存函数

#### React.memo
- [x] state变化，组件会更新
- [x] 同时，子组件默认会“无脑”更新，无论props是否变化
- [x] 想要控制子组件更新，就要使用React.memo（把子组件用React.memo包一下）

### 优化代码体积（比较必要）
#### 分析代码体积：Analyzing-the-bundle-size
[Analyzing the Bundle Size | Create React App](https://create-react-app.dev/docs/analyzing-the-bundle-size)

#### 配置路由懒加载，拆分代码，优化代码体积----react中的lazy函数
- [x] 同时还拆分了响应的css

```tsx
const Edit = lazy(()=>
  import(/*webpackChunkName: "editPage"*/ '../pages/question/Edit'))
const Static = lazy(()=>
  import(/*webpackChunkName: "staticPage"*/ '../pages/question/Static'))
```

#### 抽离公共代码（主要是第三方库，不经常改变的），合理使用http缓存？
使用webpack工具----**<font style="color:#DF2A3F;">optimization.splitChunks</font>**

[SplitChunksPlugin | webpack](https://webpack.js.org/plugins/split-chunks-plugin/)

- [x] 在craco.config.js写webpackconfig

```tsx
module.exports = {
  webpack:{
    configure(webpackConfig){
      if(webpackConfig.mode==='production'){
        // 抽离公共代码，只在公共环境
        if(webpackConfig.optimization===null){
          webpackConfig.optimization={}
        }
        webpackConfig.optimization.splitChunks={
          chunks:'all',
          cacheGroups:{
            antd:{
              name:"antd-chunk",
              test:/antd/,
              priority:100
            },
            reactDom:{
              name:"reactDom-chunk",
              test:/react-dom/,
              priority:99,
            },
            vendors:{
              name:'vendors-chunk',
              test:/node_modules/,
              priority:98
            }
          }
        }
      }
      return webpackConfig
    }
  },
  devServer: {
    port: 8000,
    proxy: {
      '/api': 'http://localhost:3003',
    },
  },
};

```

## 测试
- [x] 单元测试
- [x] 自动化测试
- [x] 可视化测试
- [x] 注意
    1. 自动化测试非常重要（流程+工具，而非依赖人的主观）
    2. 前端，不是所有组件都适合测试

### 单元测试----jest
+ 测试用例
+ 断言		

[快速入门 · Jest中文文档 | Jest中文网](https://www.jestjs.cn/docs/getting-started)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1745068719246-c40f46db-f2f2-4e42-a8eb-bc26c3bdbbb6.png)

#### 测试文件的位置
1. 统一放在__test__下
2. 和源码文件放在一起，使用.test.ts	后缀
3. 建议后者，可读性好，不容易忘

#### 使用
- [x] test()
- [x] expect()
    - toBeInTheDocument()
    - toHaveTextContent()
    - not.toHaveTextContent()
    - toBeNull() / not.toBeNull()
    - toBe()
    - toBeTruthy() / toBeFalsy()
- [x] render()
- [x] screen
    - getByText()	
    - getByPlaceholderText()
    - getByDispaluValue() ----查找元素的当前值（value属性）

```tsx
import React from "react";
import Component from "./Component";
import { render,screen } from "@testing-library/react";


test("默认属性",()=>{
    render(<Component />)
    const title = screen.getByText('问卷标题')
    expect(title).toBeInTheDocument()
})

test("传入属性",()=>{
    render(<Component desc="单元测试"></Component>)
    const desc = screen.getByText('单元测试')
    expect(desc).toBeInTheDocument()
})

test('多行文字',()=>{
    render(<Component desc={"a\nb\nc"} />)
    const a = screen.getByText('a')
    expect(a).toBeInTheDocument()
    expect(a).toHaveTextContent('a')
    expect(a).not.toHaveTextContent('ab')
})


```

#### 自动化测试----添加precommit命令
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1745219430906-d56fd669-380e-468e-be7e-e5d467ca3918.png)

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1745219466569-12da5c0a-bc07-4801-a7d8-3040c05e951b.png)

- [x] commit自动执行，失败无法提交代码（不污染现有代码）
- [x] 避免各种“不小心”问题，不依赖人的主观
- [x] 要及时完善单元测试（配合代码走查 code review）

### 可视化测试----stroybook
[Install Storybook | Storybook docs](https://storybook.js.org/docs/get-started/install)

或者：

![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1745221802371-2ccd9540-d412-47d6-b3aa-191030432557.png)

##### 其他
- [x] ts中的typeof 返回的是变量的类型；js中的typeof 返回的是类型字符串

## 服务端开发----Nest.js
- [x] 开发服务端项目，代替mock
- [x] 学会Nestjs和Mogodb的使用
- [x] 对接B端和c端

### Nest.js入门和使用
[NestJS - A progressive Node.js framework](https://nestjs.com/)

#### 控制器 contorller
```tsx
nest g controller name
```

[Documentation | NestJS - A progressive Node.js framework](https://docs.nestjs.com/controllers)

处理传入的请求，并将响应发回客户端

<font style="color:rgb(37, 41, 51);">Controller通常是后端交互的入口。在Controller中定义了路由，并通过装饰器指明各种HTTP操作，如Get、Post、Put等</font>

总的来说Controller处理三个方面的事情：

+ <font style="color:rgb(37, 41, 51);">路由：Controller管理特定的路由请求，处理特定URL的Get、Post请求等</font>
+ <font style="color:rgb(37, 41, 51);">请求处理：Controller直接与HTTP层交互，负责接受请求、处理请求和返回响应</font>
+ <font style="color:rgb(37, 41, 51);">委托：Controller通常不直接执行业务逻辑，而是将业务逻辑的处理委托给后端的Service</font>

#### service
```tsx
nest g service name
```

Service在NestJS中通常被用来封装业务逻辑、数据处理、与数据库交互等操作。Service可以被多个Controller复用，减少重复代码，简化逻辑修改

总的来说Service负责三件事：

+ **<font style="color:#DF2A3F;">复用性</font>****：一个Service可以被多个Controller复用**
+ **分离关注点：将业务逻辑从Conroller中分离，让Controller专注于HTTP层的交互**
+ **独立性：Service可以使代码独立于网络层，进行单元测试**

#### 模块 module
```tsx
nest g module 模块名
```

<font style="color:rgb(37, 41, 51);">总的来说，Module主要做三件事：</font>

+ <font style="color:rgb(37, 41, 51);">封装：封装特定业务的Controller和Service</font>
+ <font style="color:rgb(37, 41, 51);">解耦：每一个模块负责一个业务，将大型业务分解成各个模块</font>
+ <font style="color:rgb(37, 41, 51);">依赖注入：Module定义了Provider的作用域，负责依赖注入的正确配置</font>

[https://juejin.cn/post/7363121082457620495](https://juejin.cn/post/7363121082457620495)

#### 路由----在controller文件中写
- [x] 添加全局路由前缀：<font style="background-color:#FBDE28;">app.setGlobalPrefix('api')</font>

##### 客户端请求参数获取（query、param、body...)
![](https://cdn.nlark.com/yuque/0/2025/png/2587809/1745308969471-49a085a3-1222-4d96-8d5e-1b3ce86d30cd.png)

```tsx

@Get(':id')
findOne(@Param() params: any): string {
  console.log(params.id);
  return `This action returns a #${params.id} cat`;
}

```

#### 统一路由返回格式
##### 拦截器
```tsx
nest g interceptor name
```

[Documentation | NestJS - A progressive Node.js framework](https://docs.nestjs.com/interceptors)

- [x] map:<font style="color:rgb(64, 64, 64);background-color:rgb(253, 253, 253);">操作符将响应对象赋值给</font>`<font style="color:rgb(40, 118, 210);">data</font>`<font style="color:rgb(64, 64, 64);background-color:rgb(253, 253, 253);">新创建对象的属性，并将新对象返回给客户端。</font>
- [x] 全局使用该拦截器

```tsx
app.useGlobalInterceptors(new TransformInterceptor())  
```

#### 过滤器
```tsx
nest g filter name
```

[Documentation | NestJS - A progressive Node.js framework](https://docs.nestjs.com/exception-filters)

- [x] 全局使用

```tsx
app.useGlobalFilters(new HttpExceptionFilter())  
```

### Mongodb安装、启动和数据操作
[https://www.mongodb.com/zh-cn/docs/manual/tutorial/install-mongodb-on-os-x/](https://www.mongodb.com/zh-cn/docs/manual/tutorial/install-mongodb-on-os-x/)

#### compass
官方推荐的用户图形界面

#### next连接mongdb
[https://docs.nestjs.com/techniques/mongodb](https://docs.nestjs.com/techniques/mongodb)

1. 安装mongoose
2. 在app.module.ts中导入
3. 抽离数据库路径，公共配置[https://docs.nestjs.com/techniques/configuration](https://docs.nestjs.com/techniques/configuration)
4. 创建schemas文件夹及相关数据库文件（在schema中写要存入数据库的参数）

```tsx
import { Prop, Schema, SchemaFactory } from '@nestjs/mongoose';
import { HydratedDocument } from 'mongoose';

export type UserDocument = HydratedDocument<User>;

@Schema({
  timestamps: true,
})
export class User {
  @Prop()
  username: string;

  @Prop()
  password: string;
}

export const UserSchema = SchemaFactory.createForClass(User);

```

5. 在响应的moudle文件中引入数据库
6. 在相应的service文件中注入schema，写数据处理逻辑函数
7. 在相应的controller文件中注入service，并使用service函数
8. 调用接口，完成



### 开发问卷、答卷、统计等功能
#### 常用操作
- [x] 代码实现：分页、模糊搜索

```tsx
// 查询问卷列表  分页  模糊搜索
async findQuestionList({keyword='',pageNo=1,pageSize=10}){
    const whereOpt:any = {} 
    if(keyword){
        const reg = new RegExp(keyword,"i")
        whereOpt.title={$regex:reg}
    }
    return (this.questionModel.find(whereOpt)).sort({_id:-1}).skip((pageNo-1)*10).limit(pageSize)
}
```

- [x] 复用service
1. 原service的module中导出该service
2. 现moudle中导入原module
3. 现service中导入原service，并使用原service的函数
- [x] 增加jwt验证
1. 安装jwt依赖
2. module引入jwtmodule，配置jwt信息（如自定义规则和过期时间）
3. service中注入jwtservice，并使用
4. 增加guard校验，解析token，并验证token的有效性
- [x] 重定向---- [https://docs.nestjs.com/controllers#redirection](https://docs.nestjs.com/controllers#redirection)
- [x] 登陆后，自动知晓身份，后续操作不需要传userId
    1. 登陆token校验，获取身份，存储身份信息中的userId到request中（在guard文件中写）
    2. 客户端发起请求，如创建操作，对应的controller从request中获取userId，添加到model save，数据库成功添加带有userId的数据！
- [x] 复制问卷----注意修改id，id不能重复

#### 常用api
+ findOne
+ toObject （获取原始数据 == vue中的toRaw())
+ new this.[moduleName]
+ .save
+ .find
+ .sort
+ .skip
+ .limit
+ .countDocuments
+ findById
+ findOneAndDelete
+ deleteMany

```tsx
this.questionModel.deleteMany({
    _id: { $in: idList },
    userId,
  });
```

#### 前后端联调
##### 配置允许跨域
# react和vue使用体验比较
### 响应式数据（数据）
### 感觉react中的hooks能更轻松的封装公共逻辑
比如说，在哪个页面调用了这个hooks，就能获得这个页面的数据，比如路由参数之类的，而vue需要先在页面上获取，然后传递过去？

### dom的书写方式
### 各种hooks Vs vue中的语法糖？
#### 比如useRequest，vue中有类似的功能函数吗？
#### 搜索列表，不直接和数据联动，而是通过改变url的参数，列表监控url的参数，获取数据；vue中好像不这么做？
#### useEffect和watchEffect、computed
- [x] useEffect必须写依赖 
- [x] watchEffect和computed可以自动监听函数中的变量变化

### 组件思维（语法侧重点/优缺点）
### 与typescript结合的方式和程度
### vuex和redux的比较（方式、思维）
### ant design组件库的使用




