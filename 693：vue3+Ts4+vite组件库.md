# TS基础知识
[基础知识.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1718534110536-4aea726d-91cd-46bb-a79b-b76682784314.pdf)

定义：融合了后端面向对象思想的超级版的javascript语言

### 环境搭建
1. npm init -y   初始化项目
2. npm install typescript 安装ts依赖
3. tsc --init  <font style="background-color:#FBDE28;">生成ts核心配置文件！！  tsconfig.json</font>

### 与js相比，ts的优势！！！ 
1. **<font style="color:#D22D8D;">编译时静态类型检测</font>**：函数或方法传参或变量赋值不匹配时，会出现编译错误，规避了开发期间的大量低级错误，省时省力。
2. **<font style="color:#D22D8D;">自动提示更清晰明确</font>**
3. **<font style="color:#D22D8D;">引入了泛型和一系列	TS特有的类型</font>**
4. **<font style="color:#D22D8D;">强大的d.ts声明文件</font>**：声明文件像一本书的目录一样，清晰直观展示了依赖库文件的接口，type类型，类，函数，变量等声明
5. **轻松编译成JS文件**：即使TS文件有错误，绝大多数情况也能编译出JS文件
6. **灵活性高**：尽管TS是一门强类型检查语言，但也提供了 <font style="color:#D22D8D;">any </font>类型和 <font style="color:#D22D8D;">as any </font>断言，提升了TS的灵活度

### 动态类型语言和静态类型语言的区别
+ 动态类型语言：在运行期间才去做数据类型检查的语言。不用给变量指定数据类型，该语言会在第一次复制给变量时，在内部将数据类型记录下来。
+ 静态类型语言：在写程序时需要声明变量的数据类型。

### 类型注解-----自己定义  
:type（定义某种类型的数据）

```javascript
let data:number = 3;
```

### 类型推导-----根据你的赋值，自动推导
```javascript
let data = 'jhdfwoihj'
```

### TS编译和编译优化
#### TS代码要编译成 js 才能被正确执行！
#### 批量将ts文件编译为指定文件夹的js文件
1. 修改**<font style="color:#D22D8D;">tsconfig.json</font>**中的“**<font style="color:#D22D8D;">outDir</font>**”和“**<font style="color:#D22D8D;">rootDir</font>**”
    1. 其中“outDir”是你想要编译输出存储js文件的路径
    2. “rootDir”是ts的文件地址
2. cd进入总文件目录，在终端中输入 “**<font style="color:#D22D8D;">tsc</font>**”，实现批量转换！
3. 一些命令

```javascript
// 指定输出文件的名称
tsc index.ts --outfile file-name.js
//  每当做了一个改动，typescript自动编译代码
tsc index.ts -w
```

## TS的常用24种类型
### 基本类型：
+ number
+ string
+ boolean
+ symbol
+ null
+ undefined

##### 注意 unknown 和 null 的细节
1. any, unknown, undefined 可以接受 **<font style="color:#7E45E8;">undefined </font>**为赋值
2. any，unknown，null 可以接受 **<font style="color:#7E45E8;">null</font>** 为赋值

```javascript
let data:unknown=undefined
```

#### 根类型
+ Object
+ { }

#### 对象类型
+ Array
+ object
+ function

#### 枚举
+ 关键字：**<font style="background-color:#FBDE28;">enum </font>**

##### 使用枚举的意义
1. 解决多次 if/switch判断中值得语义化问题
2. 解决使用常量带来的局限性
    1. 方法参数不能定义为具体类型，只能初级使用number、string基本类型代替，降低了代码的可读性和可维护性
3. 有默认值和可以自增值，节省编码时间
4. 语义更加清晰，可读性增强

##### 定义：用来存放一组固定的常量的序列 
##### 分类：数字枚举和字符串枚举
- [x] 数字枚举定义时，可只给第1项赋值，后面的项会按顺序+1

```javascript
enum numb{
    first=1,
    secrond,  //自动为2
    third,  // 3
}
```

- [x] 字符串枚举定义时必须给序列中的每一项都赋值

```javascript
enum strb{
    monday='monday',
    tuesday='tuesday',
    wensday='wensday'

}
```

##### 取值：数字枚举可以双重映射取值
##### 数字枚举：值取key & key取值
```javascript
numb['first']
numb.first
numb[1]
```

##### 字符串枚举：只能单向由key取值
```javascript
strb['monday']
strb.monday
```

#### 常量枚举---可以提升性能
一般的ts枚举被转为js后会转换成很多复杂的代码，而常量枚举会简单很多

