vue 
    数据共享
    路由

    主体框架
        插值表达式 :  -> {{ 表达式 }}    {{ 1+1 }}
                只能是 Math 这样的 内置对象 可以写在里面， window 的并不能写进。 
    
        指令  :   ->   :class :value  v-if  v-for  v-on ， @click绑定事件
        computed (计算属性)  
        Watch
        过滤器
        自定义指令
        响应式原理
        虚拟阶段原理
    
        组件
        组件通信
        声明周期
    
    插件 。。。 
        状态
        路由 。 

**vm的直接属性探究**
```js
vm.$el ;   // 就是一个根元素标签。 

```

> 区别于 DOM 操作。 是居于 **数据驱动**。
> DOM 操作是 ： 获取节点， 操作节点
> Vue : 不会出现 DOM 的操作。 
构造函数习惯首字母大写。 

w

```html
目前的总结 ： 
1 插值表达式 是可以写表达式的。 什么是表达式 操作数 和 操作符
2 指令 先了解意思 ;   预期是可以 被赋什么类型的值。 
		v-text : => <span> {{ 向内插入text }} </span>
		v-html : => <span>  {{ 向内插入html }} </span>
		v-show : 值为 true/false  =>  显示 或 display:  none 
		v-if   : true/false   展示 或 被注释(注释就是根本就不进入模板中)
		v-else :   和 if else  else if 用法一样。 只展示其一
		v-else-if : 
		
		v-for :  根据 for in 来判断重复渲染多少;  
						预期：Array | Object | number | string | Iterable (2.6 新增)
						注意的事项：  对数组的解构 (item, i ) 值 和 键。 
		v-on  : 缩写 `@` 用于绑定事件 , 对象语法
				写法有点多 ， 且引出了动态事件 和修饰符 
			v-on:click=""  v-on="{ click : 'fn1', mousedown : 'fn2' }"  @click.stop.prevent="fn3"
		v-bind : 缩写 `:`	, 把属性的去值变为变量 :src="path" path 就是一个变量。 得在 this 里面去找
				修饰符 ：  prop   camel  sync
				



```

## 在vue 中的虚拟元素中绑定事件 `element-ul` 里面荡下来的元素 可以加 `native` 修饰符。 



## 指令
> v-if:class=""       v-if 指令，     :class 参数
> v-on.prevent  : 指令  参数   修饰符( modify )
> 缩写 ：  v-on:click - >  @click

```js
:class= ..
:value="" 
v-bind:title="message" :  绑定标题这个属性 给 data.message 。 
    简写 ：    `:title`   `:` 就是 v-bind 的简写
        让指令的值 变成任意表达式  ->  :title='任意表达式'
v-if='true'   :  删除添加
    v-else  , v-else-if
v-show :         display: none; 'block'
v-for="(item, i) in todos"  :  循环， 绑定数组数据来渲染, 循环创建
        (i, key, value) in object,  
v-on:       :  添加一个时间监听器。 v-on:click="fnName"
v-once : 这个属性的 标签插值不会改变
v-model : 把表单的 value 和 Input change 事件 绑定和响应
					在复选框中，数据的变化是靠 checked(checkbox , radio) 或是  selected(select) 的状态来响应
          选中则可以拿到 value 中的值。 checkbox，selected 用数组，  radio 则是单值
          		重新认识了 desable 属性的作用， 让第一个说明做一个站位符
v-cloak : 可以把一开始拿一瞬间的闪给去掉。 样式 { display : none; }

```
v-for :  当 数组内的内容改便是并不会触发 DOM的 值得改变
         当 数组添加， 或删除 子项是， 就会触发 值得改变

### 特殊的属性
class 和 style  是个存在多个值得属性， "  f d a"   {} ， 可以是 []数组， json 
    所有 class 和 style 的特殊写法 : 支持 数组和 对象的写法, 加上本身的字符串写法。 
    :class='["box", "name"]'  数组语法。 
    :class= '{ box : true, name : false }' ,  true 则类添加， false 则 类remove


数据变化 驱动视图 ( Vue实例控制的页面 ) 变化  :  **响应式** ; 还未明白 。 
vm.  ....  回去调试一下看看。 

表达式 ： 单个操作数，或加操作符  |  如 1+1 就是表达式 ， 函数调用表达式(就是一定会有返回值)。 函数调用也是一个表达式。 
> 表达式都会有 放回结果。 
    1 : 原始表达式 ： 单个参量
    2 ： 复合表达式 ： 原始表达式 + 操作符；   

```js 
var vm = new Vue({
    el : '',                   绑定的视图标签 / (el 选择器)第一个
    data : {  name: '' }       数据集， 所有的数据都在这里。 data 内的数据默认都是响应式的。 数据变化驱动视图变化。
    methods : {  fn(){} }      所有的自定义函数包括 事件绑定的函数。  
    computed : { get  set}              计算属性    // getter    setter
    watch : {}                 侦听属性
})

data 和 methods ： 会添加到 Vue 实例的属性中。 
```
### 响应式
> 实现条件：  1 视图要绑定数据{{ data }}  2 这个数据必须要有监听。 vue 中有默认的监听和 watch 和 computed 可以监听
    a. 有 data 
    b. 这个data 必须插入到视图里。

