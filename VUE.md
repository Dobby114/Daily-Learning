## class1------vue语法初探
#### <script src="https://unpkg.com/vue@next"></script>
#### Vue.createApp（）--创建vue实例
```javascript
    // // 表示创建一个vue的实例
     Vue.createApp({
       data() {
         return {
           content: "hellow world",
         };
       },
       //   页面加载完成后自动执行！！
        mounted() {
          setInterval(() => {
            // 箭头函数没有自己的this，这个情况下，this指的是creatAPP?
            this.content += 1;
          }, 1000);
          console.log("too slow");
        },
      // 模板，其内容就是要展示的内容
     // template: "<div> hellow world</div>",
       //   表示div里面的内容是content
       //   {{}}vue中，里面的内容表示是一个变量或者表达式---{{}}叫做差值表达式！
     //   可以直接改变DOM元素的内容了，而不需要显示的DOM操作
       methods: {
         handleBtnClick() {
          // 打撒、反向再组合
           this.content = this.content.split("").reverse().join("");
          // alert("hello world");
         },
      },
      template:
        // 直接添加一个button组件，并且用vue绑定了一个click时间：v-on表示要绑定时间，
        //click表示绑定click事件，后面的是处理函数，这个处理函数要写在methods里！！
       "<div> {{content}} <button v-on:click='handleBtnClick'>反转</button></div>",
     // 在id为root的组件上使用
    }).mount("#root");
```

#####     createApp 表示创建一个 Vue 应用, 存储到 app 变量中
#####     传入的参数表示，这个应用最外层的组件，应该如何展示
#####     method里面的方法里面的this统一指向vue实例！！里面的方法不要用箭头函数来定义，这样会导致箭头函数里的this指向最外层的window
#####     MVVM 设计模式，M -> Model 数据， V -> View 视图， VM -> ViewModel 视图数据连接层
##### {{}} 插值表达式
v-啥的都叫做指令

#### v-on:click='handleBtnClick'--事件绑定--也可以直接简写为@符号
绑定事件的处理方法一定要写在methods里！否则不生效

```javascript
methods:{
  handleBtnClick(){}
}
template: "<div @click='handleBtnClick'>{{message}}</div>"
```

#### v-if='show'--是否存在--通过show变量是否为true来决定某个标签是否存在，当为false时是通过直接<font style="color:#DF2A3F;">移除DOM元素</font>来实现
```javascript
data(){show:true},
template: "<div v-if="show">{{message}}</div>"
```

#### v-for --数据循环 v-for='(item,index) of list
#### v-model--数据绑定（标签的值）v-model='inputValue'---这是双向绑定！
#### v-bind--属性值与变量绑定（v-bind:title='inputValue'）和组件变量绑定v-bind:list='list'-----简写：去掉v-bind，直接写  <font style="color:#DF2A3F;">:title='inputValue'</font>
```javascript
<button v-on:click='handleBtnClick' v-bind:title='inputValue'>增加</button>
```

```javascript
<todo-list v-bind:list='list'/>
```

### 组件化
#### app.component（）----props接受参数
```javascript
    app.component("todo-list", {
      // 通过props接受绑定的参数“list”
      // 接收多个参数props: ["list",'index']
      props: ["list"],
      template: `<li v-for='(item,index) of list'> {{item}}---{{index}}</li>`,
    });
```

#### app.mount("#root");
```html
// 最后才将这个vue实例挂载到html页面中
    app.mount("#root");
```

#### 根组件里直接用组件
```html
template: `<div>
        <input v-model="inputValue" />
        <button v-on:click='handleBtnClick' v-bind:title='inputValue'>增加</button>
        <ul>
          <todo-list v-bind:list='list'/>
        </ul>
      </div>`,
```

#### 根组件--const vm = app.mount("#root")
##### vm 代表的就是 Vue 应用的根组件---最基本的组件，其他的组件都用在它里面
##### <font style="color:#DF2A3F;">vm.$data.message</font>----就获得了里面的message的值，通过操作vm.$data.message='yes'可以改变这个值！！
##### 可以通过vm进其他操作
## class2------vue的基础语法
### 生命周期函数--在某一时刻会自动执行的函数（钩子函数） --8个
 

![生命周期图](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677468767754-c4458ba5-633c-4b7b-99ec-d9d5459a8ea3.png)

#### 组件的生命周期：
组件从创建到销毁的过程，就是组件的生命周期。分为3个阶段，分别是：创建、更新、销毁

#### 组件的生命周期函数：
指的是组件创建 - 运行--销毁的过程中，<font style="color:#DF2A3F;">自动按次序执行的内置函数</font>，叫做组件的生命周期函数。

#### 
#### beforeCreate(){}-----在实例生成之前会自动执行的函数
此时data数据和method方法等都不可用，在开发中不常用

#### ceated(){}-----在实例生成之后会自动执行的函数
此时data数据和method方法等都已经初始化好了，非常重要。

在实际开发中，如果一进入组件，就希望调用methods中的函数，发起ajax请求，此时可以在created中，通过this.函数名（），自动调用指定的函数

#### beforeMount(){}-----在组件内容被渲染到页面之前自动执行的函数
#### mounted(){}-----在组件内容被渲染到页面之后自动执行的函数
#### beforeUpdate(){}-----在data中的数据发生变化时，会立即自动执行的函数
#### updated(){}-----当数据发生变化，页面重新渲染后，会自动执行的函数
#### beforeUnmount(){}-----当vue应用失效时（通过unmount函数），自动执行的函数
#### unmounted(){}-----当vue应用实效时，且dom完全销毁之后，自动执行的函数
### 常用模板语法
#### {{变量或者js表达式}}--差值表达式
```javascript
template: "<div>{{message}}</div>"
```

```javascript
template: "<div>{{'a'+'b'}}</div>",
template: "<div>{{Math.max(1,2)}}</div>",
```

#### v-html='message'--用html的方式去显示某个变量
```javascript
message: "<strong>hello world</strong>",
template: "<div v-html='message'>{{message}}</div>"
```

#### v-once--只使用一次某个变量来进行渲染，后续这个变量再变化，这里的使用也不会变化，，还是第一次渲染的样子--降低无用的渲染，提高性能
```javascript
template: "<div v-once>{{message}}</div>"
```

#### 动态属性---vue指令中的一些绑定，可以通过[变量]，实现绑定动态属性
如v-bind和v-click

```javascript
data(){message:'hello world,name:'title',event:'mouseenter'},
template: "<div :[name]='message'>{{message}}</div>"
template: "<div @[event]='handleClick'>{{message}}</div>"
```

#### 修饰符---一些标签的默认行为的设置？
比如，阻止表单自动提交----以前的写法是e.preventDefault()

现在：<font style="background-color:#FBDE28;">@click.prevent='handleClick'</font>

```javascript
methods:{handleClick(){alert('不提交就不跳转')},
         template:
         '<form action='https:www.badu.com' @click.prevent='handleClick'>
           <button type='submit>提交</button>
           </form>'
```

### 数据，方法，计算属性和侦听器
##### method里面的方法里面的this统一指向vue实例！！
#### templet里面调用方法传参--用{{函数（参数）}}
```javascript
      methods: {
        handleClick() {
          alert("click");
        },
        formatString(string) {
          return string.toUpperCase();
        },
      },
      template: "<div @click='handleClick'>{{formatString(message)}}</div>",
```

#### 计算属性：computed：{}和method类似，里面都是放一些方法，调用只需写名字即可
```javascript
      computed: {
        total() {
          return this.count * this.price;
        },
      },
      methods: {
        getTotal() {
          return this.count * this.price;
        },
      },
      template:
        "<div >{{total}}</div>",
```

上述computed里面的total和methods里的getTotal（）都能实现计算，method调用要加（）---但一般与计算相关都写在computed里面！！！可以避免一些不必要的渲染，提升性能。

##### computed里面的计算方法只有当<font style="color:#DF2A3F;">计算属性依赖的内容</font>发生变更时，才会重新执行计算
##### 而methods里面的方法，只要页面重新渲染，就会重新计算
#### 侦听器----监听数据或者事件的改变，来实现一些异步或者其他效果？！
监听获得数据当前和变化之前的值：current、prev

```javascript
      data() {
        return {
          price: 4,
        };
      },
      watch: {
        price(current,prev) {
          setTimeout(() => console.log("price changed"), 3000);
        },
      },
```

