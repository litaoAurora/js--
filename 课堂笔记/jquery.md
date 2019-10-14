由繁入简易， 由简入繁难
js : 布朗登爱奇
封装思想 :  单一性。
nodejs ： 
npm i jquery@1.12.4  ; 在当前目录中 dist 。
    dist - 目录 

min -> 压缩版。  webpark  。 

在head 标签里 
    jQuery 要比 原生的 onload  要快。 并不用 用 window.onload 事件(HTML 和 CSS 样式都加载完才触发。) ：
        window.onload  与 addEventListener('DOMContentloaded')  绑定方式不同。 覆盖与 多个。 
    jquery 是  `DOMContentloaded`( 仅就 HTML 加载完旧触发事件 ) 事件 : 触发时机更早 。 只需内容加载完毕就行了。
    入口函数  $(function(){}) :  - 
             $(document).ready(function(){});  二
```javascript
$(function(){
    $().....
})
// dom 结构加载完之后去触发该函数。 
```
- `$(function(){})` -> 入口函数
- `$().html()`  -> 修改 内容标签内容
- `$().text()` ->  innerText:   textContent(火狐,旧) 
- `$().css()`  -> 修改样式, 获得样式。 
  - hidd() show() === css('display' 'none | block')
- `$().eq()` -> 过滤选择器  eq 等于的
- `$().get(index)`  this 的索引
- `$(ul).children( li )`  ul>li
- `$(ul).find( li )`  ul li
- `$(ul).siblings()`   除了自己的所有兄弟。  li ~ li 只是li之后的li
- `$(ul).next()` 下一个兄弟
- `$(ul).parents()`   所有父级  li ~ li 只是li之后的li
- `$(ul).first()`   -> this[0]
- `$(ul).last()`   -> this[this.length-1]
- `$(ul).eq(3)`   -> this[2]
- `$(),index()` -》 当前元素再父元素中排行老几


事件
- `$().click(function(){})`


添加类, 移除类， 判断是否又类， 切换类
- `addClass`       getElementById('').className += 'classname'
- `removeClass(pa)` : 全部 或 pa    className = '' , ''.includes(pa),  
  - replace(' '+pa, '')
- `hasClass()`  是否有类 length,
- `toggleCLass(pa)` 切换类，  有类就 删， 没有类就加

选择器 
`ul>li:eq(0)` eq-> nth-chlild 
`:odd` `:even`  奇数 偶数 
`:gt` 大于
`:lt` 小于

for(var i=0;i<3;i++){
    oBox.index = 1; // => 借索引
}

动画 jquery 的三种动画 加一个 自定义动画 animate.
- `show(param, param2)` `hidd()` `toggle()` => `display : block, none;` , 改变宽高和透明度。 
  - param1 : 时间， 有过渡，`slow` 600ms `normal` 400ms  `fast` 200ms
  - param2 ：  callback()
- `slideDown(param1,param2)` 划入,滑出 `slideUP() ` 默认是 normal 400ms
  - param1 ： 时间。 param2
- `slideToggle()` 切换
  - 单击划入 或 滑出
- `stop()` , 动画排队问题。 => 原理? ???
- `fadeIn( param )` `fadeOut()` `fadeTaggle()` `fadeTo(time,opacity,cb) ( 到指定透明度 )`  淡入淡出
  - 原理是 ：display: black; opacity: 0-1;  改变的是透明度。
  - param1 : time  ;  param2 ： callback

- `animate({}, speed, curve ,callback)` : 多值动画。
  - {}, 多值， speed 时间 , curve : liner, swing(抛线速度); callback: 回调。
- `stop(param1, param2)` ： 调用一次停止 队列第一个 动画 animate ，
  - param1 : 是否清楚队列 false , 第二个还会执行。 
  - param2 ： 是否跳转到动画的最终效果。false 
- `finish()` : 直接到所有的最终效果

**节点操作**
`createElement()` `appendChild()` `insertBefore()` `cloneNode() true 深度` `createTextNode()` `replaceChild` =>   操作 节点 Node 
`innerHTML += ''` : element 

- `append( $(<div>wode</div>) )` : push 如果是html 里本身的元素，剪切； 虚拟DOM 则添加。 与 token 有关
- `prepend( DOM )` :  unshift
- `after( DOM )` : after 
- `before( DOM )` : previue
- `appendTo()` `prependTo()`
- `html()` : => innerHTML = $().html() + '<div>wde </div>';
- `empty()` 清空子标签标签， 会把元素和事件都清空， 而 html 会把事件的绑定给遗留了， 内存泄漏
- `remove()` : 移除this 中的元素。
- `cloneNode( isEvent )` :     无法克隆事件， 原生还不知道。得看下源码
  - isEvent  ： true 克隆事件

表单的属性 ：  `:disable` `:enable` `:selected ( 已选中的框 ctrl + 左键可以多选 )` `checked ( 已选中的复选框 )` : =>  `checked 或 undefined ` 
可以是 ： 属性， 也可以是 伪类选择器。

箭头函数
回调函数传参 setTimeout(function(){ this.jj },0);
箭头函数 : setTimeout(()=>{ this.jj },0) ;  this继承于上层作用域。
箭头函数的 this 的继承 ； 继承于 定义于的 父级函数作用域。  

getAttribute() ,  setAttribute(), 
- `attr()` : 设置属性， 或获取属性, 不能获取 checked selected disable 的伪类属性选择器。
- `removeAttr()` : 移除属性。 `checked` => `checked undefined` ： 不利于判断
- `prop` : property 获取属性,设置属性。 `chenck` => `true 或 false ` : 利于判断。

`value` `innerHTML` :
- `val()` : value ： input 表单属性， 其他的也可用。
- `html()` : innerHTML
- `text()` : innerText

**表单事件**
`onfocus` 获得焦点  `onblur` 失去焦点 `onchange` value值改变。

**尺寸操作**

`clientWidth`(width + padding - 滚动条) `clientHight` `offsetWidth` `offsetHight` (width + padding + border) `scrollTop`(滚动过的距离) `scrollWidth`


`innerWidth` `outerWidth` `outerWidth(true)`
**可获取尺寸， 可设置**
- `width()` : 获取定义好的宽
- `innerWidth()` : width + padding (设置是改 宽) => 原 clientWidth
- `outerWidth()` : width + paddin border  => offsetWidth
- `outerWidth( true )` : width + padding + border + margin :

`offsetLeft (子盒子距离父盒子的内边框距离)` `offsetTop` `offsetParent`
**操作坐标值**
- `offset({})` : 距离文档 html 的距离 。用offsetTop + 递归 
  - 设置值是就是相对文档的距离 ： 没有position， 就加个相对定位， 相对自己偏移。
- `position()` : 相对有定位距离的位置。 offsetParent 的距离
  - 只能读取， 不能设置。有个坑， 不包括吱声margin 
- `scrollTop()` 原生 : document.documentElement.scrollTop; body.scrollTop

滚动事件一般给 windwo 加 window.onscroll = function (){}