什么情况下 ： 数据变化视图不会变化 ？？？ 
> 绑定原理： vue 初始化 会绑定数据的 监听。 每次视图刷新会重新 检测新的数据， 添加绑定。
> 不同的数据类型的绑定 ：  基本数据类型是立马绑定。  Object 的是绑定自身和自身的属性，Array 只绑定自身里面Obect的**属性 deep**  Array 的第一层是都不会绑定的。 
> 会改变数据的 方法有 ：  push pop unshift splice(返回数组)  sort reverse

- 故 ：1  新添加的，之前没有绑定到的   2 添加了，但是视图没有刷新的  3 数组的第一层数据的下标改变   
上边的 3点都会导致 数据刷新而 视图没有刷星的。本质是数据有没有添加监听。 get set.



### Vue 事件处理
`<input type="button" :value="name" @click="fn( $event, param )">`;
    $event ： 是Vue 传事件对象的固定写法。 特殊变量


### 三步走

1 什么是原型
    一个类的特有属性的集合
2 什么时候用原型
    需要一次性给多个对象添加 属性和方法是
3 怎么用原型
    instace.prototype.kk = ... 


    prototype.hasOwnPerproty()  是否不存在于原型链，存在自身
arr    in :  arr属性 是否在 原型链上 
    prototype.isPrototypeOf( arr )    :  对象是否 在 另一个的原型链上。 就是说  arr  是否继承于 Object
    instanceof  : 

    getOwnPropertyNames()  某对象是否存在于 某一个对象的的原型链上 。  
    __proto__ : 用来获取一个对象的上一级的原型对象
    
    v-for  选项卡
    http://192.168.4.171/svn/codeAndvideo

##  使用表达式
> 灵活使用 表达式 ， {{  表达式 }}   和  :class= ' data ? "" : "" ' 

```js
{{ number + 1 }}
{{ ok ? 'YES' :  'NO' }}
{{ message.split('').reverse().join('') }}

<div v-bind:id="'list' + id"></div>
```

语句是不能卸载 插值里的 ru  : `{{ var a=1 }}`  `{{ if(ok) {return message } }}`

## 指令
Directive  : 指令是


## 对象语法

```js
<div v-bind:class="{ active : isActive }">    
active 这个者是否存在取决于  isActive这个数据 boolean值
```

?? {{ ...arr }}  里面可以放解构数组吗

## 底层 设置属性和描述 defineProperty  获取对象属性的4 中基本描述 definePropertydescriptor()

当 创建一个新的  vue 实例是 会 添加  data  里面的数据监听 defineProperty 
> 有多少设置多少监听，  没有设置不了
> 当每次 视图更新之后就会 有重新收集依赖这一过程。 watcher
> 数组里面的集合  第一层的简单数据是不会添加监听的， 复杂的数据类型里面的属性才添加监听。 
> 数组的 第一层的所有数据都不会添加监听， 会给复杂类型的属性添加监听并且深度遍历，而这个复杂的数据本身并不会被监听。
> 对象里的属性会添加

-  会 懵逼的地方是 ： 什么时候 会重新再 收集监听 ？？？？  

                     收集依赖    
视图 - >   watcher   <--> data
虚拟节点 -> 生成 


给 data 里的 ： 属性添加监听  getter, setter
data : {
    obj : {},    
    arr : []
}

绑定数据是  `v-model` 双向绑定

统一规律: 就封装

那么  onclick   也类似于 属性监听的 形式一样。 
事件句柄 后面的函数就是事件句柄 ：   obj.onclick = function(){}
> 事件句柄的定义 ： 就是事件触发是要进行的操作。

handler : 事件句柄  (回调函数)   (操作)
watch 自定义的数据监听器。   可以写成 对象和 函数 
: 在数据变化是 希望做一些格外的数就用 watch 选项。 

### watch 和 computed

: 习惯  ->   最好 属性在书写时都写成 字符串。

> handler 是在 watch 里面的。
computed:     如果一个数据依赖别的数据计算得出 都可以用 computed 
```js
// watch 可以监听 data 和 computed 里面的属性。
data : { proper: '' }
watch : {
    proper : function (){} // 直接函数 简写
    "proper" : { // 对象 里面加事件句柄 handler  
        deep: true,  // 深度监听
        immediate : true , // 会立即执行一次，触发一次 数据改变。 
        handler : (newProper, oldProper){  // 会把 proper新改变的值和  proper 旧的值传进来。
        }
    }
}
// 计算属性 computed : 当 price 或 count 变化是 都会出发  tobal. 
// computed 监听的是 tobal ， 当 price 变化是  如何知道？？ 
// 怎么知道是 price 和 count 变化就？？？ 
computed : {  
    tobal(){  // 监听的值是放在这里而不是放在 data 里，  watch 监听的子是放在 data 里的， 差别还有很多
            // tobal 的值是依赖本身的return的值， 在异步函数是不能拿到自身的return 的。 就不能操作异步函数
        return this.price * this.count;  
        // 只有 this 里面的数据才有响应式。 其他的不具备响应监听效果。  如 全局 有个 a 数据
        return a;  // a 是全局数据，会在初始化获取一次， 后续不具备监听效果。 
    }  // 简写, 就是 get 
    // 全写
    tobal : {
        get(){},
        set(newValue){} //(修改set ) 这里的逻辑是 以触发 get函数来达到修改的目的的。 有点麻烦
    }
}
```
**computed** 里面的数据的值由  `getter`  return 出来的。 与 异步函数， 所以不能体现到异步函数中。