```javascript
//常量枚举
const enum data {
    monday='pink',
    tuesday='green',
    wensday='yellow',
    thusday='blue',
    friday='red'
}
```

#### 其他特殊类型：
+ any
+ unknown
+ never
    - 什么场景never能被直接推导出来而不用定义？（ if 穷尽所有的预定义类型之后的else里可以看到提示，变成never ）
+ <font style="background-color:#F1A2AB;">void：</font><font style="color:rgb(31, 31, 31);"></font>**<font style="color:rgb(4, 12, 40);">表示没有返回值</font>**<font style="color:rgb(31, 31, 31);">。 当函数的返回值类型为void时，意味着该函数不返回任何值。 需要注意的是，void类型并不是指返回undefined的类型，而是指函数不返回任何值</font>
+ tuple
+ 可变元组

##### any和unknown的两点区别和应用场景
###### 相同点
any和unkown可以是任何类的**<font style="color:#DF2A3F;">父类</font>**，所以任何类型的变量都可以赋值给any类型或者unknown类型的变量

######  不同点
1. **<font style="color:#AE146E;">any也可以是任何类的子类，但unkown不可以，</font>**所以any类型的变量都可以赋值给其他类型的变量
2. <font style="color:#AE146E;">不能拿unknown类型的变量来获取任何属性和方法，但any类型的变量可以获取任意名称的属性和方法</font>

```javascript

// 会报错
function getData(data:unknown){
    console.log(data.name)
}
```

##### any比较典型的应用场景
1. 自定义守卫
2. 需要进行as any类型断言的场景

##### unknown一般用作函数参数
用来接受任意类型的变量实参，但在函数内部**<font style="color:#DF2A3F;">只用于再次传递或输出结果</font>**，不获取属性的场景

#### 合成类型
##### 联合类型-------   | 
是一个可以被分配到多个类型的变量

```javascript
const data:number | string = 3
```

##### 交叉类型（<font style="color:rgb(10, 10, 35);">将多种类型组合为一种类型</font>）-------   & 
可以用关键词：type来声明变量

```javascript
type obj1 = {name:string}
type obj2= {age:number}
let instance1:obj1&obj2={name:'yihuik',age:18}
```

#### 字面量数据类型
```javascript
type num=1|2|3
let n:num=3   //此时如果n为1、2、3之外的数字就会报错！
```

## 接口  --  关键词： <font style="color:#DF2A3F;">interface </font><font style="color:#AE146E;"> 定义的所有内容，只能申明，不能实际定义值</font>
只能在ts中用于静态类型检查，不能被转换到js中去，因为js是没有的

##### 定义：用于定义对象类型的一种类型
```javascript
interface Product{
    monday:numb；     //   属性
    tuesdsay:string；
    wensdat():void； 
}
```

##### 接口具有继承性
```javascript
interface P1 extends Product{
    friday:string
}
```

##### 应用场景
1. 一些第三方包或者框架底层源码中有大量的接口类型

```javascript
interface Product{
    monday:number;
    tuesdsay:string;
    wensdat():void
}

let p:Product={
    monday:11,
    tuesdsay:'jiwehf',
    wensdat(): void{
        console.log('生效')
    }
}
```

2. 提供方法的对象类型的参数时使用

```javascript
function getProduct(p:Product){
    console.log(p)
}
getProduct(p)
```

3. 为多个同类别的**<font style="color:#AE146E;background-color:#FBDE28;">类</font>**提供统一的方法和属性声明-----**<font style="color:#AE146E;background-color:#FBDE28;">implement</font>**

```javascript
class P2 implements Product{
    monday= 11
    tuesdsay='ehjwifi'
    wensdat(): void {
        throw new Error("Method not implemented.")
    }
}
```

#### <font style="color:#DF2A3F;">可索引签名-</font>----- <font style="background-color:#FBDE28;">[x:string]:any  </font>  只能是string、number或者symbol类型
###### 当接口中可能存在未知的属性时（不知道属性名，不知道还有几个），<font style="color:#DF2A3F;">写上可索引签名</font>可以在变量中无限定义符合条件的变量
```javascript
interface instance{
    name:string,
    age:number,
    addr:string,
    [x:string]:any
}

const ming:instance={
    name:'ming',
    age:18,
    addr:' shanghai',
    gender:'male',
    100:345,
    [Symbol('what')]:1000
}
```

###### 在 [x:string]:any 写法下，属性名和值都可以是很多种类型，如上图的字符串、数字和symbol，也可以写成其他，比如 <font style="background-color:#FBDE28;">[x:number]:any</font> 或者 <font style="background-color:#FBDE28;">[x:symbol]:any</font> 等。
###### 但<font style="color:#DF2A3F;">可索引签名的类型值必须兼容原接口中定义的所有属性的类型</font>！！！
```javascript
interface instance{
    name:string,
    age:number,
    addr:string,
    [x:string]:string | number
}
```