[this.$watch 和组件的 watch 有什么区别_qq_36437172的博客-CSDN博客](https://blog.csdn.net/qq_36437172/article/details/109151114)

#### 总结
##### computed和method都能实现的一个功能，建议使用computed，因为缓存
##### computed 和watch都能实现的功能，建议使用computed，因为更加简洁
### 样式绑定语法
#### string、Object、Array（数组里面还可以写对象）true或者false表示该属性加还是不加
```javascript
    <style>
      .red {
        color: red;
      }
      .green {
        color: green;
      }
    </style>
      
<script>
    const app = Vue.createApp({
      data() {
        return {
          classString: "red",
          classObject: { red: false, green: true },
          classArray: ["red", "green", { brown: false }],
        };
      },
      template: `
      <div :class='classArry'>
        Hello World
      </div>
    `,
    });
</script>
```

#### 组件的样式
单独改变调用的子组件的样式方法

1、在子组件上改

```javascript
    app.component("demo", {
      template: "<div class='red'>one</div>",
    });
```

2、在调用时改（但如果子组件有多个元素，则需要用v-bind绑定数据:class='$attrs.class'，表示该元素的类与调用时设置的类一样）否则不生效

```javascript
      template: `
      <div :class='classArray'>
        Hello World
        <demo :class='classString'/>
      </div>
    `,
```

```javascript
template: `
<div :class='classArray'>
  Hello World
  <demo :class='classString'/>
</div>
`

app.component("demo", {
  template: "<div :class='$attrs.class'>one</div> <div>tow</div>",
});

        
```

#### 行内样式----用对象存储，然后绑定style属性
```javascript
data() {
  return {
    styleObject: { color: "orange", background: "blue" },
  };
template: `
<div :class='classArray' :style='styleObject'>
  Hello World
</div>
`,
```

### 条件渲染
#### v-show:和v-if类似，但他的原理是通过将该标签的display值设置为none，<font style="color:#DF2A3F;">该组件不可见但仍然存在</font>
#### v-if：当为false通过直接删除dom元素实现
#### v-else
#### v-else-if-----连续的要写在一起才能生效
```javascript
  template: `
  <div v-if='show' >IF</div>
  <div v-else-if='conditionOne'>ELSE IF</div>
  <div v-else='conditionTow'>ELSE</div>
`,
```

### 列表、对象循环渲染--v-for=''
```javascript
data() {
  return {
    listArray: ["today", "is", "a", "sunny", "day"],
    listObject: { data: "monday", weather: "sunny", mood: "blue" },
  };
},
template: `
<div v-for='(item,index) of listArray'>{{item}}---{{index}}</div>
<div v-for='(value,key,index) of listObject'>{{value}}---{{key}}---
index</div>
`,
```

数组：item、index

对象：value、key、index

##### 当通过循环渲染数组或对象，为了提高渲染效率，即让已经有了的元素可以直接保留，只渲染新增的元素，需要绑定key的值为当前的index（也可以不是index，但最好用唯一的标志符）--<font style="color:#DF2A3F;">:key='index'</font>
```javascript
template: `
<div v-for='(item,index) of listArray' :key='index'>{{item}}---
{{index}}</div>
<div v-for='(value,key,index) of listObject' :key='index>{{value}}-
--{{key}}---index</div>
`,
```

#### 改变列表
##### 1、使用数组变更函数 push、pop、shift、unshift、splice、reverse等
##### 2、直接替换数组
##### 3、直接更新数组的内容
```javascript
data() {
  return {
    listArray: ["today", "is", "a", "sunny", "day"],
  };
},
methods: {
  handleClick() {
       this.listArray.push("hellow");
       this.listArray = ["today", "is", "monday"];
       this.listArray[0] = "bey";
  },
},
template: `
<div v-for='(item,index) of listArray'>{{item}}---{{index}}</div>
<button @click='handleClick'>改变数组</button>
`,
});
```

#### 改变对象
##### 直接添加或改变对象的内容
##### 如果不想展示其中的某些元素，可以用v-if，但是要在循环之后的标签里，因为循环的优先级高于条件
##### template占位符，只占位，不渲染，可用来代替某些不想渲染的div标签
```javascript
data() {
  return {
  listObject: { data: "monday", weather: "sunny", mood: "blue" },
  };
},
methods: {
  handleClick() {
    this.listObject.year = 2023;
    this.listObject.mood = "tired";
  },
},
template: `
<template v-for='(value,key,index) of listObject'>
  <div v-if='key!==data'>{{value}}---{{key}}---{{index}}</div>
</template>
<button @click='handleClick'>改变对象</button>
`,
});
```

### 事件绑定 
#### 获得原生事件e---用$event参数
```javascript
data() {
  return { count: 0 };
},
methods: {
  handleClick(num, e) {
    console.log(e);
    this.count += num;
  },
},
template: ` 
      {{count}}
      <button @click='handleClick(2,$event)'>button</button>
    `,
```

#### 事件修饰符：.stop  .self  .prevent   .capture  .once  .passive ....
#### 按键修饰符:  .enter  .tab .delete .....
#### 鼠标修饰符:  .left  .right ....
#### 精确修饰符:  .exact
[vue中的修饰符_star@星空的博客-CSDN博客](https://blog.csdn.net/weixin_43638968/article/details/108635864?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-108635864-blog-119183888.pc_relevant_3mothn_strategy_recovery&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-108635864-blog-119183888.pc_relevant_3mothn_strategy_recovery&utm_relevant_index=2)

[Vue中常见的事件修饰符及其作用_keleqy的博客-CSDN博客_vue事件修饰符的作用](https://blog.csdn.net/keleqy/article/details/119183888)

### 表单中双向绑定的指令与使用
#### v-model双向绑定，可以用在input、textarea、checkbox（多选框）、radio（单选框）
```javascript
<input v-model='message' />
```

```javascript
<textarea v-model='message'/>
```

#### checkbox---通过设置value值，并用v-model双向绑定，message设为[]，即可获得选中的box的值
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677497293551-1e3201db-28e6-4718-96c1-c26752e1a4c8.png)

```javascript
data() {
  return { message: [] };
},
template: `
  <div>
      {{message}}
      sunday<input type="checkbox" v-model='message' value="sunday" />
      hot<input type='checkbox' v-model='message' value='hot'/>
      blue<input type='checkbox' v-model='message' value='blue'/>
  </div>`,
});
```

#### radio与box的操作一样，但由于radio是单选，所以message设为''
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677497370894-097f5ae1-fb2c-460d-b5ee-d7d7f6e34f06.png)

```javascript
data() {
  return { message: "" };
},
template: `
  <div>
      {{message}}
      sunday<input type="radio" v-model='message' value="sunday" />
      hot<input type='radio' v-model='message' value='hot'/>
      blue<input type='radio' v-model='message' value='blue'/>
     
```

####  select---单选和多选双向数据绑定
```javascript
data() {
  return { message: "a" };
},
template: ` 
  <div>
      {{message}}
      <select v-model='message' 
      multiple>
          <option>a</option>
          <option>b</option>
          <option>c</option>
      </select>
  </div>`,
});
```

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677498322443-49f08299-3a22-4c46-907b-f861661b2664.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677498353826-ace272e6-3313-4811-9a7a-c32997ffa8b3.png)

##### 实现下拉列表的个数由变量个数决定，且通过value值，<font style="color:#DF2A3F;">将选择的返回值进行格式转换</font>！！！
```javascript
data() {
  return {
    message: "A",
    options: [
      { text: "A", value: { value: "A" } },
      { text: "B", value: { value: "B" } },
      { text: "c", value: { value: "c" } },
    ],
  };
},
template: `
  <div>
      {{message}}
      <select v-model='message' multiple>
          <option v-for='item in options' :value='item.value'>{{item.text}}</option>
      </select>
  </div>`,
});
```

#### checkbox----通过true-value和false-value来自定义选中与不选中时的值，默认是true和false----主要是可以改变未选中的默认值
```javascript
<input type="checkbox" v-model='message' 
  true-value='hot' false-value='sun' />
```

#### 表单修饰符----.lazy   .number  .trim(前后空格，中间的空格不行)
[【前端知识之Vue】Vue常用的修饰符_前端修饰符_饭啊饭°的博客-CSDN博客](https://blog.csdn.net/weixin_44337386/article/details/125434867)

## class3----探索组件的理念
### 组件的定义及复用性、局部组件和全局组件
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677501220960-0a85be49-ad5f-4e93-b0f2-2b72d419acb0.png)

#### 全局组件
##### 全局组件，只要定义了，处处可以使用，性能不高，但是使用起来简单，<u><font style="background-color:#FBF5CB;">名字建议小写字母单词，中间用横线间隔</font></u>
##### 不管有没有被用到，都会一直存在，会影响性能
#### 局部子组件
```javascript
const Counter = {
    data() {
      return {
        count: 1
      }
    },
    template: `<div @click="count += 1">{{count}}</div>`
  }

const HelloWorld = {
  template: `<div>hello world</div>`
}