computed 与 watch : 有异步操作时... 需要用 watch .
setTimeout... 


obj 里面的 属性也称为 标识符，  标识符不能添加 `.`   "fdfd.fdf"

断句： `;`  函数会自动 在 {};  会自动加个`;`

虚拟节点 ：  通过 js 的 Object对象模拟DOM中的节点。 然后再通个特定的render方法将其渲染成真的DOM节点
为什么 要使用虚拟节点： 
    频繁操作 DOM 

选项： 类如 可供选择的选项， 并不是必须。 



# 实例方法 vm.methods



##  混合选项 `vm.mixins`

> 混合继承。  把实例的公共选线抽离出来。 供别人使用

> 类似于类的继承。  可以类比。







##   vm.$set  手动添加至并添加依赖

> 手动把 data里的数据给 watcher  添加依赖。 , 额外添加 一些。

```js

let vm = new Vue({
  el: "#app",
  data : {
    obj : {}
  },
  created : function(){  // 声明周期的第二个函数,  此时 wacther 要监听的值已经遍历完了， 
    this.$set( this.obj, 'name', 5555 ) // 手动给watcher 添加依赖
  }
})

// 全局 - 静态方法
Vue.set(vm.obj, 'name', 555)


```

## `vm.$emit`  `vm.$on(fn)== @send="getData"` 

> emit : 提交;   **手动触发事件。 主动**

> 不同于组件和 prop，事件名不会被用作一个 JavaScript 变量名或属性名，事件名不存在任何自动化的大小写转换. 

```html
// 绑定事件 是 :send="handle" , 调用 是 $emit 来调用的。
// 绑定的 这个 send 不是methods 或 data 里的， 不能用 驼峰命名来操作。
<div @send="handle"></div>  // 定义了，就默认是框架自己给 当前this 绑定了一个事件。  
this.$emit( '事件名', 传给句柄的值 ) // 在这里调用 send 事件。
this.$on  ( '事件名' ，  事件句柄 )  // on 是绑定一个 事件。和 :send="handle" 是一个样的。



```







### refs  获取DOM : reference 参照， 引用

> Vue 里 用于获取操作 DOM  的方法。 

```html

<div id="app">
  <p id='p' ref="pp">
    
  </p>
</div>

<script>
		var vm = new Vue({
      el : "#app",
      methods : {
        getDom(){
          console.log(this.$refs.pp) // 就是 pp id为 p 的DOM 节点。
        }
      }
    })
</script>

```





# 全局api, 也叫静态方法



## 过滤器  Vue.filter(id, [defined]) 管道符的过滤。

> 在这里的 过滤器是一个 **自定义一种规则**， 去覆盖原数据的显示， 原数据本身没有改变

- 参数
  - `{string} id`
  - `{ Function }  defined`

```html

<div id="app">
	{{ mgs | capitalize }}  <!-- |   管道符, mgs 会把自身作为参数传进来给 capitalize -->
  <!-- capitalize 是 靠 Vue.filter return 的结果来覆盖显示的规则。 -->
</div>

<script>
  //  /\B(?=(\d){3})\b/   \b 是个单词界限。 就是 word 与空格之间。， 断言是判断
	Vue.filter('capitalize', function(){ // 全局的
    if(!value) return ''
    value = value.toString()
    return value.toUppercase();
  })
  
  let vm = new Vue({
    el: "#app",
    data : {
       mgs : 'xiao'
    },
    filters : {
      "capitalize" : function (val){
        	// val 就是  mgs,   靠 return 来拿值
        		 return val.toUpperCase();
      }
    }
  })
</script>

```



> html 名， 属性名 是对大小写不敏感的。 在定义变量是 **不要尝试用大小写来规避 变量冲突**。



## 组件  Vue.component

> 组件是： 可复用的 vue 实例。 且与 `new Vue` 接受相同的 选项。 

> 为什么要用组件 ：   组件  为了模板高效的复用代码。 提高维护效率。

> **每个组件都是一个 Vue 实例。** 都可以定义自己的 data , methods 

>  `new Vue()`   本身也是一个 组件。 而且是一个父组件， 其他全局的或是 在 实例中的私有模板都要挂载则父组件之下。  `new Vue`  也就是所谓的  **`根组件`** 

> **每个组件必须要有且只有一个根标签**， 否则报错。 

### 选项

-   **`data`**  :   在此 必须是以个函数， 保证每个实例的数据都是唯一的。 
-   **`template`**   :   定义模板，  如何用组件？？ 就是写在 template 属性这里。
-   **`props`**  :   通过 props  在实例中接受数据， 用于实例( 父传子的数据共享 )之间的数据通信， 共享。
    -   `props : [ zhi ]`  里面的 zhi 是可以直接 this.zhi  