#### keyof 相当于拿出接口中的所有的属性
```javascript
interface Product{
    monday:number;
    tuesdsay:string;
    wensday():void
}

type PKeys = keyof Product
let pKeys:PKeys='monday'   //可选所有项  'monday' | 'tuesdsay' | 'wensday'
```

#### 可选参数-------在变量后添加 ? 
函数调用可选是否传入参数

```javascript
function fn(data?:string){
    // data!.toString()  忽略data为undefined
    if(data) data.toString()
}

fn()
```

#### <font style="color:#601BDE;">变量不赋值，打印不报错的方法------类型上拼一个undefined</font>
```javascript
let srt:string|undefined
console.log(srt)
```

#### 只读属性不可修改值：readonly
```javascript
// 接口
interface Person{
  name:string,
    // 可选属性
    age?:number
  // 只读属性
  readonly id:number
}

const liao:Person={
  name:'liao',
  id:18
  // age不写不会报错
}
// id只读，不能修改
liao.id = 4
```



#### 错误取值
1. ~~**<font style="color:#DF2A3F;">变量不能作为某个对象的key来取值，常量才行  </font>**~~**<font style="color:#DF2A3F;">经过测试，可以哇？？！</font>**

```javascript
let obj={username:'ming',age:18}

// let username='username'
const username='username'
let test = obj[username]
```

2. 当定义了某个变量的类型为object时，取值时会先在object中找key，没找到就会报错！！

```javascript
let obj:object={username:'ming',age:18}

let test = obj[username]
```

## 类型断言--as
<font style="color:rgb(44, 62, 80);">告诉编译器你比它更了解这个类型，并且它不应该再发出错误。</font>

**<font style="color:#DF2A3F;">但如果把类型断言成，联合类型中不存在的类型，会报错</font>**

```javascript
function getLength(input:string|number):number{
    // const str = input
    const str = input as string
    //如果不用as断言，无法调用length属性，会报错
    console.log(str.length)
}
```

#### 数组和数组元素同时设置为<font style="color:#DF2A3F;">只读</font>-------- <font style="color:#DF2A3F;">as const</font>
```javascript
const arr = [10,45,14,52,78] as const
```

#### type guard----通过<font style="color:#DF2A3F;">type of</font>条件来确认变量类型
```javascript
function getLength2(input:string|number):number{
    if(typeof input ==='string'){
        return input.length
    }else{
        return 0
    }
}
```

#### 非空断言操作符：！
在变量或者表达式后面加 ！ 表示不会为null或者undefined

