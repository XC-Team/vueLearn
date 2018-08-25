# vuedemo02

> A Vue.js project

```js
npm install -g vue
vue init webpack-simple my-project
cd my-project
npm install
npm  run dev
```

## Vue知识总结
>Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层

模块化与组件化的区别：

1.模块化是针对代码来说的，即抽离js代码进行复用
2.组件化是针对Ui来说的，由组件就能很快组成一个页面

vue与react的比较

1.Vue里使用.vue格式模板实现组件化，而react采用把html写进js即jsx
2.vue是双向数据绑定，react是单向数据绑定，在通过state来管理

### 声明式渲染
```js
<div id="app">
  {{ message }}
</div>
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```
### 条件与循环
```js
<div id="app-3">
  <p v-if="seen">现在你看到我了</p>
</div>
var app3 = new Vue({
  el: '#app-3',
  data: {
    seen: true
  }
})
```
### 处理用户输入

v-on 指令添加一个事件监听器，通过它调用在 Vue 实例中定义的方法

v-on:click = @click 事件

### 组件化应用构建

![](./images/components.png)

全局定义组件

```js
// 定义名为 todo-item 的新组件
Vue.component('todo-item', {
  template: '<li>这是个待办项</li>'
})
<ol>
  <!-- 创建一个 todo-item 组件的实例 -->
  <todo-item></todo-item>
</ol>
```
### vue生命周期

![](./images/lifecycle.png)

### vue指令

v-html绑定html
v-text绑定文本
v-bind:属性 = :属性 绑定属性
v-on:click = @click 事件

v-class
```
<ul  v-for="item in list1">
    <li :class='{red: flag, blue: !flag}'>{{item}}</li>
</ul>

```

v-style
```
<div class="box" :style="{'width': boxWidth+'px'}">
    
</div>
```



获取ref定义的dom节点
```js
<input type="text" ref="userInfo">
<div ref="box"></div>
<button @click="getValue()">点击</button>
export default {
    data(){
        return {
            message: '这是一个根组件',
        }
    },
    methods: {
        getValue(){
            console.log(this.$refs.userInfo);
            this.$refs.box.style.background='red';
            alert(this.$refs.userInfo.value);
        }
    }
} 
```
自定义属性

1.html里设置data-xx

2.把$event传给事件

3.事件利用e.srcElement.dataset.aid获取 或
e.srcElement.style.background='red';修改样式

```js
<button data-aid='123' @click="eventFn($event)">事件对象</button>      
    export default {     
      data () { 
        return {
          msg: '你好vue',
          list:[]      
        }
      },
      methods:{
        eventFn(e){
          console.log(e);
          // e.srcElement  dom节点
          e.srcElement.style.background='red';
          console.log(e.srcElement.dataset.aid);//123  /*获取自定义属性的值*/
        }

      }
    }
```