```js
选项 / 数据 ( this.数据 )
data( 定义数据 )   methods( 方法 )   props( 接受父组件的参数 )  computed( 计算数据 ) /每一个新的。  
propsData( 创建new 实例 )  watch ( 添加侦听 )

选项 / DOM  ( DOM 是与模板有关的 )
el ( 根,挂点 ) ,  template ( 模板 ) , render ( createElement, 构建虚拟节点 ), renderError(没), 
  
生命   ( 生命周期钩子 )
beforeCreate created  beforeMount  mounted  beforeUpdate  updated  
activated( 动态组件的激活 ) deactivated ( 动态组件的冻结 )
beforeDestroy  destroyed( 销毁 )  errorCaptured ( 没, 捕获子组件的错误 )

选项 / 资源  ( 什么是资源 )
directives(没， 自定义指令)  filters( 过滤 )  components( 组件 )  

选项 / 组合  ( 什么是组合 )
parent( 父组件,父实例 )  mixins( 继承, 混入)  extends( 扩展 )  provide / inject ( 主要为高阶插件 )

选项 / 其他 ( 都没见过 )
name delimiters functional model(  ) inheritAttrs  comments 


```



**那可数据是哪个组建的？** ： **写在谁的模板里就是谁的响应数据**， 父组件有模板， 子组件也有模板。 

```html

<div id="app">  // app 是父组件( 根组件 )， 里面的 <test> 是子组件。 
  	
  	父组件向子组件传递参数。 就是在这里宏观新加的， 是为数据源， 然后向 Vue.component 传递数据。    
  	<!-- title="property"  数据源。    {{ title }}:  使用数据   -->
     <test title="property"> {{title}} </test>
  	 <!-- ################## -->
     <test title="" :title=""  v-on:helloWork="log"> </test>   
  <!-- title 对象props ['title'], :title="" 对应 new Vue 里 data { title: '' } -->
     <h1 is="test"></h1>
  		<!-- 常量: is, 变量:  :is ;  用于便于阅读可以加个 <h1 is="test"> 来替换 <test>-->
</div>

<script>
  // title 是与 Vue.component 对应的。
 Vue.component('test', {
        //   data 在此 是  function , 保证返回的是唯一的 引用类型。
        data : function (){
            return {
                count : 0
            }
        },
        template : `<h1 >你是我的眼 肉嘟嘟的小脚丫 {{ title }} 
												<button v-on:click="$emit('helloWork')"></button> 
										<h1>`, // 这是 子组件
   			// button 不能和 h1 同级， 应为 h1 已经是 根组件了。v-for 是不能写在 根元素上面。
        // 向子组件传递 数据。 , 在实例中接受数据， 用于与其他实例共享数据。 
   			// v-on:click="$emit('helloWork')"  是预先给定的 可供 父组件绑定事件的 定义。
   			//  v-on:clice="""
        props : ['title']
    })
  
  // :title 是与 new Vue对应的
    new Vue({
        el : '#app',
      	methods : {
          log: function(){
            console.log('hello work')
          }
        },
      components : {      // 实例的 自定义组件。
        	'componentName' : {
            	template :  `<ul></ul>`
          }
      }
    })
</script>

 
```

###  子传父， 由函数(调用来传递)

> 利用 函数来传递。 父组件把函数传给子组件， 让子组件来调用。 

> <span style="color: red; font-weight: blod;">原理： 只要是函数的调用不是用 call 或bind 的调用的话，   函数的声明在哪里，里面的 this 就指向哪里父级的作用域。 <span style="color: deeppink;">把函数传进子组件中去掉用，来达到 通信的目的    </span>由此可以延伸出其他的 通信方法</span>



```html

<div id="app">
  	<div is="box" :sent="getData" >
     <!-- :sent 等效于 :this.$on('send', getData) --> 
  	</div>
  
</div>

<script>
  
  let box = {
    	template : `<div> <span @click="sendData" ></span> </div>`,
    	data (){
        return { str: '' }
      },
    	props : ['send'],
    	methods : {
        	sendData(){
            this.$emit('sent', this.str); // 提交一个 自定义事件,并调用。 名字叫 `sent` 
          }
      }
  }
  
	let vm = new Vue({
    	el : '#app',
    	data : {
        getChild : ''
      },
    	methods : {
        getData: function( val ){
          this.getChild = val;
        }
      },
    	components : {
        	box : box
      }
  })

</script>

```



#### 兄弟之间的传参

> this 的问题是 在传递的过程中的问题， 往往是在传递中丢失的

