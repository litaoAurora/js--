
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

> 区别于 DOM 操作。 是居于 **数据驱动**。
> DOM 操作是 ： 获取节点， 操作节点
> Vue : 不会出现 DOM 的操作。 
构造函数习惯首字母大写。 

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

class 和 style  是个存在多个值得属性， "  f d a"   {} 
    所有 class 和 style 的特殊写法 : 支持 数组和 对象的写法, 加上本身的字符串写法。 
    :class='["box", "name"]'
    :class= '{ box : true, name : false }' ,  true 则类添加， false 则 类remove
```
v-for :  当 数组内的内容改便是并不会触发 DOM的 值得改变
         当 数组添加， 或删除 子项是， 就会触发 值得改变


数据变化 驱动视图 ( Vue实例控制的页面 ) 变化  :  **响应式** ; 还未明白 。 
vm.  ....  回去调试一下看看。 

表达式 ： 单个操作数，或加操作符  |  如 1+1 就是表达式 ， 函数调用表达式(就是一定会有返回值)。 
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
> handler 是在 watch 里面的。
computed:     如果一个数据依赖别的数据计算得出 都可以用 computed 
```js
watch : {
    proper : function (){} // 直接函数 简写
    proper : { // 对象 里面加事件句柄 handler  
        deep: true,  // 深度监听
        immediate : true , // 会立即执行一次， 
        handler : (newVal, oldVal){  // 会把 新改变的值和 旧的值传进来。
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
    }  // 简写, 就是 get
    // 全写
    tobal : {
        get(){},
        set(newValue){} //(修改set ) 这里的逻辑是 以触发 get函数来达到修改的目的的。 有点麻烦
    }
}
```
computed 与 watch : 有异步操作时... 需要用 watch .
setTimeout... 


obj 里面的 属性也称为 标识符，  标识符不能添加 `.`   "fdfd.fdf"

断句： `;`  函数会自动 在 {};  会自动加个`;`

虚拟节点 ：  通过 js 的 Object对象模拟DOM中的节点。 然后再通个特定的render方法将其渲染成真的DOM节点
为什么 要使用虚拟节点： 
    频繁操作 DOM 