const app = Vue.createApp({
  components: {
    // counter: Counter,
    // 'hello-world': HelloWorld,
    Counter, HelloWorld,
  },
  template: `
    <div>
      <hello-world />
      <counter />
    </div>
  `
});
```

##### 局部组件，定义了，要注册之后才能使用，性能比较高，使用起来有些麻烦，<font style="background-color:#FBF5CB;">建议大些字母开头，驼峰命名</font>
局部组件使用时，要做一个名字和组件间的映射对象，你不写映射，Vue 底层也会自动尝试帮你做映射

### defineComponent的使用
[vue3中defineComponent 的作用详解 - 掘金](https://juejin.cn/post/7198426159478456381)

### component中setup语法糖定义组件名字
[vue3中如何使用setup语法糖定义组件name - 掘金](https://juejin.cn/post/7139709801671426056)

### 组件间传值以及传值校验
#### 组件父子级之间的传值----父：通过<font style="color:#DF2A3F;">调用时直接设置</font> <font style="color:#DF2A3F;"> :参数名字=‘参数的值’</font>传参数进入组件  /  全局子组件：通过 <font style="color:#DF2A3F;">props：[ '参数名字']</font>接受与父组件传入的参数名相同的参数，一定要<font style="color:#DF2A3F;">相同</font>！！
#### <font style="color:#601BDE;">动态传参</font>，就使用<font style="color:#DF2A3F;">v-bind</font>将‘参数的值’换成父组件中data中的动态值
##### 动态传参的好处：<font style="color:#D22D8D;">可以传任意格式的参数，如</font>String, Boolean, Array, Object, Function, Symbol<font style="color:#D22D8D;">等等，而静态传参，智能传固定的字符串！！</font>
```javascript
const app = Vue.createApp({
  data(){
    return{num:'123}
  },
  template: `
  <div>
  	<test\ :c='num'>
    <test\ c='123'>
  </div>
`,
});
app.component("test", {
  props: ["c"],
  template: `<div>{{c}}</div>`,
});
```

#### 类型校验
##### 通过<font style="color:#DF2A3F;">props</font>自动校验数据类型====改写
```javascript
app.component("test", {
  props: {c:Number},
  template: `<div>{{c}}</div>`,
});
```

#### composition API使用<font style="color:#DF2A3F;">defineProps</font>
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1703483563286-85ff964a-5e9c-4776-ba9a-13c533ca9dcc.png)

##### 多个条件校验：<font style="color:#D22D8D;">type</font>（类型），<font style="color:#D22D8D;">required</font>（true表示必须要传，否则报错），<font style="color:#D22D8D;">default</font>（如果不传，则将该参数设为默认值，该值可以是一个数，也可以设为一个函数返回的数）<font style="color:#D22D8D;">validator：fun</font>----接受参数值value，检验传递的值是否符合条件，是一个函数（深度校验）
```javascript
app.component('test', {
  props: {
    content: {
      type: Number,
      validator: function(value) {
        return value < 1000;
      },
      default: function() {
        return 456;
      }
    }
  },
  template: `<div>{{content}}</div>`
});
```

### 单项数据流的理解
当需要传给组件的数据非常多时--单个单个写可读性和维护性差

##### 把父组件的data中return的数据写进对象里，直接传递该对象即可
```javascript
data() {
  return { params: { a: 1, b: 34, num: 1234 } };
},
template: `
<div><test :content="params" /></div>
`,
```

#### 定义很长名字的变量，可以用-而不是驼峰，传的时候写-，接受的时候写驼峰，vue'会自动转
```javascript
template: `
<div><test :content-abc="params" /></div>
`,
props: [contentAbc],
```

#### <font style="color:#D22D8D;">单向</font>数据流----<font style="color:#D22D8D;">子组件可以使用但不能修改</font>父组件传递过来的数据
解决办法：通过将父组件传递的数据复制一份作为自己的数据，然后再组件中使用自己的数据

```javascript
data() {
  return { mayCount: this.count };
},
props: [content],
```

##### 单向数据流保证了vue中组件的可复用性！！！
### None-Props 属性（<font style="color:#601BDE;">样式传递</font>）
#### 父组件向子组件传参，但子组件没有接收，此时，该参数会被直接加在子组件的标签上--如右边多了属性cotent=''hello''----适用于传递样式或属性修饰啥的
原始：

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677570739263-aa3a708e-7d0d-4fbd-9675-728e1a076510.png)

未接收参数：

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677570766855-d810af29-bde5-41af-8d18-4645b9f5e516.png)

#### 解决办法：<font style="color:#D22D8D;">inheritAttrs: False</font>
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1692791831427-d2f1faf2-a725-4d2b-a1ae-039184d7b35f.png)

#### 当自组件有多个根节点时，传递的Non-props属性不生效---
#### 解决办法：
##### <font style="color:#DF2A3F;">v-bind='$attrs'</font>----表示将父组件传递的所有属性都放在这里
##### 将父组件传递的多个属性分别放在不同的标签上：通过<font style="color:#D22D8D;">v-bind'变量名'="$attrs.相应的变量名"</font>
```javascript
app.component("test", {
  // inheritAttrs: False,
  // props: ["content", "content1", "content2"],
  template: `
  <div v-bind='$attrs'></div>
  <div :class1='$attrs.content1'></div>
  <div :class2='$attrs.content2'></div>`,
});
```

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677571832611-5ca4a51b-ca20-4395-ac3e-ee3df515387f.png)

##### 另外一种获取Non.props属性的方法---this.$attrs
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677571970568-91543c9d-6905-4e35-b415-89fe51f951b4.png)

### 父子组件间如何通过<font style="color:#601BDE;">事件</font>进行通信（事件传递）
#### this.$emit（‘事件’）---子组件通过this.$emit向外触发某个事件，然后父组件通过@事件=‘方法’监听子组件的该事件，并对其进行处理----让父组件帮你处理数据，就不用在子组件中复制数据了。
##### 子组件
methods: {

       <font style="background-color:#E8F7CF;"> handleClick()</font> {

          <font style="background-color:#FBDE28;">this.$emit("add")</font>;

        },

      },

      template: `<font style="background-color:#FBE4E7;"></font>

      <div <font style="background-color:#E8F7CF;">@click='handleClick'</font>>{{content}}</div>`,

    });

##### 父组件
     const app = Vue.createApp({

      data() {return { params: 1, a: "123", b: "325" };},

      methods: {

        <font style="background-color:#81BBF8;">handleAdd()</font> {

          this.params += 1; },},

      template: `<test :content="params" <font style="background-color:#FBDE28;">@add</font>='<font style="background-color:#81BBF8;">handleAdd</font>'/> `,

    }); 

#### 也可以通过向外触发事件时<font style="color:#DF2A3F;">传递参数</font>，父组件事件可以接受到
**子组件向外触发事件：**

        handleClick() {

          this.$emit("add", <font style="background-color:#FBE4E7;">this.count += 1</font>);

        },

**父组件相应的事件：**  
        handleAdd(<font style="background-color:#FBE4E7;">count</font>) {

          this.params = count;

        },

#### composition API使用 defineEmits
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1703483438148-ab9fe887-4556-490c-a261-388169502afb.png)

#### 为了清楚地知道，子组件向外触发了哪些事件，一般用需要在子组件上用一个属性将他们写在一起
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677575149920-2cde2a87-2831-4778-b64f-1ad4b8f56bf9.png)

#### 用v-model------来实现简化写法---直接和数据绑定，就可以不用再写额外的方法了------通过改写名字，可用v-model传多个变量进去
##### 父组件通过<font style="background-color:#FBDFEF;">v-model</font>将count变量传入（与子组件绑定）
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677580246428-06e56b1d-1ac3-452a-8f93-c8cfb6e8ae3a.png)

##### 也可以改名字！！
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677580364800-49e24d77-f90b-49a4-8e9b-788e7c97a1b6.png)

相应的子组件中也要将modelValue改为app！！

##### 子组件接受传入的变量名字一定要是“modelValue”否则不生效！
##### 向外触发的事件一定要叫“update:modelValue”否则不生效！
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677580278340-8b0453c2-6875-4f3b-b428-13c755f2062c.png)

### 组件间双向绑定高级内容 ---v-model自定义修饰符
##### 1、v-model.修饰符的名字
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677582721213-5ca84507-acb9-4563-875b-3f7960a00205.png)

##### 2、子组件props中添加<font style="background-color:#E6DCF9;">modelModifiers</font>属性，其值设置<font style="background-color:#E6DCF9;">default属性</font>，且设为，()=>({})，意思是，<font style="background-color:#FDE6D3;">如果v-model传入修饰符的话，modelModifiers.修饰符就是true，否则就是空</font>。
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677582897269-56561e89-a5f6-4f40-860d-0c872cf3c0c4.png)

##### 3、然后，就可以在用到的方法中为这个修饰符编写功能，可以利用修饰符做一些预先的处理
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677583032659-4e99924c-9c41-4daa-9472-54f94a644f6c.png)

### 内容分发：使用<font style="color:#601BDE;">插槽（slot）和具名插槽</font>解决组件内容传递问题---解决DOM传递问题
父组件给子组件传递DOM，子组件让传递的dom在子组件中渲染父组件传递的dom

<font style="color:rgb(77, 77, 77);">插槽，也就是slot，slot就是子组件里的一个</font>**<font style="color:rgb(77, 77, 77);">占位符</font>**<font style="color:rgb(77, 77, 77);">，一个slot的核心问题，就是</font>**<font style="color:rgb(77, 77, 77);background-color:#FBDE28;">显不显示，显示的话显示话，该如何去展示出来</font>**<font style="color:rgb(77, 77, 77);">，</font><font style="background-color:#FBE4E7;">这是由父组件所控制的</font><font style="color:rgb(77, 77, 77);">，但是</font><font style="color:rgb(77, 77, 77);background-color:#81DFE4;">插槽显示的位置是由子组件自己所决定的</font><font style="color:rgb(77, 77, 77);">，slot写在组件template的什么位置，父组件传过来的模板将会显示在什么位置。</font>

##### <font style="color:rgb(77, 77, 77);">1、将子组件在父子间的调用方法由标签变为双标签，双标签之间插入你想让子组件展示的标签样式</font>
      template: `

<font style="background-color:#CEF5F7;">      <test></font>

<font style="background-color:#CEF5F7;">        <div>{{content}}</div></font>

<font style="background-color:#F9EFCD;">        <input/>{{content}}  </font>

<font style="background-color:#F9EFCD;">      <test/></font>`,

##### 2、子组件中，用<slot></slot>来代替原来template中内容
    app.component("test", {

      template: `

      <font style="background-color:#FBDFEF;"><slot></slot></font>`,

    });

##### 3、结果：
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677587054483-6d662291-a515-4b3d-8536-a86e9e41ea32.png)

##### <font style="color:#E746A4;">注意！！！</font><font style="color:rgb(77, 77, 77);">slot没有办法直接绑定事件，如果要给子组件中的slot绑定事件的话，需要在其外层包裹另外一个标签，然后把事件绑定在该标签上，可以用t</font>~~<font style="color:rgb(77, 77, 77);">emplate占位符</font>~~<font style="color:rgb(77, 77, 77);">或者span等标签（子组件中用了template，出现了渲染不出来的情况，不知道为什么）</font>
```javascript
template: `
<template @click='handleClick'>
<slot></slot>
</template>`,
});
```

- [x] 并且父模板里调用的数据属性，使用的都是父模板里的数据
- [x] 字模板里调用的数据属性，使用的都是子模板里的数据

#### splot默认值设置---如果父组件的标签没有给值，就会直接用这个默认值代替
template: `