```html

<div id="app">
  <div is="box1"></div>
  <div is="box2"></div>
</div>
<script>
	var bus = new Vue();
  var box1 = { 
  	template : `<div id="box1" @click="sendData" >`,  // 点击时触发 手动触发 emit， send事件。
    data (){},
    methods: {
      sendData(){
        bus.$emit( 'send', this.msg ) // 触发 'send' 事件， 并把 this.msg 这个参数传递进去
      }
    }
  };
  var box2 = {
    template : ``,
    data(){},
    // 绑定事件需要自调用， 可以选用 created钩子； 可以自己手动调用， 可以不用钩子。
    created(){
      	// 不能直接给 box1 用 $on 来板顶这个事件。 因为这个函数不存在， 只存在于 真正的Vue实例中
      	// 这时只能借助 new Vue 来做 中间传递器。 
      bus.$on( 'send', (val)=>{
        this.str = val;
      } )  // 用箭头函数 解决 this传递丢失的问题。
    }
  }

</script>

```







###  **`is`**   指令

> 经过测试是  **`is`** 的值不能是原来有的 html 标签名。   还有data 等名词冲突等问题。 



###   `$children`  ,  ` $parent`

> 实例的直接子组件的集合 ； 数组。vm.$children[0]  vm 的第一个子组件模板。

> **this.children,  this.parent**



###  报警  $key

> 有相同父元素的子元素必须有**独特的 key**。重复的 key 会造成渲染错误。



# 生命周期

> 创建时的两大阶段
>
> > 1 处理数据 ：  beforeCreate,  created ； 后 数据绑定以结束
> >
> > 2 处理视图 ：  beforeMount,   Mounted;   处理虚拟节点，  mounted 视图已经挂载了。 



8个阶段 ： 老视图 与 新视图。 

—————   创建    —————

1） beforeCreate  ： 数据监听前,   添加  getter 和 setter 监听。  **数据没更新**

2)    created            ：  数据监听后,  监听和注入,     **数据已更新**

​	render 函数就是生成 虚拟节点的函数， 通个 el | template,   有 template 就是将 template 生成虚拟节点

3) 	beforeMount  ：   过载前   新视图替换老视图 就叫 挂载。   **获取节点验证 $refs**

4) 	mounted 			：  挂载后     新视图已经挂载完了。    **挂载之后才有新视图， 才可以**

—————  运行  ——————  

5)	 beforeUpdate   ： 视图跟新前

6) 	updated             ： 视图跟新后

7) 	beforeDestroy   ：   销毁前

8) 	destroy  			 ：  销毁后

> **什么是生命周期？？**
>
> ​		**在 Vue实例化的过程中的各个阶段触发的函数。**

> 为什么要用生命周期？？ 

### 虚拟节点

> **每次数据变化,vue是先更新这个虚拟节点的相应属性,最后一次性更新到真实节点上.(diff算法)**

虚拟节点 ： 是js 用json对象来模拟的DOM,存在于 内存中， 可以减少DOM 操作的频率。 优化性能。 m

​			其实就是对一个HTML模板的 **“描述”** ， 方方面面的**关系， 内容。** 

当视图更新，先跟新虚拟节点

过程 ： 

​		1 给响应式数据添加数据监听

​		2 将 el 选项所表示的视图转化为虚拟节点

​		3 通过这个虚拟节点生成一个一模一样的真实节点， 再把这个节点赶回el 所在的地方

​		4 

diff 算法： 前后比较， 最小化DOM 操作。 

有个疑惑就是 created 里面 请求 ajax ， created 的 同异步函数的问题。

### 子模板的创建顺序

> 哪个子模板需要先渲染，就先触发哪个组件的生命周期， 就先创建。 

```html
<div id="app">
  <div is="box2"></div>  // 因为box2 是先在视图中渲染， 所以是 box2 先创建， 先触发生命钩子
  <div is="box1"></div>  // box1 是后渲染， 然后就是他要比 box2 后渲染。
</div>
<script>
父组件beforeCreate
父组件created
父组件beforeMount
2子组件beforeCreate
2子组件created
2子组件beforeMount
1子组件beforeCreate
1子组件created
1子组件beforeMount
2子组件mounted
1子组件mounted
父组件mounted

</script>

```

### 视图更新 beforeUpdate, update

> watch 和 update 的区别？？ ？ ， 数据驱动视图， 视图更新
>
> watch 数据更新时触发( 操作数据时 )，  update 视图更新后触发(  操作跟新后的视图时  )。
>
> **`watcher 在监听数据的变化。数据没变就是视图也不会变。`**



<span style="color: red;"> watch 是可以知道是哪个数据更新了。 这个倒是要比 update 要来的实用，因为update 是不是到哪个数据 变化的。  </span>



### destroyed , beforedestroy

> Vue 实例被销毁。  
>
> 什么时候触发??   当 `vm.$destroy()`  函数调用时就会触发 before destroy 和 destroyed
>
> >   销毁后就不会再再有 数据以视图的更新， 但是 : 数据于然存在。 只是数据的变化并不会触发视图的变化

### vm.$nextTick  视图更新后触发
我对 newxtTick 的功能还完全不是很了解。 
> 目的是操作 DOM ;  在数据变化后，视图还没有变化 可以手动调用 nextTick(callback) 函数
> 功能也还没有 很了解。

```js  
this.nextTick( ()=>{} )  // 只触发一次， 用于了解数据的变化
```


### 图片的 Onload, window, XMLHttpRequest

> onload 是可以 给 window ,  XMLHttpRequest,  img  判定。 当 

