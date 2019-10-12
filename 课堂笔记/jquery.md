由繁入简易， 由简入繁难
js : 布朗登爱奇

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
- `$().html()`  -> 修改 内容
- `$().text()` ->  innerText:   textContent(火狐,旧) 
- `$().css()`  -> 修改样式
  - hidd() show() === css('display' 'none | block')
- `$().eq()` -> 过滤选择器  eq 等于的
- `$().get(index)`
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
- `removeClass(pa)` : 全部 或 pa    className = '' , ''.includes(pa), replace(' '+pa, '')
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
  - param1 : 时间， 有过渡，slow 600ms normal 400ms  fast 200ms
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

封装思想 :  单一性。