<template >

<font style="background-color:#FBDFEF;"><slot>默认值</slot></font>

</template>`,

});

#### 具名slot-----解决父组件中写的标签都只能一起放在子组件的一个slot中的问题
#### 父组件中，添加v-slot：名字
      template: `

      <test>

        <<font style="background-color:#D9EAFC;">template</font> <font style="background-color:#FBDFEF;">v-slot:header</font>>

          <div>header</div>

        <<font style="background-color:#D9EAFC;">/template</font>>

        <template<font style="background-color:#FBDFEF;"> v-slot:footer</font>>

          <div>footer</div>

        </template>

      </test> `,

**<font style="color:#E746A4;">但不能直接添加在子组件名上，而要用另一个标签包裹，再添加！！</font>**

#### 子组件中，slot标签上添加属性name='名字'
      template: `

      <span @click='handleClick'>

  <slot <font style="background-color:#FBDFEF;">name='header'</font>></slot>

  <slot<font style="background-color:#FBDFEF;"> name='footer'</font>></slot>

  </span>`

##### 此时父子组件就会按名字对应！！！
##### 具名插槽<font style="background-color:#FBDFEF;">v-slot:header</font>可以直接简写为-------<font style="background-color:#FBDFEF;">#header</font>就可以了！！！！！
#### 作用域插槽
##### 当子组件展示的内容要由父组件来决定，但内容参数存在于子组件中时，可以通过作用域插槽将参数由子组件传到父组件，父组件接收后，再用。
##### 1、子组件传参-----<font style="color:#E746A4;">:名字='参数'</font>


      template: `

  <slot v-for='item in list' <font style="background-color:#F8B881;">:data='item'</font>></slot>`,

    });



##### 2、父子间，接受参数----<font style="color:#E746A4;">v-slot={data}</font>可以用对象解构语法
      template: `

      <test<font style="background-color:#F8B881;"> v-slot:componentData={data}</font>>

          <div><font style="background-color:#F8B881;">{{componentData}}</font></div>

      </test>

    `,

#### 这三种插槽都是独立存在的，比如，作用域插槽不能用在匿名插槽和具名插槽上！！！
### 动态组件----<componont :is='子组件'> <font style="color:rgb(192, 0, 0);">动态切换组件的显示与隐藏</font><font style="color:rgb(64, 64, 64);">。</font>
[vue动态组件_vue中动态组件_努力学习前端的小陈的博客-CSDN博客](https://blog.csdn.net/qq_57587705/article/details/124520495)

##### 多个子组件
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677592112299-7715c446-f323-48df-be00-95ef386d8612.png)

##### 父组件控制动态切换渲染组件
切换函数！

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677592198885-f64afdf2-a230-4320-8d64-b47b96d95d28.png)

通过button，触发切换函数，然后通过currentItem变量来控制

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677592236440-5872d90c-21f8-42b6-b579-a36ffd29d99e.png)

##### 在通过component切换组件时，无法保持组件的状态（如input之前的输入会被清除），解决办法---- <font style="background-color:#F8B881;">keep-alive</font>。使用vue 内置的 <keep-alive>双标签 组件保持动态组 件的状态
#### <font style="color:#DF2A3F;">插槽透传！！------- $slot</font>
[Vue3 属性透传 $attrs 与 插槽透传 $slots](https://www.jianshu.com/p/bea0681bd7cc)

### 异步组件
##### 注册一个异步组件---------异步函数的写法
```javascript
app.component(
  "async-item",
  Vue.defineAsyncComponent(() => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({ template: `<div> I'm fine!</div>` });
      }, 4000);
    });
  })
);
```

```javascript
const asyncOne = Vue.defineAsyncComponent(() => {
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            resolve({ template: `<div> I'm fine!</div>` });
          }, 4000);
        });
      })