我终于知道了。 



### 动态组件 , 入口 只有一个标签 `:is`

> 定义 ：  只有一个自定义的标签， 通过切换 is来创建，销毁不同的组件。 

> 动态的组件默认是创建和销毁组件的。  创建组建的 生命周期是不断创建和销毁。

> :is="com"`
>
> data : {  com: box1 || box2 ,  }



### keep-alive 抽象组件， 用于缓存

>  keep-alive : 是一个自定义的标签， 包裹动态组件， 会缓存不活动的缓存, 而不是渲染他。 
>
> <span style="color: red;">keep-alive: 主要用于保留组件状态或避免重新渲染。</span>





### 组件状态

> 1 组件数据
>
> 2 组件视图
>
> 状态管理器VueX( 数据共享的管理 )



### 特有的动态组件声明周期钩子函数  activated

> 触发条件：  当动态组件被缓存时。 

> **`activated ( 激活 )`**     **`deactivated ( 冻结 )`** 



### :key 属性，记得在 v-for 的地方加个 key ,  否则会在模块下会报错

> 在   因为 Vue 是存在复用元素的情况，`<li>`   v-for 不加 `:key` 属性会报警。 **diff :   就地更新 **

**key 者作用： 为了标识元素的不同， 加key来区分： 也就是说： key 应该是放在data 数据里。**



<span style="color: red;">Vue 在更新视图时，为了性能， 会尽可能的**复用元素**。 </span>

: 这句话是什么意思呢？ 如 ：  v-if 和 v-else : 在 切换时，标签类型一样， 标签属性一样，就会复用元素。 





## 渲染模板函数 render

> template 模板最终都是经历 rander 来创建的 。 

```html


<script>
	
  new Vue({
    
    render( createElement ){
      	return createElement( 
        	'div',
          {
            attrs : { class : 'active' },
            on : { click: function(){} },
            style : { background: "red", }
          },
    			[createElement( 'span', {}, "11111" ), createElement('a', {}, [])]
        )
    }
  })
  
</script>

```



##  根组件 

```html


<div id="app"></div>

<script>
	// 是利用 render 来替代 template, 然后 把template 写出去就行了。 
  var App = {
    	template: `
					<div id="#app">
                <div >  {{ msg }} </div>
                <div is="tab2"> </div>
           </div>`,
    	data(){
        return { msg: 'msg' }
      }
  };
  
  var vm = new Vue({
    	el : '#app',
      render : creatElement => creatElement(App),
      // component : { APP : App }
  })
  
</script>


```



脚手架 ： 工作平台



##  v-slot 插槽 ， `<slot>` 父组件把内容分发到子组件就是插槽。 

> 更利于内容分发， 为了不足 is 的不足。 把内容留下来
>
> **把对应的内容分发到相应的位置**

> **为什么会有插槽： ** 我目前的认为是 在子组件添加到父组件里时， 父组件想动态在模板里向子组件投入内容是有点麻烦的。 
>
> <span style="color: blue;font-weifht:bold;">所以插槽的本质是在子组件( 模板 )预先把位置留出来， 让给父模板 动态的把内容投入子组件中。 </span>
>
> ​			slot 本质是个站位符， 把位置留出来让给父组件插入内容

<a href="https://cn.vuejs.org/v2/guide/components-slots.html" >插槽 slot 的文档 </a>



```html
<slot></slot>
<slot name="s1"></slot>
<p slot="name(s1)" >
  
</p>
```



## 选项 directive 自定义指令  directives 

```js

// el 是添加了自定义指令的元素，  binding 是一个对象值{}
Vue.directive( 'background', function(el, binnding){
    el.style.background = binding.value;
} );
//  可以自定以封装一个拖坠指令。 

```



## vuex

> 任意两个组件间数据共享都能使用 vuex. 

k

> 核心概念 ：  **`state `  `strict`  `mutations`  `actions`  `getters`**



**调试中遇到的问题，注意事项: ** 

 **1 mutations 里的函数return 是没有效果的。 外面是拿不到放回值得。 是个回调函数**    

**2  getters 和 state 里的数据是分开的，  mutations 里的函数所拿的参数 是 `state`  选项 **



```html
<div id="app"></div>

<script>
 // do no 
let store = new Vuex.Store({
  	state : { msg : '', count:10, price : 5 },
    strict : true,  // 使用严格模式,  
  // 修改数据的逻辑 也因该写在 这里
  	mutations : {
      setMsg(state, val){  // state 是 state 里的数据。 那不到 getters 监听的数据的。 
       // this.$store.state.msg = this.str
        state.msg = val 
        
      }
    },
  	actions :{
       aSetMsg( store, val ){
         	setTimeout(function(){
             store.commit( 'setMsg', val );
          }, 1000)
       }
    },
   // vuex 中的 计算属性
	  getters : {
       total(state){
          return state.count * state.price;
       }
    }
});
    
  
let box1 = {
  template : ``
  data(){
     return { str: '' }
  },
  // 拿数据必须是放在 computed 里
  // 设置数据是放在 methods 
   methods : {
      setMsg (){
          this.$store.commit( 'setMsg', this.str )
        	// 这里的 this 是 box1 , stroe的挂载点在 vm哪里, 
        	// 经过测试 vm 并不在 box1 的继承链上, Vue 会默认的将 store 挂载在自身和子组件上。 
      }
   }
};
let box2 = {
   template : `{{ msg }}`,
   computed : {
      msg(){
         retuen this.$store.state.msg;
      }
   }
}
  
