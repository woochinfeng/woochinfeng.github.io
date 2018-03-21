---
layout: post
title: Vue是什么？
date: 2017-08-02 00:00:00 +0300
description: Vue # Add post description (optional)
img:  vue-logo.jpg # Add image post (optional)
tags: [JS, VUE] # add tag
---


**框架模式：**
>框架模式是管理和组织代码的学问

(1)MVC
>是最常见的软件架构之一，业界广泛应用；
  MVC分为三部分，view(用户界面) Contoller(业务逻辑) Model(数据保存);

  >说明：view传送指令到controller
        controller完成业务逻辑，model改变状态
        Model将新的数据发送到view，用户得到反馈；

  >特点:所有的通信都是单向的

  >互动模式：
  接受用户指令时，MVC分为两部分，一种是通过View接受指令，传递给controller:另一种是直接通过controller接受指令;

(2)MVP
>MVP模式将Controller改名为Presenter,同时改变了通信方向；

>1、各部分之间的通信，都是双向的；

>2、View和Model不发生联系，都是通过presenter传递

>3、view非常薄，不部署任何业务逻辑，没有任何的主动性，而presenter则是所有的逻辑部署都在哪里

(3)MVVM
>MVVM模式将presenter改名为ViewModel,基本上与MVP模式完全一致。
  view ViewModel Model
  唯一的区别是，它采用的是双向绑定，view的变化，自动反映在viewModel；

一、了解Vue
**Vue.js 是什么？**

>Vue.js（读音 /vjuː/, 类似于 view） 是一套构建用户界面的渐进式框架。与其他重量级框架不同的是，Vue 采用自底向上增量开发的设计。Vue 的核心库只关注视图层，并且非常容易学习，非常容易与其它库或已有项目整合。另一方面，Vue 完全有能力驱动采用单文件组件和 Vue 生态系统支持的库开发的复杂单页应用。
Vue.js 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。

>官网 http://cn.vuejs.org/

>Vue.js CDN：https://unpkg.com/vue/dist/vue.js

>NPM版本要高于3.0 查看版本:npm -v
>
>低的话要升级:  cnpm install npm -g

**项目构建步骤**
```
npm install --global vue-cli
vue init webpack ***
cd **
npm install
npm start
```

代码初识

>Hello Vue（通过元素选择器绑定数据）

```
<div id="app">
	{{ message }}
</div>

var app = new Vue({
	el: '#app',
	data: {
		message: 'Hello Vue!'
	},
	methods:{
		showMsg:function(){
		alert(this.message)
	}
})
```
学习完其他框架之后再和其他框架作比较???

_______________________________________________
基本用法：

>1、v-xxx

>2、属性绑定v-bind  缩写  ‘:’

```
<a v-bind:href="url"></a>
<!-- 缩写 -->
<a :href="url"></a>
```

>3、事件绑定 v-on  缩写 ‘@’
```
<a v-on:click="doSomething"></a>
<!-- 缩写 -->
<a @click="doSomething"></a>
```

1、模板表达式

```vue
//流控制也不会生效，请使用三元表达式和逻辑表达式
{% raw %}
	{%if user.isAdmin%}
	true
	{% else %}
	false
	{% endif %}
{% endraw %}
```

2、html内容 `v-html {{{}}}`

动态渲染的任意 HTML 可能会非常危险，因为它很容易导致 XSS 攻击。
请只对可信内容使用 HTML 插值，绝不要对用户提供的内容插值。

```
eg:{{htmlstr}}
   htmlstr:"<a href='todolist.html'></a>"
```

`v-cloak`，在元素的最外面加`v-cloak`属性，另外手动的在style中加``[v-cloak]{dispaly:none}``;表示一开始元素信息全部隐藏，等数据解析出来才会显示

- `v-html` 绑定标签

- `v-text` 绑定文本

- `v-pre`  不当做数据去解析

- `v-if` 对DOM节点的添加和移除(不需要切换的时候用v-if,切换的时候消耗性能)

- `v-show`, DOM的显示和隐藏(频繁的切换，初次渲染的时候消耗性能)

- `v-model` 数据双向绑定

- `v-for="(item,index) in arr" :key='index'`

- `:style='obj'||'{}'`

- `:class="{'box-bg':true}"`注意JS中不识别-，要记得加引号

**过滤器：**

全局定义
```
Vue.filter('reverseMsg',function(value){
	return value.split('').reverse().join('');
});
```
局部定义:
```
new Vue({   
	 el:"#box",
	 data:{
	 	message:"msg"
	 },
	 filters:{
		//局部定义        
		reverseMsg:function(value){
		   return value.split('').reverse().join('')      
		}
	  }
})
```

计算属性：computed

```
new Vue({    
	el:"#box",   
 	data:{     
   		message:"msg"    
   	},
    computed: {
		fullName: function () {
    		return this.firstName + ' ' + this.lastName
		}
	}
})
```

watch（一般执行异步操作或开销较大的操作）:

```
new Vue({   
	el:"#box",   
  	data:{
     	message:"msg"    
  	},   
  	watch: {
		firstName: function (val) {
			this.fullName = val + ' ' + this.lastName
		},
		lastName: function (val) {
			this.fullName = this.firstName + ' ' + val
		}
 	}
})
```
vue-resource（支持 jsonp）

```js
cdn:<script src="https://cdn.jsdelivr.net/vue.resource/1.3.1/vue-resource.min.js"></script>
// 基于全局Vue对象使用http
Vue.http.get('/someUrl').then(successCallback, errorCallback);
Vue.http.post('/someUrl').then(successCallback, errorCallback);
```

```js
在一个Vue实例内使用$http
this.$http.get('/someUrl').then(successCallback, errorCallback);
this.$http.post('/someUrl').then(successCallback, errorCallback);
```

axios  

```js
CDN:<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```


1、事件绑定
```js
    v-on:eventname
    //简写
    @eventname
```


2、阻止冒泡
```js
   e.stopPropagation?e.stopPropagation():e.cancelBubble=true;
    <div id='inner' @click.stop='inner'></div>

    //阻止默认事件
    e.preventDefault?e.preventDefault():e.returnValue=false;
    <a href="" @click.prevent='aa'> 链接</a>
```


3、键盘事件
```js
   ev.keyCode
```

4、通过键值绑定事件
```js
    @keyup.13="show()"
    @keyup.enter="show()"
```

事件修饰符:

```js
.stop  阻止事件冒泡
.prevent 阻止默认事件
.capture 事件捕获模式
.self  只触发我本身(不包含子元素)__________
```

该元素本身（而不是子元素）触发时触发回调
按键修饰符:

```js
.enter
.tab
.delete (捕获 "删除" 和 "退格" 键)
.esc
.space
.up   38
.down 40
.left 37
.right 39
.ctrl
.alt
.shift
```


生命周期,
Vue实例是一个完整的生命周期，即从开始创建，初始化数据，编译模板，挂载DOM,渲染更新，渲染卸载的过程，成为生命周期.
创建
```js
beforeCreate
created
```


添加
```js
beforeMount
mounted （在这里进行数据请求）
```


更新
```js
beforeUpdate
updated
```

激活（动态切换的时候会触发）
```js
activated
deactivated
```

销毁  `（主动销毁this.$destroy()）`
```js
beforeDestroy   
destroyed
```
**组件与传递数据**

1、组件的定义与注册

```js
	//1.通过Vue.extend定义组件
	    var Header=Vue.extend({
			template:`<h1>我是header标签</h1>`
		});
	//2.注册组件
	    Vue.component(‘v-header’,Header); //组件名不能和html标签名一样
	//3.使用组件
	    <v-header></v-header>
```

2、组件的定义和注册2js

```
	//1.直接定义组件
	    var Header={
	        template:‘<h1>这是一个头部组件</h1>’        
	    }
	//2.注册组件
	var vm=new Vue({
	    el:‘#box’,
	    data:{
	        name:‘zhangsan’
	    },
	    components:{
	        ‘v-header’:Header   //在vue内部注册组件
    	}
    });
```

3、组件的数据和方法

```js
   组件可以自己定义方法和数据（数据必须通过方法返回）

   var Header={
       template:'<h1 @click="change()">{{name}}</h1>',
       data:function(){   /*组件里面定义数据的方式*/
            return {
               name:'头部组件',
             }
       },
       methods:{
           hange(){
             this.name='头部组件变';
             alert('this is a  Header component  run');
           }
       }
   };
```

4、组件的模板

```js
	//1、通过script创建
	<script type="x-template" id="header">
	    <div class="header">
	        <p>{{msg}}</p>
	        <button @click="run()">这是一个按钮</button>
	    </div>
	</script>
	//2、或者通过template标签创建
	<template id=" header ">
	    <div class="header">***这里需要有一个根元素
	        <p>{{msg}}</p>
	        <button @click="run()">这是一个按钮</button>
	    </div>
	</template>
	//3、使用
	var Header={template:'#header'}
```


5、组件标签的内容分发

```js
	//1、通过<slot></slot>插入组件标签嵌套的内容
	<div id="box">
	   <v-header><span slot ='text'></span></v-header>
	</div>
	<template id="aaa">
	    <div>
	        <slot  name=”text”>
	            //这是默认情况下的内容
	        </slot>
	    </div>
	</template>
```

组件通信

```js
//1、父组件控制子组件通信（props）
	//1、调用组件
	       <v-content >
	         	<v-list :list-fata="listData"></v-list>
	       </v-content>
	//2、在content组件内部通过props接受
	      props:['list-data']
		//list-data表示标签的属性时不能用驼峰
    //3、在模板中用的时候再用驼峰
       <li v-for='(item,index) in listFata'>{{item}}</li>
```

2、子组件控制父组件通信


3、无关系的组件通信