app.component(
  "async-item",asyncOne
);
```

### ref
#### 1、获取某个节点的DOM元素---this.$refs.count.innerHTML
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677594215327-3fb65e63-16e7-49b5-971c-10f528f945c0.png)

#### 2、获取子组件，并可以通过获取子组件调用子组件的内容---但这种的维护性不是很高
####  ![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677594472311-543831c2-554a-4c65-8184-3273b6e01a64.png)
### provide和inject---数据的多层传递：父---->子------>孙等
provide提供数据，inject直接跨越多层接受数据

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677594778283-4e1864c5-672a-4e5b-8077-8251147dd2d4.png)

##### 当需要传递data中的数据时，需要将provide写成函数形式
```javascript
provide(){
  return{
    count:this.count}
}
```



##### setup语法糖中的写法
###### 父组件
```javascript
import { provide} from 'vue'
provide('text',sonText)
```

provide中的两个变量分别是传入的变量名和变量值

如果要传递多个数据，要写多个provide

也可以通过对象或者数组的方式传入多个变量

```vue
provide('data',{
  'text':sonText,
  'price':1
})
```

###### 子组件
```vue
import {inject} from 'vue'
const sonData = inject('data')
```

inject只传入一个变量，即变量名

##### 目前这样传递数据，是一次性的，provide只传递一次，而后面数据发生变化之后，provide不会继续传递
## CLASS4----VUE中的动画
### 用vue实现基础的css过渡和动画效果
### 动画&过渡
#### 绑定相应的class----通过数据来控制
### 使用<font style="color:#601BDE;">transition标签</font>实现<font style="color:#DF2A3F;">单元素</font>组件的过渡和动画效果
#### transition标签搭配固定的css样式-----如出场和入场样式
- [x] .v-enter-from{}
- [x] .v-enter-activate{}-----出现的整个过程中的状态，也就是过渡或动画的过程
- [x] .v-enter-to{}
- [x] .v-leave-from{}
- [x] .v-leave-active{}
- [x] .v-leave-to{}

#### 固定样式也可以重命名：
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677934335970-d56a5b01-ab73-44ac-9e0e-e2a78490114f.png)

##### 此时，上面的固定样式名称就要写成自定义的名字开头的，如：.hello-enter-to{}
##### 第二中重命名的方式:----将单个css样式的全名进行自定义----可以方便地用第三方的css样式库（如Animatiaon）
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677937618367-9ed47aa7-05ea-47f7-b162-2ee9a21b7391.png)

#### 第三方css样式库---Animation---有很多样式[https://animate.style/](https://animate.style/)
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677937738969-258c2ca8-1328-4548-9820-8a7620036558.png)

   ![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677937811737-5c3d5338-40d4-4e06-ad7a-618d4a8f13f0.png)

#### 同时添加动画和过度效果
##### animation和transition中的内容都是要先在style样式中写好的
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677938157256-3465f34c-811f-40ab-be5a-e76f97e2fd21.png)

##### type属性----确定transition执行的时间所依赖的对象
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677938435969-e49d6f34-f097-41f2-8248-97afa29ae27d.png)

##### 表示此时transition标签里所有的动画或者过渡，都<font style="color:#601BDE;">以transition样式</font>里写的<font style="color:#601BDE;">时间</font>为准
#### duration属性----统一设置transition标签里动画和过渡的运行时间---它的值可以是数字也可以是对象
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677939696806-4651c9d1-b271-4444-a0db-c475c93f549e.png)

##### 对象----表示控制入场的样式持续时间为1s，出场的样式持续时间为3s
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677939799926-a86e8401-c0c1-46eb-af93-58a15e7ec919.png)

#### mode属性--------可以设置执行入场和出场的先后顺序
##### mode='out-in':表示先执行出场动画或过渡，再执行入场的
##### mode='in-out':表示先执行入场动画或过渡，再执行出场的
#### appear属性--------表示一开始就生效显示动画
#### 不使用transition来做css动画，加上 :css='false'
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677939915811-59743318-8f31-448c-9a95-de0c34068b16.png)

#### 用js来做动画-----可以调用它的一些生命周期函数（钩子函数）
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677940632737-91253c40-361d-4532-9e10-627255d3a1c5.png)

##### before-enter='处理函数'---------该函数接受一个el变量--表示这个元素
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677940226116-0f3d2df0-bf64-4b1d-939b-5d61f4a7bffe.png)

##### enter=‘处理函数’---------该函数接受el和done变量--表示这个元素以及函数完成
- [x] **<font style="color:#601BDE;">clearInterval</font>****表示清楚了animation样式，可以让动画停止**
- [x] 执行**<font style="color:#601BDE;">done（）</font>****<font style="color:#D22D8D;">表示告诉js这个函数已经执行完了，接下来就可以执行after-enter钩子函数了，否则after-enter没法执行！！</font>**

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677940360055-16fc62d9-2d1d-4e94-ac5e-672f6577db8b.png)

##### after-enter=‘处理函数’---------该函数接受一个el变量--表示这个元素
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677940597028-4dc0d350-ef5b-46c1-bb87-5acf3e68241b.png)

##### before-leave=‘处理函数’---------该函数接受一个el变量--表示这个元素
##### leave=‘处理函数’---------该函数接受el和done变量--表示这个元素以及函数完成
##### leave-after=‘处理函数’---------该函数接受一个el变量--表示这个元素
### 组件和元素切换动画的实现----transition
#### 用条件渲染控制组件或者元素切换渲染，然后用transition设置动画
### 列表动画的实现------用transition-group标签
#### .vue-move{}：在某个元素变换的过程中，其他元素移动时该怎么变化？
```javascript
.v-move{
  transition:all .5s ease-in
}
```

### 状态动画
#### 通过数据来控制内容的展示，数据不断改变，内容也不断 改变的动画
[VUE3 之 状态动画 - 这个系列的教程通俗易懂，适合自学_vue3 动画_追风人聊Java的博客-CSDN博客](https://blog.csdn.net/u011181989/article/details/123622271)

## Class5-----vue中的高级语法
### Mixin混入的基础语法
#### 将<font style="color:#DF2A3F;">外部的一些数据混入vue实例的data中</font>，当该vue实例的data中没有这个数据时，就会用混入的数据，当data中有数据时，就会用原data中的。<font style="color:#AE146E;">即，组件data 优先级高于mixin data优先级</font>。
  const <font style="background-color:#1DC0C9;">myMixin</font> = {

    number: 1

  }

  const app = Vue.createApp({

   <font style="background-color:#FBDE28;"> mixins: [myMixin]</font>,

    number: 2,

    template: `

        <div>{{number}}</div> ` });

##### 生命周期函数也可以混入---此时生命周期函数先执行混入的再执行自己的
##### methods的混入-------组件的meithods优先级高于混入的mixin里的methods的优先级
##### 这里的mixin的写法和用法是局部mixin，它只能根组件里被用，不能直接在根组件中调用的子组件里用（在子组件里再次声明才能被用）
#### 全局mixin----不用在组件中申明，只要定义了就自动嵌入到每个组件中了-----不推荐使用，维护性不高
```javascript
app.mixin({
  data(){return{number:2,count:22}},
  created(){console.log('minxin handleClick')}
})    自动会执行？？
```

#### vue实例中的自定义属性---------在根组件中通过this.$options获得
##### 自定义属性，组件中 的属性优先级高于mixin属性的优先级
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1677995771932-97397f83-9aec-4fd2-8aa1-5f42d670cf34.png)

##### 对<font style="color:#AE146E;">自定义属性</font>的合并策略做修改：app.config.optionMergeStrategies.属性=(mixinVal,appValue)=>{return mixinVal || appValue;}
```javascript
app.config.optionMergeStrategies.name=
  (mixinVal,appValue)=>{return mixinVal || appValue;}
```

### 开发实现Vue中的自定义指令----封装一些常用的功能directive
#### 全局指令
##### 定义
```javascript
app.directive("focus", {
  mounted(el) {
    el.focus();
  },
});
```



##### 使用
```javascript
const app = Vue.createApp({
  data() {return {distance: 110,};},
  template: `
  <div>
  <input v-focus />
  </div>`,});
```

#### 局部指令
##### 定义
```javascript
const directives = {
  focus: {
    mounted(el) {
      el.focus();
    },},};
```



##### 使用----derectives属性指定+v-focus
```javascript
const app = Vue.createApp({
  deectives: directives,
  data() {return {distance: 110,};},
  template: `
  <div>
  <input v-focus />
  </div>`,});
```

#### 自定义指令传参数：v-pos:arg='值'
    const app = Vue.createApp({

      data() { return {

          **<font style="background-color:#EDCE02;">distance</font>**: 110,};},

      template: `

        <div>

          <div <font style="background-color:#EDCE02;">v-pos:right="distance"</font> class="header">

            <input />

          </div>

        </div>`,});

    app.directive('pos', (el,<font style="background-color:#F297CC;"> binding</font>) => {

      el.style[**<font style="background-color:#CEF5F7;">binding.arg</font>**] = **<font style="background-color:#CEF5F7;">(binding.value + 'px'</font>**);

    })

#### 一些生命周期函数的简写：如果mounted和updated里面的内容是一样的话，可以简写为	
原来：

```javascript
app.derective("pos", {
  mounted(el, binding) {
    el.style[binding] = binding.value + "px";
  },
  updated(el, binding) {
    el.style[binding] = binding.value + "px";
  },
});
```

简写：

```javascript
app.directive("pos", (el, binding) => {
  el.style[binding.arg] = binding.value + "px";
});
```



### Teleport传送门函数-----可以将写在其他DOM位置的元素直接挂在另外一个DOM位置
[Vue3中 内置组件 Teleport 详解_vue3 teleport-CSDN博客](https://blog.csdn.net/ZYS10000/article/details/126323177)

#### 应用场景：组件引用
- [x] <font style="color:#DF2A3F;">当在父组件中使用子组件时，子组件会被层层嵌套在父组件中，其在父组件中的位置等样式，很难写</font>
- [x] 此时可以使用传送门在子组件中，把需要的DOM传送到父组件的指定位置渲染

#### <font style="color:#DF2A3F;">< Teleport > 只改变了渲染的 DOM 结构，它不会影响组件间的逻辑关系。</font>
```javascript
<teleport to='body'>
<input />
</teleport>
```

```javascript
<teleport to='#hello'>
<input />
</teleport>
```

### Render函数
通常我们都会把我们的页面结构逻辑都写在 template 中，然后再通 、过vue将我们的代码转换成虚拟DOM，相比于真实DOM，虚拟DOM是通过js代码处理的，所以消耗的性能相对较小，当然大部分情况下使用 template 创建我们的HTML是可以的，但是在有些场景下，我们真的需要通过Javascript的完全编程的能力来完成时，就可以用到 render函数，比之 template 更接近编译器。

#### template -> render -> h -> 虚拟DOM（JS对象）-> 真实 DOM -> 展示到页面上
[Vue中render函数浅浅详解_vue render函数怎么传参_专注前端研究二十年的博客-CSDN博客](https://blog.csdn.net/AI_huihui/article/details/121456284?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-121456284-blog-126907040.pc_relevant_3mothn_strategy_and_data_recovery&spm=1001.2101.3001.4242.1&utm_relevant_index=3)

#### render函数的作用就是返回一个虚拟dom，将该虚拟dom渲染成真实的dom。
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678016244370-dceaf810-478b-440a-8fb2-df4145cf1b2f.png)

```javascript
const app = Vue.createApp({
template: `
  <my-title :level="2">
    hello dell
  </my-title>
`
});

app.component('my-title', {
props: ['level'],
template:`<h1 v-if='level===1'><slot/></h1>
<h2 v-if='level===2'><slot/></h2>
<h3 v-if='level===3'><slot/></h3>
<h4 v-if='level===4'><slot/></h4>`
})
```





render函数写法---数据控制

```javascript
const app = Vue.createApp({
  template: `
  <my-title :level="2">
    hello dell
  </my-title>
`,
});

app.component("my-title", {
  props: ["level"],
  render() {
    const { h } = Vue;
    return h("h" + this.level, {}, [
      this.$slots.default(),
      h("h4", {}, "dell"),
    ]);},});