let vm = new Vue({
  el : 'app',
  components : { box1, box2 }
  store : store  // Vuex 实例的挂载点。 
})
  

</script>

```



### 本地存储,  localStorage,  sessionStorage, cookie

> localStorage,  sessionStoreage, cookie

```js
localStorage.setItem()    getItem('name')
JSON.parse('{}')  JSON.stringify( name ) -> 是在提交时才用转换了。 

```

### FormData  接口提供了表单数据的键值对的构造方式
与
> 经过 FormData 的数据可以 XMLHttpRequest.send()  方法送出。 
```js
var formData = new FromData();
formData.set(name, value);
formData.append(name, value)
formData.delete(name)
formData.entries(name, value); //  enteries 本质是把值变成可以迭代的东西。 
formData.get(name, value)
formData.has(name)
formData.keys(name, value)
```



# 遇到的 Error 





```js
Error in render: "RangeError: Maximum call stack size exceeded" // 追踪尺寸过渡。 最大追踪范围。 

found in

---> <CreateInfo>
       <Anonymous>
computed 中 return 了一个 没有在 data 或其他地方声明的 属性。  范围异常， 就是存在不存在的异常。 
         
-----------------------------------------------------------------------------------------
  
Unknown custom element: <infoTable> - did you register the component correctly? For recursive components, make sure to provide the "name" option.
found in
// 不知道 custom的 定做元素， infoTable , 你有正确地 correctly 注册过 这个组件吗，  
// 递归这个组件， 提供 这个 名字的选项。 
         
  ----------------------------------------------------------------------------
<template v-slot> can only appear at the root level inside the receiving the component
// 这个<template v-slot> 只能在接受组件的根等级里出现。 

--------------------------------------------------------------------------------
Unknown custom element: <router-view> - did you register the component correctly? For recursive components, make sure to provide the "name" option.
不认识的 custom 顾客 元素 <router-view> 你有正确的注册 这个 组件吗？ 
我的翻译： 遍历了一遍 组件的集合， 没有发现 有这个 'name' 名字选项。 
正确的  :  对于 递归组件， 请确保提供 'name' 选项。 
provide 提供  recursive 递归。  make sure 确保。 

解决是 :  vue.use( VueRouter )

----------------------------------------------------------
Do not use built-in or reserved HTML elements as component id: div;
我的翻译 ：   你有使用 已经建立保存的 html 元素名 作为你的组件 id 吗？？  
系统的翻译 ：不要使用内置或保留的HTML元素作为组件id: div
built-in : 内置的
reserved : 保留的

```



## 路由 route ， 单页应用

> 这样切换( 响应 )就会快很多。    切换的不同的组件 。 anchor

> 手机上的APP. 
>
> ​	原生 app  andr 原生软件。 调用原生 系统底层  api .快。 
>
> ​	纯 ： webApp 软件。  完全 web 技术实现的APP.    调用 系统api 就会很慢， 麻烦
>
> ​	混合App :   `highbird` 用原生 web 混合。 ———>     **此时就是单页应用的。** 



插件  ： 

路由重定向。 `redirect`    

路径标签  ： `<router-link to="http://">`   来代替 a 标签， to 来代替 href  填写 路径。

 ```html
<router-link to="/home"> 
<a href="#/home" class="router-link-exact-active router-link-active"> 首页 </a>
-------------------------------------------------------------------------------
<router-link to="{name : 'name'}"></router-link> //  to  name
<a href="#/{ name : 'home' }" class=""> 首页 </a>
  
  // 把配置对象传入 实例。 
let = new VueRouter({
		routers : [
         { 
             path : '/home',
             component : home,
             name : 'home' // 给path 取个名字
         },{}    
		]             
})



 ```

**嵌套路由**

```html

let router = new VueRouter({
		routers : [
				{
					path: `/home`,
					component: home,
					name : 'name',
					children : [{path: '/home/phone', ...  redirect: ''}]
				}
		]
})
```



**router 属性**

<img src="https://s2.ax1x.com/2019/11/08/MV2D3T.png" style="float:left;"  />







## axios  请求 第三方ajax 库。 

> fetch  替代原生的 ajax 方案



## 动态路由

组件永远只有一个， 没有组件被隐藏， 没有组件被

在组件切换，只是在动态改变组件的内容.  



检测路由的跳转： ``

```html

<script>

  // 监听是 getter 和 setter 。 所有的都是基于 这两者。 
  
  watch: {  // watch 是可以监听 this 内的所有的数据的变化的， 只要是 在this内。 
      "$route.path"(){   // "$route" 并不是 路由实例。 
        
      } 
  }
  

</script>