[https://blog.csdn.net/weixin_43599321/article/details/130767293](https://blog.csdn.net/weixin_43599321/article/details/130767293)

```javascript
curNode.next = curNode.next!.next;
const a:number = b!
const element = document.querySelector('#my')
```

## 函数
#### 函数类型：定义了参数，参数的类型以及函数的<font style="color:#DF2A3F;">返回类型</font>
```javascript
function fn(name:string,age:number):number{
    return 3
} // 最后的:number定义的是返回类型
```

```javascript
const fn = function(name:string,age:number,z?:number):number
{
    return 3
} //可选函数必须写在最后面
```

```javascript
const fun:(name:string,age:number)=>number=function(name,age){
    return 3
}
```

#### 定义一个<font style="color:#DF2A3F;">函数类型</font>的变量
##### type声明函数
```javascript
type FunType =(name:string,age:number)=>number

const fun:FunType=function(name,age){
    return 3
}
```

##### interface声明函数
```javascript
// 声明了一个输入为number，输出也为number 的函数 test
interface test{
    (x:number,y:number,z?:number):number
}
```

#### rest参数  --- -类型可以是任意类型的数组，或者any
```javascript
type FunType =(name:string,age:number,...rest:any)=>number

const fun:FunType=function(name,age,fd,efw,erwew,gre,greg){
    return 3
}
```

```javascript
type FunType =(name:string,age:number,...rest:string[])=>number

const fun:FunType=function(name,age){
    return 3
}

fun('ming',12,'fewkof','234','djfiewf')
```

#### 函数类型解构
```javascript
type virableType={name:string,age:number,gender:string,area:string}

const fun=function({name,age}:virableType){
    return 3
}
```

### interface和type的区别
#### 定义类型范围不同
+ interface只能定义**<font style="color:#7E45E8;">对象类型</font>**或接口当名字的**<font style="color:#DF2A3F;">函数类型</font>**

```javascript
interface add{
  (x:number, y:number): number
}
```

+ type 可以定义任何类型，包括基础类型、联合类型、交叉类型、元组

#### 接口可以继承一个、多个接口或者类，也可以继承type，但type类型没有继承功能
但一般接口继承类和type的应用场景很少见

#### 用type交叉类型 <font style="color:#7E45E8;">&</font> 可以让类型中的成员合并成一个新 的type类型，但接口不同交叉合并
## 元组
#### 定义
1. 在定义时每个元素的类型都确定
2. 元素值的数据类型必须是当前元素定义的类型
3. 元素的个数和顺序必须和定义时个数相同

```javascript
const test:[string,number,number]=['dfewr',23,32]
```

#### 可变元组------用rest实现
```javascript
const test:[string,number,number,...any[]]=['dfewr',23,32,45,78,'edfjo','213324']
```

##### 取值
1. 像数组一样，通过索引取值

```javascript
test[4]
```

2. 通过解构取值

```javascript
const [name,age,...rest]=test
```

#### 可变元组标签-----给类型项命名，增强可读性
```javascript
const test:[name:string,age:number,phone:number,...rest:any[]]=['dfewr',23,32,45,78,'edfjo','213324']

const [name,age,...rest]:[name_:string,age_:number,...rest:any[]]=test
```

#### 可以使用数组中的一些方法，比如push，但是只能push，元组中定义好的类型
## 泛型---<占位名>
**允许在定义函数、类、接口等时，不预先指定具体的类型，而在使用的时候再指定类型**

[https://juejin.cn/post/6844904184894980104#heading-3](https://juejin.cn/post/6844904184894980104#heading-3)

```javascript
// 泛型---变量占位符
 function thusday<T,U>(arg1:T,arg2:U):[U,T]{
    return [arg2,arg1]
 }
```

#### 约束泛型---<font style="color:rgb(37, 41, 51);">限制每个类型变量接受的类型数量</font>
##### 显示约束
```javascript
// 显式约束----此处约束为数组
function notHappy<T>(arg:T[]):T[]{
    return arg
}
```

##### 隐式约束----extends
```javascript
//  隐式约束----extends
interface white {
    // color:string,
    length:number
}

function mood<T extends white>(arg:T):T{
    console.log(arg.length)
    return arg
}

// 确保输入的变量上有length类型就不会报错，输入number会报错
const red = mood('red')
const none = mood([1,2,3,4])
const obj = mood({length:10,width:30})
```

#### 泛型在类和接口中的应用
##### 类
```javascript
// 类中的泛型
class Test<T>{
    private data:T[]=[]
    push(item:T){
        return this.data.push(item)
    }
    pop(){
        return this.data.shift()
    }
}
// 保证了类型的一致性，具有更高的包容性
const queue = new Test()
queue.push(1)
queue.push('1')
const queue2 = new Test<number>
```

##### 接口
```javascript
// 接口
interface green<T,U>{
    color:T,
    alpha:U
}

const pink:green<string,number>={color:'2341',alpha:12}

let arr:number[]=[1,2,3]
let arr2:Array<number>=[1,2,3,4]
```

### 泛型函数（omit、pick、partial....)
[https://juejin.cn/post/7146214190842282015](https://juejin.cn/post/7146214190842282015)

[https://juejin.cn/post/7109403211127062558#heading-3](https://juejin.cn/post/7109403211127062558#heading-3)

- [x] 获取复杂对象中某个属性的类型定义用  ['属性名字']

```javascript
  stepItems: {
    type: Array as PropType<Pick<StepsProps, 'items'>['items']>,
    default: () => [],
  },
```

### 类型别名
[https://juejin.cn/post/6844903753431138311](https://juejin.cn/post/6844903753431138311)

## 类，静态属性，何时用静态属性？
####  类
```javascript
class People{
    name:string;
    age:number;
    addr:string;
    gender!:string  //这种写法可以不赋初值
    constructor(_name:string,_age:number,_addr:string){
        this.name=_name
        this.age=_age
        this.addr=_addr

    }
}

const ming = new People('ming',18,'hduw')
```

#### 静态成员------关键词 static   静态属性+静态方法
静态成员只有类本身才能拥有并使用，任何实例都不能继承

```javascript
class People{
    name:string;
    age:number;
    addr:string;
    static gender:string='female'    //静态属性
    constructor(_name:string,_age:number,_addr:string){
        this.name=_name
        this.age=_age
        this.addr=_addr
    }
}

const ming = new People('ming',18,'hduw')
console.log(People.gender)
```

#### 单例模式
让程序中有且只有一个实例，保证在任何时候获取类中的信息时，都是拿的同一个对象的信息，保证状态的一致性

[TS 设计模式03 - 单例模式](https://www.jianshu.com/p/1a67aee49cec)

##### 立即创建单件模式（饿汉式） -----<font style="color:rgb(64, 64, 64);">在该类创建的时候就进行了实例化，且只实例化一次</font>
后面再被实例化也不会重复执行！！

- [x] private + static

```javascript
class People{
    name:string
    static defaultName = new People('ming')
    private constructor(_name:string){
        console.log('只运行一次')
        this.name=_name
    }
    formatName(){
        console.log('formatName')
    }
}
const Hong = People.defaultName
const Yuan = People.defaultName
console.log(Hong===Yuan)   //true
```

##### 懒汉模式------在真正调用时，类才真正被实例化
```javascript
class People{
    name:string
    static instance:People
    private constructor(_name:string){
        console.log('只运行一次')
        this.name=_name
    }
    static getInstance(){
        if(!People.instance){
            People.instance = new People('Ming')
        }else{
            return this.instance
        }
    }
}
const Hong = People.getInstance()
const Ping = People.getInstance()
```

#### get和set属性，和es6差不多，设置存值函数和取值函数，给变量赋值
- [x] set要通过外部赋值，才会自动调用！

```javascript
class People{
    firstname:string;
    age:number;
    _lastname!:string
     constructor(_firstname:string,_age:number){
        this.firstname=_firstname
        this.age=_age
    }
    set lastname(val:string){
        this._lastname=val
    }
    get lastname(){
        return this._lastname
    }
}

const Ming=new People('ming',18)
// 要在外部给值，会自动调用set，执行逻辑
Ming.lastname='Liao'
// 自动调用get，获取
console.log(Ming.lastname)
```

## 声明文件  .d.ts文件
- [x]  声明文件本身，为实际的业务逻辑提供类型
- [x] 不会有任何的实际逻辑代码，只有类型声明
- [x] interface function类型或者class等的类型声明
- [x] 在typescript.org/dt/searc安装不同第三方库的声明文件

### declare----后面加具体的名称来声明变量的类型
```javascript
declare function axios(url:string):string
declare const one:number
```

### 第三方库的声明文件
- [x] 大部分第三方库在安装时会自动安装申明文件 

## 内置类型
[https://juejin.cn/post/7091292968174223368](https://juejin.cn/post/7091292968174223368)

功能类型：

[https://www.typescriptlang.org/docs/handbook/utility-types.html](https://www.typescriptlang.org/docs/handbook/utility-types.html)

## 配置文件
[TypeScript配置、tsconfig.json配置文件，TypeScript使用详解_typescript配置文件详解-CSDN博客](https://blog.csdn.net/muguli2008/article/details/122246623)

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1717922053936-f125cd8e-6e48-4ef6-bb48-d7ef99b4a2fc.png)

# vue基础知识
## 使用vite创建项目/文件结构/插件
官网：[https://cn.vitejs.dev/](https://cn.vitejs.dev/)

### 使用vite创建项目
#### vite的特点
+ 启动快
+ HMR支持
+ 默认支持TS、JSX、CSS等
+ 多种打包模式支持
+ 通用插件
+ 底层API支持TS
+ 不仅仅限于VUE3，是个通用脚手架工具
+ [https://cn.vitejs.dev/guide/why](https://cn.vitejs.dev/guide/why)

#### 为什么选择vite而不是vue-cli
官方工具链： [https://cn.vuejs.org/guide/scaling-up/tooling.html](https://cn.vuejs.org/guide/scaling-up/tooling.html)

+ vite是vue3官方推荐的脚手架
+ vue cli处于维护模式
+ vite比vue cli快很多

#### 创建vite项目   [https://cn.vitejs.dev/guide/](https://cn.vitejs.dev/guide/)
1. npm create vite@latest
2. 附加命令指定创建，不同的npm版本，命令会有不同
3. 还可以通过yarn 、 pnpm来创建

### 项目文件结构及推荐的插件
![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1718461844365-c7d95480-ce37-4104-af90-7a039d582d83.png)

分别对应该项目在浏览器环境和node环境的运行配置

#### vue 浏览器插件
![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1718462816092-184e2e4b-04c2-4b78-bee4-cca6d5645033.png)

## 配置开发环境（eslint)----eslint用来检测编写的代码是否符合规范
[https://juejin.cn/post/7217340231752958009#heading-6](https://juejin.cn/post/7217340231752958009#heading-6)

### **eslint简介和初步使用------规范代码格式**
[使用 Eslint.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1718534082723-ec9e9cb4-950d-45d7-bbe8-f18c3c3bb3d8.pdf)

**eslint是一个开源的javascript的linting工具，使用espree将javascript代码解析成抽象语法书（ast），然后通过AST来分析我们的代码**

**没有规范代码格式可能会出现的问题**

+ **代码难以读懂**
+ **代码提交时会有很多格式问题的修改，造成不必要的时间消耗**

#### **使用**
1. **安装： npm install eslint --save-dev**
2. **项目eslint初始化：npm init @eslint/config 或者 npx eslint --init**

此时会自动安装依赖：@eslint/js, typescript-eslint, eslint-plugin-vue

3. **eslint 检查：配置rules，然后终端输入 npx eslint 文件路径**
4. ![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1718533929387-5c26bc4d-28d3-4246-8070-814801b32c39.png)
5. 使用eslint推荐规则合集  https://eslint.org/docs/latest/rules

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1718534703886-425eaa56-4e78-4c90-9dcf-1911a8c7db5d.png)

### eslint配合vite、vue、typscript实现更多规则校验
#### vite添加eslint插件
[Vite项目中eslint的简单配置1.创建一个vite项目 使用包管理工具创建一个vite项目。 2.安装eslint - 掘金](https://juejin.cn/post/7414157132973981732#heading-11)

## 学习各类基础知识（vue3.2）
### 响应式 ref/reactive/computed/watch
[响应式基础.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1718546999654-d7aefcc7-57cf-4276-8cc8-c0afb8f0fc2d.pdf)

```javascript
const user1:Person = reactive({
    name:'1',
    age:2
})
const botton1 = computed<boolean>({
  
  get:()=>{
    return false
  },
  set:()=>{
    className.value = 2
  }}
```

- [x] watch监听**<font style="color:#DF2A3F;">对象中的某个属性值</font>**，不能直接写，而是要**<font style="color:#DF2A3F;">通过箭头函数返回这个属性值</font>**的方式写。

```javascript
watch(
  () => user1.name,
  (newValue, oldValue) => {
    console.log(newValue, oldValue);
  }
);
```

- [x] flash:'post' ，修改watch在dom更新之后被调用。默认值是pre，watch在dom更新之前被调用

### 生命周期
### 组件 属性/事件
#### 组件基础
- [x] defineComponent的用法：属性props

```vue
export default defineComponent({
    name:'Test',
    props:{
        name:{
            type:String,
            // req uired:true
        },
        today:{
            type:String,
            required:true,
            default:'saturday'
        },
        day:{
            type:Number,

        },
        LYH:{
            // 使用PropType,以及接口来标注复杂类型
            type:Object as PropType<Person>
        }

    },
    setup(props){
        const count = inject('count')
        const LYH = props.LYH
        return{count}
    }
})
```

- [x] 父子组件传值，非字符串类型的值，视为动态属性，副组件要用v-bind进行传值
- [x] PropType标注复杂类型

#### 组件的自定义事件
- [x] defineComponet使用emit属性，不能使用defineEmit（只能在setup语法糖里使用）
- [x] 在setup的第二个参数里获得emit，一般把这个参数命名为ctx（contex）

```vue
export default defineComponent({
    name:'Test',
    props:{
        LYH:{
            // 使用PropType,以及接口来标注复杂类型
            type:Object as PropType<Person>
        }

    },
    emits:['changeColor'],
    setup(props,ctx){
        const count = inject('count')
        function handleChangeColor(){
            ctx.emit('changeColor','rgb(45,221,89)')
        }
        return{count,handleChangeColor}
    }
})
```

#### 组合式函数（compositon API）
### hooks函数
把一些重复使用的函数抽象出来，放到一个独立的ts文件中，以实现重复使用

### setup语法糖--vue3.2以上的版本才支持
是composition API的语法糖

优点：

+ 更少的样板内容，更简洁的代码
+ 能够使用纯Typescirpt申明props和抛出事件
+ 更好的运行时性能
+ 更好的IDE类型推断性能

#### 在defineProps和defineEmits上使用Ts语法
1.  **<font style="color:#601BDE;">defineProps</font>**

```vue
const props = withDefaults(defineProps<{LYH?:Person}>(),{
    LYH:()=>({name:'LYH',age:26,money:'0'})
})
```

- [x] 使用泛型约束变量类型
- [x] 使用withDefaults函数给变量约定初始值
- [x] 初始值如果是对象类型的，要用函数的方式返回；基本类型可以直接返回
2. **<font style="color:#601BDE;">defineEmits</font>**                                          

```vue
interface IEvent{
    (e:'changeColor',rgb:string):void
}

const emits = defineEmits<IEvent>()
```

### 依赖注入  provide / inject
#### 基础使用
提供一种在组件之间共享参数的方法，而不必通过组件树的每个层级显示地传递props，目的是为了共享那些被认为对于一个组件树而言是“全局”的数据

#### 父组件
```vue
provide('count',1)
```

#### 子组件
```vue
const count = inject("count");
```

- [x] 传递的变量可以是ref或者reactive类型的
- [x] 可以通过定义变量名字为symble类型，来避免变量名重复的问题

```vue
export const keyOne = Symbol();
```

#### 和TS结合
- [x]  使用vue中的InjectionKey函数

```vue
import { InjectionKey } from "vue";
export const keyOne = Symbol() as InjectionKey<string>;
  
```

## 介绍vue3.3（2023/5/11）升级的内容
[Vue3.3 升级内容.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1720963263907-8f7960fb-abe7-4081-877b-e504289841b0.pdf)

- [x]  支持类型导入和复杂类型(defineProps）
- [x] defineEmits使用ts语法的新写法

```vue
const emits = defineEmits<{ changeColor: [color: string] }>();
```

- [x] defineSlot设置slots类型，不需要引用，可以直接写
- [x] defineOptions在setup语法糖中代替defineComponent

[https://juejin.cn/post/7374595069745201178](https://juejin.cn/post/7374595069745201178)

# Button组件
## 任务
### 需求分析（可以参考element UI、或者ant之类的UI组件库，打造属于自己的）
**<font style="color:#601BDE;">Button组件大部分关注样式，没有交互</font>**

根据分析可以得到具体的属性列表：

+ type：不同的样式（Default、Primay、Danger、Info、Success、Warning）
+ plain：样式的不同展现模式boolean
+ round：圆角boolean
+ circle：圆形按钮，适合图标boolean
+ size：不同大小（small、normal、large）
+ disabled：禁用 boolean
+ 图标：TODO---后面再添加
+ loading：TODO---后面再添加

#### Button组件的本质
```vue
//本质是class名称的组合

class=“vk-button-primary vk-button-large is-”plain 
```

### 初始化项目
#### create-vue
[Vue.js](https://cn.vuejs.org/guide/typescript/overview.html)

[GitHub - vuejs/create-vue: 🛠️ The recommended way to start a Vite-powered Vue project](https://github.com/vuejs/create-vue)

使用

```vue
npm create vue@3
```



### 确定项目文件结构
确定功能

从简单入手，一开始文件结构不要太复杂

#### defineOptions----vue3.3的新特性
用于定义声明组件选项，比如name

[Vue.js](https://cn.vuejs.org/api/sfc-script-setup.html#defineoptions)

#### defineModle---vue3.4的新特性
用于在子组件中定义双向绑定的变量，父组件通过v-model使用

[Vue.js](https://cn.vuejs.org/api/sfc-script-setup.html#definemodel)



### 规范基础写法
#### <font style="color:#DF2A3F;">要兼容button的原生属性---一个组件的重要考量因素</font>
[<button> - HTML（超文本标记语言） | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/button)

#### defineExpose---显式的指定要暴露出去的属性
在vue3 的setup语法糖中使用defineExpose来指定向父组件暴露的属性

button这里是需要向外暴露组件实例---一个组件的重要考量因素

[Vue.js](https://cn.vuejs.org/api/sfc-script-setup.html#defineexpose)





### 样式解决方案以及色彩系统
[css.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1724576740560-7fcfba0e-930f-4383-a6b7-f6c9cd96b41c.pdf)

#### css解决方案
[谈谈 CSS 预处理器 | HZFE - 剑指前端 Offer](https://febook.hzfe.org/awesome-interview/book2/css-preprocessor)

#### <font style="color:#DF2A3F;">postcss</font>
+ 实际上，PostCSS 的主要功能只有两个：
+ 第一个就是前面提到的把 CSS 解析成 JavaScript 可以操作的 AST，
+ 第二个就是调用插件来处理 AST 并得到结果。

因此，不能简单的把 PostCSS 归类成 CSS 预处理或后处理工具。PostCSS 所能执行的任务非常多，同时涵盖了传统意义上的预处理和后处理。

[ArchGrid - 架构知识网格 - PostCSS使用速记](https://archgrid.xyz/posts/frontend/css/postcss-usage/)

##### 使用
- [x] vite本身支持，无需安装
- [x] 在项目根目录中手动创建文件 postcss.config.jcs
- [x] 在该文件中手动配置需要使用的插件

```vue
/* eslint-env node */
// 添加注释，修改node现在的环境
// 在该文件中配置需要使用的postcss插件
module.export = {
  plugins: [
    require('postcss-nested'),
    require('postcss-each')({
      plugins: { 
        beforeEach: [
          require('postcss-for'), 
          require('postcss-color-mix')] 
    }
    })
  ]
}
// 在each遍历之前，先处理for和color-mix才能正确解析出mix的颜色变量
```

##### 插件
[PostCSS插件以及其作用_postcss-scss-CSDN博客](https://blog.csdn.net/dongshuaiqi/article/details/131128703)

+ 原子css

[原子化CSS-Tailwind CSS的简介和使用-CSDN博客](https://blog.csdn.net/a20065259/article/details/130769375)

#### reset css---normalize.css（目前最常用）
作用：

+ <font style="color:rgb(51, 51, 51);">保护有用的浏览器默认样式而不是完全去掉它们</font>
+ <font style="color:rgb(51, 51, 51);">一般化的样式：为大部分HTML元素提供</font>
+ <font style="color:rgb(51, 51, 51);">修复浏览器自身的bug并保证各浏览器的一致性</font>
+ <font style="color:rgb(51, 51, 51);">优化CSS可用性：用一些小技巧</font>
+ <font style="color:rgb(51, 51, 51);">解释代码：用注释和详细的文档来</font>

![](https://cdn.nlark.com/yuque/0/2024/webp/2587809/1724576915642-8cb56da5-d767-4757-b93f-39d7b15f4808.webp)

[来，让我们谈一谈 Normalize.css | 咀嚼之味](https://jerryzou.com/posts/aboutNormalizeCss/)

- [x] <font style="color:rgb(76, 73, 72);">使用</font>----在vue项目中的<font style="color:rgb(76, 73, 72);">main.js 中引入</font>：<font style="color:rgb(76, 73, 72);">import’normalize.css/normalize.css’</font>

#### postcss each 插件
<font style="color:rgb(51, 51, 51);">过使用插件来实现。其中一个常用的插件是postcss-each</font>

[PostCSS-每个循环遍历列表_For循环遍历列表_循环遍历元组列表并解包每个元组的元素 - 腾讯云开发者社区 - 腾讯云](https://cloud.tencent.com/developer/information/PostCSS-%E6%AF%8F%E4%B8%AA%E5%BE%AA%E7%8E%AF%E9%81%8D%E5%8E%86%E5%88%97%E8%A1%A8)

#### <font style="color:rgb(51, 51, 51);">postcss-for 、postcss-color-mix、postcss-each-variables插件</font>
像使用js语法一样，来写css变量

```vue
 @each $val, $color in var(--colors) {
    --vk-color-$(val): $(color);
    @for $i from 3 to 9 by 2 {
      --vk-color-$(val)-light-$(i): mix(#fff, $(color), .$(i))
    }
    --vk-color-$(val)-light-8: mix(#fff, $(color), .8);
    --vk-color-$(val)-dark-2: mix(#000, $(color), .2);
  }
```

[GitHub - awcross/postcss-each-variables: PostCSS plugin enabling variable mapping for each](https://github.com/awcross/postcss-each-variables)

## 总结
[总结.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1724601174290-85a6e7a0-ef97-4757-857e-4de6ca02b2ed.pdf)

# collapse组件
### BEM命名（block、element、modifier）
[什么是CSS BEM命名规范？BEM命名规范的总结（详细） - 30Curry - 博客园](https://www.cnblogs.com/stephensurry/p/14276413.html)

### 组件支持v-model
[Vue.js](https://cn.vuejs.org/guide/components/v-model)

#### 底层机制
+ 一个名为modelValue的prop，本地ref的值与其同步
+ 一个名为 update:modelValue的事件，当本地ref的值发生变更时触发

### Transition 
**<font style="color:#DF2A3F;">vue内置组件，</font>****用于为元素或组件制作基于状态变化的动画和过渡**

[Vue.js](https://cn.vuejs.org/guide/built-ins/transition.html)

#### [@keyframe](undefined/keyframe)的使用
[css 中 keyframes 的使用_css keyframes-CSDN博客](https://blog.csdn.net/qq_42816270/article/details/128651997)

# icon组件
### $attrs 透传属性--没有被组件申明的属性或者事件
[Vue.js](https://cn.vuejs.org/guide/components/attrs)

# 组件测试
[总结2.pdf](https://www.yuque.com/attachments/yuque/0/2024/pdf/2587809/1728803035398-f903fa0b-124c-42db-a7d9-2c1540b88a99.pdf)

![](https://cdn.nlark.com/yuque/0/2024/png/2587809/1728803010870-c4f523ae-e2a7-4e06-ad26-910ddc1bba11.png)