```

##### 用this.$slot获得各种插槽的内容---用this.$slots.default(）获得默认插槽里面的内容
### 插件的定义和使用
#### 插件：把通用性的功能封装起来
#### 定义
```javascript
// plugin 插件, 也是把通用性的功能封装起来
const myPlugin = {
install(app, options) {
  app.provide('name', 'Dell Lee');
  app.directive('focus', {
    mounted(el) {
      el.focus();
    }
  })
  app.mixin({
    mounted(){
      console.log('mixin')
    }
  })
  app.config.globalProperties.$sayHello = 'hello world';
}
}
```

##### install接受两个变量，一个是vue实例，另一个是传入的参数
#### 使用---实例.use(插件名，参数)
```javascript
const app = Vue.createApp({
  template: `
      <my-title />
    `
});
app.component('my-title', {
  inject: ['name'],
  mounted() {
    console.log(this.$sayHello);
  },
  template: `<div>{{name}}<input v-focus /></div>`
})
app.use(myPlugin, { name: 'dell'});
```

#### 在子组件中使用插件中provide的变量要用inject才行！！！其他的使用与一般的一样


#### 可以通过插件扩展vue实例的内容--一些通用的东西可以写在这里面，就不用重复写
### 数据校验插件实现---代码第8课
### this.$options-----表示vue实例，可以通过它互动获得vue实例中的所有东西
## class6----composition API
<font style="color:rgb(33, 53, 71);">能够通过</font>[组合式函数](https://cn.vuejs.org/guide/reusability/composables.html)<font style="color:rgb(33, 53, 71);">来实现更加简洁高效的逻辑复用</font>

<font style="color:rgb(33, 53, 71);">按照惯例，组合式函数命名以‘use’开头</font>

<font style="color:rgb(33, 53, 71);">大大降低了重构成本，这在长期维护的大型项目中非常关键。</font>

[组合式 API 常见问答 | Vue.js](https://cn.vuejs.org/guide/extras/composition-api-faq.html)

<font style="color:rgb(33, 53, 71);"></font>

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678076310234-6011fb7c-a4ca-4e5a-b9e4-0e5994d1c6cf.png)

### setup函数----在created实例被完全初始化之前自动调用---此时无法用this，无法调用实例中的方法，但实例中其他指令可以获取setup函数return的内容
compositonAPI所有代码都建立在setup函数的基础上

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678076776412-0f3badb3-5442-4c82-84dc-884d34ba70c3.png)

### ref、reactive 响应式引用的用法和原理---可以代替原来的data
#### 原理：通过proxy对数据进行封装，当数据变化时，触发模板等内容的更新，当数据发生变化时，会自动更新使用该数据的地方
#### ref处理基础类型的数据-----如字符串、number等，不适合用来处理对象、数组等数据
```javascript
const app = Vue.createApp({
  // VUE在这里会自动帮我们调用name.value所以，用的时候就可以直接用name
  template: `
    <div>{{name}}</div>
  `,
  setup(props, context) {
    // 从vue引入ref
    const { ref } = Vue;
    // proxy , 'dell' 变成 proxy({value: 'dell'}) 这样的一个响应式引用
    let name = ref('dell');
    setTimeout(() => {
      name.value = 'lee'
    }, 2000)
    return { name }
```

#### reactive处理非基础类型的数据，如对象、数组等
```javascript
const app = Vue.createApp({
  // VUE在这里会自动帮我们调用name.value所以，用的时候就可以直接用name
  template: `
  <div>{{nameObj.name}}</div>
`,
  setup(props, context) {
    // 从vue引入reactive
    const { reactive } = Vue;
    // proxy , {name:'dell'} 变成 proxy({name:'dell'}) 这样的一个响应式引用
    const nameObj = reactive({ name: "dell" });
    setTimeout(() => {
      nameObj.name = "lee";
    }, 2000);
    return { nameObj };
```

##### 但它里面的属性<font style="color:#01B2BC;">被解构出来</font>，就不是响应式了，如果要返回解构的响应式数据，就用toRefs
##### 将reactive对象里某一个属性<font style="color:#01B2BC;">赋值给一个变量</font>，这个变量也不会是响应式数据，如果想让他也变成响应式数据，可以用<font style="color:#DF2A3F;">toRefs+解构</font>或者用<font style="color:#DF2A3F;">toRefs</font>实现单个属性的操作：
```javascript
const name1=toRef(person,'name')
// 此时name1就是一个响应式数据
```

#### <font style="color:#DF2A3F;">清空reactive数组，将其length设置为0！！！</font>  
readonly---- 返回某个数据的copy值，并将其变为只读的！！
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678078689118-1a1361c5-3e09-43cf-ac84-e995ed074295.png)













#### <font style="color:rgb(33, 53, 71);">响应式 API：工具函数（isRef、</font><font style="color:#DF2A3F;">unref</font><font style="color:rgb(33, 53, 71);">、</font><font style="color:#DF2A3F;">toRef</font><font style="color:rgb(33, 53, 71);">、</font><font style="color:#DF2A3F;">toValue</font><font style="color:rgb(33, 53, 71);">、</font><font style="color:#DF2A3F;">toRefs</font><font style="color:rgb(33, 53, 71);">、isProxy、isReactive、isReadonly）</font>
[Vue.js](https://cn.vuejs.org/api/reactivity-utilities.html#tovalue)

##### toRefs----将对象或者数组中的值也变成响应式，可以通过解构的方式返回也响应也生效
```javascript
  const { reactive, readonly, toRefs } = Vue;
  // proxy , { name: 'dell'} 变成 proxy({ name: 'dell'}) 这样的一个响应式引用
  const nameObj = reactive({ name: "dell", age: 28 });
  setTimeout(() => {
    nameObj.name = "lee";
  }, 2000);
  // toRefs proxy({ name: 'dell', age: 28}), {
  //  name: proxy({ value: 'dell'}),
  //  age: proxy({value: 28})
  // }
  const { name, age } = toRefs(nameObj);
  return { name };
},
```

toRefs proxy({ name: 'dell', age: 28})====> {

**<font style="color:#DF2A3F;">name: proxy({ value: 'dell'}),</font>**

**<font style="color:#DF2A3F;">age: proxy({value: 28})}</font>**

[vue3中toRef和toRefs函数_Doe的博客-CSDN博客](https://blog.csdn.net/weixin_43613849/article/details/120281525)

[vue3 toRef函数和toRefs函数_wuxing164的博客-CSDN博客](https://blog.csdn.net/wuxing164/article/details/109801542)

##### toRefs语法将某个数据转化为响应式，并通过解构获取某个值，而当该数据中没有某个值时，toRefs会将它会将该值设为undefined，后续无法对它进行赋值等操作
##### 而toRef会将该值设为空，后续仍然可以对其赋值且具有响应式特性
##### **<font style="color:rgb(35, 38, 59);">toRef 函数会与源数据交互，修改响应式数据会造成源数据的修改，但是他的修改不会造成视图层数据的更新。</font>**
##### **<font style="color:rgb(35, 38, 59);">ref 函数可以将对象里面的属性值变成响应式的数据，修改响应式数据，是不会影响到源数据，但是视图层上的数据会被更新</font>**
[# Vue3 toRef 和 toRefs 函数 - 我是ed - 博客园](https://www.cnblogs.com/wjw1014/p/16444682.html)

#### context参数---attrs、slots和emit
##### attrs---传入的None-props属性
##### slots---获得插槽内容---原来在子组件中通过this.$slot获得
当子组件中没有template时，如果setup返回的是一个DMO，那么父组件中的插槽就会以返回的DOM为模板来进行构建

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678083122247-747d4a62-9765-48c0-8ee3-9e4bc6cfe1d3.png)

##### emit----监听子组件的事件-
原来是通过this.$emit向外触发事件，父组件通过@接受事件并赋予处理函数

现在，不用this.$emit，而直接用emit参数实现

##### 原来
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678083576041-aa8d7a12-f466-4759-8c40-5dcaf602e4a2.png)

##### 现在
handleClick(){

<font style="background-color:#FBDE28;">emit('change')</font>

}

### 6-7用component实现todolist的历史遗留问题


![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678090244363-e002eba4-5dea-4238-8b76-58f7ae8179a3.png)

### computed计算属性
#### get方法------取值时会自动运行的方法
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678091915531-dfe07517-8a2e-4c34-a5a7-2c7a47219836.png)

运行countAddFive即会调用get方法

#### set方法-------赋值时会自动运行的方法
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678092441648-55f77f62-3c51-4cc2-bb65-0c7688def3a7.png)

接受参数

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678092495274-89dda4f2-e1ba-422f-a7f2-7f4bd4d16109.png)

当运行countAddFive.value=值，时则会运行set函数，此时count.value被设置为10,且，然后执行get计算得到返回countAddFive计算的结果得到15

### watch和watchEffect的使用和差异性
#### watch
##### 在setup中，watch具有一定的懒惰性（第一次页面渲染刷新的时候不会执行，元素改变了才执行）
监听多个元素，只要其中有一个元素改变，就会执行

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678100412341-2f1cce39-d106-4742-ad89-577cc9bb8542.png)

取消侦听------stop

```javascript
const stop=watch([() => nameObj.name, () => nameObj.englishName],
          ([curName, curEng], [prevName, preEng]) => {
            console.log("watch", curName, prevName, "---", curEng, preEng);
            setTimeout()=>{stop();},2000}
          })
```

#### watchEffect
##### 无惰性，立即执行
##### <font style="color:#DF2A3F;">不需要传递你要侦听的内容</font>，自动会感知代码依赖，不需要传很多参数，<font style="color:#DF2A3F;">主要需要一个回调函数</font>
#### <font style="color:#DF2A3F;">不能获得之前数据的值</font>
```javascript
  const stop = watchEffect(() => {
    console.log(nameObj.name);
    console.log(nameObj.englishName);
    setTimeout(() => {
      stop();
    }, 5000)
  })
```

### 生命周期函数的新写法
```javascript
  const app = Vue.createApp({
    // beforeMount => onBeforeMount
    // mounted => onMounted
    // beforeUpdate => onBeforeUpdate
    // beforeUnmount => onBeforeUnmount
    // unmouted => onUnmounted
    setup() {
      const {
        ref, onBeforeMount, onMounted, onBeforeUpdate, onUpdated,
        onRenderTracked, onRenderTriggered
      } = Vue;
      const name = ref('dell')
      onBeforeMount(() => {
        console.log('onBeforeMount')
      })
      onMounted(() => {
        console.log('onMounted')
      })
      onBeforeUpdate(() => {
        console.log('onBeforeUpdate')
      })
      onUpdated(() => {
        console.log('onUpdated')
      })
      // 每次渲染后重新收集响应式依赖
      onRenderTracked(() => {
        console.log('onRenderTracked')
      })
      // 每次触发页面重新渲染时自动执行
      onRenderTriggered(() => {
        console.log('onRenderTriggered')
      })
      const handleClick = () => {
        name.value = 'lee'
      }
      return { name, handleClick }
    },
    template: `
      <div @click="handleClick">
        {{name}}
      </div>
    `,
  });
```

#### componont中是没有beforeCreate和created函数的，因为setup函数的执行时间在这两个函数之间，可以直接写在setup上就可以
#### 新的生命周期函数
##### onRenderTracked(()=>{}) :每次渲染完之后，收集响应式依赖时会执行的
##### onRenderTriggered每次重新渲染被触发时
### Provide、inject、模板Ref的用法
#### 单向数据流：父组件向子组件传递数据，子组件用父组件的数据，但是不能直接在子组件中修改父组件的数据，要通过调用父组件给的方法，在父组件中修改数据。！！
##### 父组件传递数据provide（）
##### readonly-----以只读的方式传递数据
##### changeName---向子组件传递一个可修改父组件数据的方法
```javascript
const app = Vue.createApp({
  setup() {
    const { provide, ref, readonly } = Vue;
    const name = ref('dell');
    provide('name', readonly(name));
    provide('changeName', (value) => {
      name.value = value;
    });
    return { }
  },
  template: `
      <div>
        <child />
      </div>
    `,
});
```

#### 子组件接收数据：inject()
##### 'hello'表示，如果没找到‘name’变量的话，其默认值设为‘hello’


```javascript
app.component("child", {
  setup() {
    const { inject } = Vue;
    const name = inject("name", "hello");
    const changeName = inject("changeName");
    const handleClick = () => {
      changeName("lee");
    };
    return { name, handleClick };
  },
  template: '<div @click="handleClick">
  {{name}}</div>',
});
```



#### 模板ref-----在compositionAPI的语法下获得真实的DOM元素节点
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678104348268-cbf116aa-618e-441e-9407-f4086aa46884.png)

## CLASS7---Vue项目开发配套工具讲解
### VueCli的使用和单文件组件
### Vue-Router的理解和使用
#### 路由：根据url的不同，展示不同的内容
哈希路由：url地址带#号：比如：http://localhost:8080/#/

#### 在App.vue中写跳转链接---<router-link to="/">Home</router-link> 并用<router-view />展示当前路由对应的组价内容
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678111958384-cfa02a4f-39bd-4a1f-ba8c-11e095a1d939.png)

#### 在router/index.js中配置每个路由信息
```javascript
import { createRouter, createWebHashHistory } from "vue-router";
import HomeView from "../views/HomeView.vue";

const routes = [
  {
    path: "/",
    name: "home",
    // 路径名字为home，展示的组件为HomeView
    component: HomeView,
  },
  {
    path: "/about",
    name: "about",
    // 路径名字为about，展示的组件为AboutView.vue
    // route level code-splitting
    // this generates a separate chunk (about.[hash].js) for this route
    // which is lazy-loaded when the route is visited.
    component: () =>
      import(/* webpackChunkName: "about" */ "../views/AboutView.vue"),
  },
];

const router = createRouter({
  history: createWebHashHistory(),
  routes,
});

export default router;
```

### 异步加载路由
#### 只有当进入到该页面时，才加载该页面的内容---首页加载更快，但页面之间的切换可能会变慢，根据实际情况应用
##### 语法：import(/* webpackChunkName: "about" */ "../views/AboutView.vue")
### VueX-----数据管理框架---跨页面的数据管理
#### 它创建了一个全局唯一的仓库，用来存放全局的数据，每个页面都可以获取
#### 获取方式：<font style="color:#DF2A3F;">this.$store.state.数据名</font>
##### 定义：
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678162720939-715651d2-a239-4912-b064-41867592a8fe.png)

##### 获取：
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678162798413-e42f0c0e-013b-4a4b-aeab-a9ab961350aa.png)

#### 全局数据的修改
1. **子组件**派发一个名为‘changeName’的action-----dispatch

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678166167927-e07335f6-d194-48c9-b652-96db576dca5e.png)

2. store感知到派发的名为‘changeName’的action，执行changName
3. 提交一个commit，触发一个名为‘changeName’的mutation（this.commit）
4. 对应的mutation被执行----changeName
5. 在mutation里面修改数据
6. ![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678166259787-9bf8ba55-509b-4ac2-b82a-f7d877542724.png)

##### 如果不涉及任何异步操作修改代码，可以直接在子组件中提交commit，修改，可以不用action；如果涉及异步操作，则必须要用action，<font style="color:#DF2A3F;">因为mutation里不允许写异步代码</font>。this.$store.commit('changeName')
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678166401067-6711aec5-4f81-4573-8f5f-f410b0f29689.png)

##### 参数传递
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678166760185-239f096e-3458-4584-a2e9-5bf69f20b634.png)

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678166813149-d49eaac3-b17d-4ab9-acdf-2ceaa858123f.png)

#### 全局数据在一个地方改变，其他地方都会改变！！
#### 在component中通过VueX修改数据-----useStore
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678167989929-bc6a641a-357b-42ba-8957-0b1ed7f4baeb.png)

### 使用axios发送ajax请求
[起步 | Axios 中文文档 | Axios 中文网](https://www.axios-http.cn/docs/intro)

[axios中文文档 - 内容详细层次合理_axios文档_大前端工程师的博客-CSDN博客](https://blog.csdn.net/chengqige/article/details/129186778)

```javascript
import { createStore } from "vuex";
import axios from "axios";

export default createStore({
  state: {
    name: "xiaokangMiao",
  },
  getters: {},
  mutations: {
    changeName(state, str) {
      state.name = str;
    },
  },
  actions: {
    getData(store) {
      axios.get("https://www.fastmock.site/mock/").then((response) => {
        console.log(response);
        const msg = response.data.desc;
        store.commit("changeName", msg);
      });
    },
  },
  modules: {},
});
```

## Class8 “京东到家”项目首页开发
### 工程目录代码简介及整理
#### Eslint插件---js代码检测工具
#### Vetur插件----<font style="color:rgb(18, 18, 18);">用于为</font><font style="color:rgb(18, 18, 18);background-color:rgb(246, 246, 246);">.vue</font><font style="color:rgb(18, 18, 18);">单文件组件提供代码高亮以及语法支持</font>
### 基础样式集成和移动端开发模拟器的使用
#### normallize.css---让我们的代码在所有的浏览器上能保持一致
安装报错---dependency conflict 

解决办法：<font style="color:rgb(77, 77, 77);">在安装的 命令后面 --legacy-peer-deps</font>

[解决版本冲突问题：Fix the upstream dependency conflict, or retry_敬云的博客-CSDN博客](https://blog.csdn.net/weixin_56858521/article/details/127170870?spm=1001.2101.3001.6650.7&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-7-127170870-blog-125031241.pc_relevant_multi_platform_whitelistv3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-7-127170870-blog-125031241.pc_relevant_multi_platform_whitelistv3&utm_relevant_index=13)

#### 移动端开发模拟器
额。。。。。就是网页检查的移动端大小

### 首页底部导航完成
#### rem移动适配
页面缩放时，组件随着页面一起缩放

先设置html的fontsize--一般按照iphone6/7/8设置

#### flex布局
父元素：display：flex

子元素：flex:1

#### 绝对定位--将div定位在底部
position:absolute；

buttom：0

#### BEM命名法
[CSS — BEM 命名规范 - 掘金](https://juejin.cn/post/6844903672162304013)

#### iconfont-----在线地址（父子iconfont.css中的部分代码，然后将地址替换/更新为在线地址，就可以不用将字体图标下载到本地，管理更方便了）
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678198435455-36e5a32b-da82-4aed-bcbf-123b0467d4cf.png)

类名为iconfont，其值为复制的值

#### sass语法：&和@import
####  浏览器默认能显示的最小字号为12px，所以如果需要字号为10px的文字，不能直接设置字体大小为10，可以通过缩放（transform:scale()）的方法来实现具体大小！！
    <!-- span标签是行内元素，一行显示多个，不可以设置宽高，宽高由内容默认撑开 -->

    <!-- margin的位置书写顺序：上右下左（顺时针） -->

### 使用Scss组织地址区域布局
### 图片加载防抖（css解决方法）
![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678630365149-39f7c9d0-66b8-466b-ab4d-3a7b01ff91fd.png)

#### 设置~height’为0的主要目的是<font style="color:#DF2A3F;">让父容器占用页面上的空间尽可能小</font>，从而避免页面在图片加载前出现布局抖动或闪烁的情况<font style="color:#DF2A3F;">。同时，将“height’设置为“0”也可以让后面的padding-botton’生效，从而根据图片的宽高比计算出一个合适的高度值，使得图片占据的空间和父容器的大小保持合适的比例</font>。如果将“height’设置为其他值，可能会影响到padding-bottom的计算结果，从而导致图片占据的空间大小不符合预期。
#### padding的值写<font style="color:#DF2A3F;">百分比</font>，是<font style="color:#DF2A3F;">根据父元素的宽度</font>来计算的！
#### padding-bottom=图片的高/图片的宽，保证了padding的宽高比是和图片一样的！一般会把图片的width值设置为某个百分数，也就是父级宽度的百分之几
[前端节流（throttle）和防抖动（debounce）](https://www.jianshu.com/p/11b206794dca)

### VUE作用域约束以及Vue开发者工具的安装使
### CSS样式属性---scoped
当 style 标签里面有 scoped 属性时，它的css只作用于当前组件中的元素。在单页面项目中可以使组件之间互不污染，实现模块化。

[style 标签属性 scoped 的作用和原理_style scoped作用_三个木马人的博客-CSDN博客](https://blog.csdn.net/weixin_43299180/article/details/112978697)

[vue---style scoped属性的作用和原理、scoped穿透_style的scoped_maidu_xbd的博客-CSDN博客](https://blog.csdn.net/maidu_xbd/article/details/106361205)

### <font style="color:rgb(32, 33, 36);">Vue.js devtools</font>
name为开发者devtools提供名字--否则devtool就会用文件名来代替

![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678709112356-b93c305b-c796-4638-884c-ebd1931c8741.png)   ![](https://cdn.nlark.com/yuque/0/2023/png/2587809/1678709194262-525579e9-3399-4a65-a652-2a61d0d2b78f.png)

### 路由守卫--vue-router校验
对路由进行权限管理，必须符合条件才能访问

#### 组件守卫：在js中获得router实例以及router.push操作
必须是通过路由规则进入该组件才可以调用 beforeRouteEnter（to，from，next），beforeRouteLeave（to，from，next）

```vue
import { useRouter } from 'vue-router'
export default {
  name: 'Login',
  setup() {
    // 获得路由实例，对路由跳转做一些改变
    const router = useRouter()
    localStorage.isLogin = true
    const handleClick = () => {
      // 通过push方法来实现跳转
      localStorage.isLogin === 'true' ? router.push({ name: 'Home' }) : alert('请先登录')
    }
    return { localStorage, handleClick }
  }
}
```

```javascript
   //进入守卫：通过路由规则，进入该组件时被调用
beforeRouteEnter (to, from, next) {
   },
   //离开守卫：通过路由规则，离开该组件时被调用
beforeRouteLeave (to, from, next) {
   }
```

#### 独享守卫---当访问这个路径前才执行beforeEnter((to, from, nex)=>{})
<font style="color:rgb(77, 77, 77);">放在需要进行权限设置的路由里面，参数语法和全局一样  当访问这个路径前才执行</font>**<font style="color:rgb(77, 77, 77);">beforeEnter()</font>**

```javascript
  {
    path: '/login',
    name: 'Login',
    component: Login,
    // 正常情况下，已经登录之后，login页面应该是不能被跳转显示了
    // beforeEnter 访问login页面之前会执行的函数
    beforeEnter(to, from, next) {
      // 表示是否登录的变量
      const isLogin = localStorage.isLogin
      // 如果已经登录了，那就跳转到Home页面，如果没有登录，那就正常展示login页面
      isLogin ? next({ name: 'Home' }) : next()
    }
  }
```

#### 全局守卫----beforeEach((to, from, next)=>{})每次做路由跳转之前都会执行
##### <font style="color:rgb(77, 77, 77);">有三个参数to：去哪个路径，from：从哪个路径里来，next：是个函数调用的时候next()放行</font>
```javascript
// router.beforeEach每次做路由跳转之前都会执行这个方法
// to要跳过去的页面信息，from从哪里调过来的页面信息
// next（）表示继续执行
router.beforeEach((to, from, next) => {
  const { isLogin } = localStorage
  // console.log(isLogin)
  // 但这样写，如果你没登录的话，就会一直跳转到login而不会把login页面显示出来
  // 所以加一个条件，就是如果你访问的是login页面的话，也可以给你展示
  isLogin === 'true' || to.name === 'Login' ? next() : next({ name: 'Login' })
```

### 使用axios发送登录mock请求
[请求配置 | Axios 中文文档 | Axios 中文网](https://www.axios-http.cn/docs/req_config)

[GitHub - axios/axios: Promise based HTTP client for the browser and node.js](https://github.com/axios/axios)

#### axios的封装
```javascript
import axios from 'axios'


export const post = (url, data = {}) => {
  return new Promise((resolve, reject) => {
    axios
      .post(url, data, {
        // 会自动将baseURL和输入的url拼接在一起！！！
        baseURL: 'https://www.fastmock.site/mock/ae8e9031947a302fed5f92425995aa19/jd',
        headers: {
          'Content-Type': 'application/json'
        }
      })
      .then(
        response => {
          // 只返回需要的东西，可以更直接地看到数据、提取数据
          resolve(response.data)
        },
        err => {
          reject(err)
        }
      )
  })
}
```

### Toast----自定义的弹框
#### 一些公共组件放在components文件夹里
用v-if控制弹窗的显示----数据绑定与传递来显示传递的内容---用settimeout函数来控制显示时长

### export和export default
[vue中export和export default_喵酱睡着了的博客-CSDN博客](https://blog.csdn.net/sumiao64427/article/details/126545522)

#### 共同点
<font style="color:rgb(85, 86, 102);background-color:rgb(238, 240, 244);">export default和export都能导出一个模块里面的常量，函数，文件，模块等，在其它文件或模块中通过import来导入常量，函数，文件或模块。这样就可以使用它们了。</font>

#### <font style="color:rgb(85, 86, 102);">区别</font>
在一个文件或模块中，export,import可以有多个，**export default只允许向外暴露一次。**

**<font style="background-color:#E6DCF9;">通过</font>****<font style="color:#DF2A3F;background-color:#E6DCF9;">export</font>****<font style="background-color:#E6DCF9;">方式导出，在导入的时候需要加 </font>****<font style="color:#DF2A3F;background-color:#E6DCF9;">{} </font>****<font style="background-color:#E6DCF9;">大括号，</font>****<font style="color:#DF2A3F;background-color:#E6DCF9;">export default</font>****<font style="background-color:#E6DCF9;"> </font>****<font style="color:#DF2A3F;background-color:#E6DCF9;">不需要加{}</font>****<font style="background-color:#E6DCF9;">.</font>**

export default 向外暴露的成员，可以使用**任意变量**来接收，如 import a from './test.js

使用 export 导出的成员，**<font style="color:#DF2A3F;">必须严格按照导出时候的名称</font>**，来使用** { } **按需接收

使用 export 导出的成员，若换个变量名称接收，可以使用 **<font style="color:#DF2A3F;">as </font>**换别名，如<font style="color:#DF2A3F;">import {content as content123} from ‘./test.js’</font>

### 在线接口工具Mock
[在线接口Mock工具fastmock详解 - 猫老板的豆 - 博客园](https://www.cnblogs.com/bingcola/p/16499145.html)

### Mock.js
[Mock.js有什么用_mock.js作用_丁竹兰的博客-CSDN博客](https://blog.csdn.net/weixin_68793854/article/details/125039917)

[mockjs语法](https://www.jianshu.com/p/533a869c808c)

### <font style="color:rgb(34, 34, 38);">axios的二次封装</font>
[axios的二次封装(详解)_盛夏的记忆的博客-CSDN博客](https://blog.csdn.net/m0_66285809/article/details/127304923)

### useRoute和useRouter
##### useRouter表示的整个项目的路由，
##### useRoute表示当前访问的路由的信息--可以拿到id
route.path, route.name, route.params