```

## 路由守卫分三个等级
: 误区 ： 路由守卫是在路由的组件中触发的。 并不是在所有的组件中都能够触发。 

1 全局  ( 静态的 ) ： 
	前 ： router.beforeEach(to, from, next)  router.afterEach(to, from, next)
  router = new VueRouter()  是个实例的变量。 
2 独享  (实例化的)  ： 
	new VueRouter{ beforeEnter(),  }
3 组件内的 ( 组件内的 ) ： 
	{ template,  beforeRouteEnter(to, from, next) , beforeRouteUpdate(), beforeRouteLeave() }

  - beforeRouteUpdate 的 触发机制有点问题 , **组件复用时触发**
  - beforeRouteEnter  渲染组件时触发
    - 我的误会是 认为进入这个组件是触发。   真实是渲染该组件时触发。  如果是动态路由 该组件子在第一次渲染时触发。


### 动态路由的 缓存切换 的 监听

>  思路 ： 1 watch 监听this中的值 。  2 ` beforeRouterUpdate `    拦截钩子



```js

```





- **`beforeRouterUpdate( to, form, next )`**

  - `to`    去哪个 path
  - `form`   从哪个path 中来
  - `next()`    是否放行。 此方法不调用是 路由跳转不了的。

    - 触发时机 ： **在当前路由切换到别的路由， 再由别的路由切换到 这个路由时触发。  **

**next 的注意点： next带参数和不带参数是不一样的。带参数会重复触发beforeEach这个钩子。会死循环。** 

- 何时用？ 为什么要用？？

  - 在路由发生改变，且是当前的组件复用时调用。

    

  - 还未明白



## 路由拦截， 当路由跳转且组件跳转时

- **在路由跳转时要做逻辑判断是考虑**
- **`beforeRouterEnter( to, form, next )`**    ： 只在路由创建时触发一次。
  - 触发时机： 在跳转到当前组件前触发。 **当前组件还没有创建** 
  - Enter 里的  `next( callback ) `   的回调函数是要在 当前组件创建完时才触发。 **是最后执行的**   
    - callback( self )  是当前组件的实例。 因为当前组件已创建完了。 
  -  **注意点：**    Enter 钩子的this 是指向` window`的。  



-  **`beforeRouterLeave( to, form, next )`**

  - 逻辑差不多

  

### 全局拦截

- 对所有的组件跳转都有效。 

-  ∫å ß   ∫ µ¬πøπø∆˙©ƒ∫µ   这些字符是 alt + key 大映出来的



-  **`beforeEach( to, form, next )`**  每一个组件的切换
-  **`beforeEach( to, form )`**



## 请求拦截 和 响应拦截

> 用 于 拦截 请求配置项， 和响应的 数据处理

> 

> 这个解决了我之前的 写请求配置的 烦恼

```js
( 拦截的概念是： 类似于流水线的 毛坯 在这个流程 中到某个时刻，某个部门 该为这个毛坯添加，修改点什么。  )
( 那么此时此刻 就只有你可以操做 这个毛坯， 应该就是拦截的最简单的 构建 )
( 根据这个逻辑 return 是不能少的。 因为你放回别人就那不到 这个毛坯 )

// 全局拦截
axios.interceptos.request.use( function(resolve){}, function(reject){} )

axios.interceptos.response.use(  )

// 局部拦截, 写在配置对象里面
axios({
    transformRequest : [ function(data, headers){  return data } ]，
    transformResponse : [ function(data){ return data } ]
})
```


## 在处理数据的注意事项
- this.$router  ： 是 router 的实例
- this.$route   ： 是 当前页面路由的信息

                : 和 路由跳转的信息。
- vuex 和 axios 回来的数据会混淆。 
	- vuex : this.$store.state[ 'data' ]   这个是 vuex 定义共享的的数据
	- axios : .then(function(data){ 
		data.data
	 }) 

- 动态路由的原理： 当锚点变时 当前的 数据变化就好了。 
- 路由的跳转也是一个 异步函数。 因为有过程。




## 请求配置 



```js

// 库的默认值的下一级就是 全局的默认值
const instance = axios.create({     // 这个就是 可的默认值
  baseURL : 'https//api.example.com'
});

// 全局的默认值, 可以先定义好全局的默认值, 在 用私有的覆盖
axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;   // 请求头的 common
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';

// 实例的默认的下一级就是 每次请求的私有
axios( {
   method : 'GET'
} )

```



-  **顺序 ：  axios.create() - >  axios.defaults.baseURL= '全局配置'   ->    axios( { 私自的最高 } ) **


### vue 的 UI 框架
> 在Vue中使用 UI 框架。 

element-ui -> vue 的插件 一般用于移动端
iview  ->  pc 端， 后台管理系统
vux  - > 移动端vue 组件库。 


## 打包的路径问题。 

js内引入图片需要使用 requir 导入。 


## 父组件的视图刷新会不会刷新子组件的视图 ??? 
不会。 如果子组件中的数据没有数据变化就不会刷新 。 updated 钩子就不会触发。 
子的 updated 先触发 后到  父的 updated 再触发。 


专业 ： 
    大学 ( 辅修计算机 ) 
    自动化。 

18年 毕业。 

