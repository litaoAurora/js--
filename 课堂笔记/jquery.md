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
- `remove()` : 移除this 中的元素。自杀。 
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
  - 获取表单标签的 中的 value . 
- `html()` : innerHTML
  - -》 innerHTML , 获取内容
- `text()` : innerText
  - innerText  获取文本

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

**绑定事件**
addEventListener()  支持捕获，和 绑定
    attachEvent()  不支持捕获
    detachEvent()


**jquery事件** 
> 其实都是调用用一个方法 ： on , 只是我还没有找到
- `mouseover()`  一般的绑定
- `bind()`  jqeury 的事件绑定方式
  - `unbind()`
  - `bind('click mouseover' function (){})`
  - 一次绑定多个
  - `bind({  "click" : function(){}, "mouseover" : function(){}   })`
  - 缺点 ： 无法实行动态绑定， 即 事件委托(利用冒泡原理)， 
- `$(this).delegate(child, 'click',  function(e){})` // delegate 委托。 动态绑定
  - function(){} 中， this =》 child . 
  - `undelegate()` ： 解绑
- `on()`  函数重载了
  - `off( EventType, fn )` : 鼠标解绑, fn 没传则所有
  - param1 : obj , string (此重载)
  - param2 : srcElement , target.
  - param3 : Function  e => e.delegate , e.currentTarget , e.data
- `hover(fn,fn)` : fn1 : 鼠标移上去， fn2 鼠标移出
- 自定义触发 `trigger()` 和 `triggerHandle() 不会触发默认行为。`

```javascript
// 没完
ul.onclick = function(e){
    var e = e || event;
    var target = e.srcElement || e.target; // 兼容性。
    // srcElement 是 target 的别名。 
}
e.delegateTarget
```
**隐式迭代**
**手动遍历**
- `each(funcion(index, item){})` 
- `$.each(arr, function(index, item){})`

**释放$符**
- `var alias = $.noConflict()` : 释放 $ 符， 用 alias 代替。


插件 jquery
jq22.com
**jquery的插件**

- `jqueru.fn.extend(obj)` : init, 实例方法。 
- `jQuery.extend(obj)` :  静态方法， 扩展

**jquery.color.js** : 颜色过渡插件
**jquery.lazyload.js** : 图片懒加载的插件
    : 图片懒加载的原理 -> 

`/^\s+|\s+$/g` : 正则的 | 或应用，还未明白。

前端的 快速标签语法。

# ajax  asynchronous javascript and xml 
// 老师的 根目录 在 ： htdocs . 
> xml  : 扩展标记语言。
内置对象 =》 前后端数据交互。 

<a href="https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/XMLHttpRequest"> async MDN </a>

js : 不是真的异步， 只是在模拟。 

- window : phpstudy   wamp  xamp 
- mac :  mamp ; 

mac : 子代 apache 
`sudo apachectl start/stop` : mac 启动
/Library/WebServer/Documents   默认根目录。 


ftp : 20 , 21 ; "文件传输协议"
http : 80;     ""
https : 443;


```js

if(window.XMLHttpRequest){
    var xhr = new XMLHttpRequest();
}else{
    var xhr = new ActiveXobject('Microsoft.XMLHTTP');
}

// 创建对象
// EventTarget -> XMLHttpRequestEventTarget -> XMLHttpRequest
// IE 6 不支持 这个对象 => ActiveXobject('Microsoft.XMLHTTP'); 兼容。 
var xhr = new XMLHttpRequst();

// get 携带数据 :  ulr+ data.
// pust 携带数据 ： send (data);
xhr.open('get', 'hello.txt'); // 定义表单(method, address, isayscn)
    // address : api/get.php?username=张三&password=125 ;   通过地址携带数据。
xhr.send(); // 发送 操作。 

// 当阶段 发生变化是触发的事件 。 on  ready: 只读  state：声明 change  ：  
xhr.onreadystatechange = function(){

    if(xhr.readState == 4){
        if(xhr.status == 200){
            var data = xhr.responseText;
        }
    }
}
```

- 对象  `var xhr = new XMLHttpRequest()`
- 选择 打开方式，地址(url)，和是否异步   `xhr.open(method, address, isasync [,user][,password])`
  - 设置 post 请求头 ： xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')  ; 设置**编码格式**
- 发送动作 `xhr.send( data )` : data = 'username=xxx&pass=xxx' ;  以后端对应。
- 添加监听事件 `xhr.onreadystatechange = function(){}`
- 阶段  `xhr.readyState == 4 `
- 状态  `xhr.status == 200`
- 响应数据  `var data = xhr.responseText`

url 有长度限制 : 故 get 提交的数据大小有限制
pust : 把数据 放到 form-data 中。 
    理论上可以无限， 但是服务端有限制。 ( 配置 post_max_size=10M )
黑客 ( 技术 工具 sql注入 )

`XMLHttpRequest()` 
    `responseText` ( 文本 ) `responseXML` (  xml ) `responseURL` `responseType`
    `readyState` 0(创建对象) 1(执行send()前) ( 1到2是阻塞 ) 2(数据回来了后) 3(解析数据) 4(解析完成) 
                    阶段， 就是时间段而不是时间点。 
    `onreadystatecheange` : 监听函数 . abort() 打断是就不会触发了
    `timeout` : 设置超时值  timeout = 2000ms;
        单超时时 会触发  `ontimeout = function(){}` 事件
    `upload` => XMLHttpRequestUpload 对象。 这个对象是不透明的, 可以绑定如下事件
        `onloadstart` `onprogress` `onbort` `onerror` `onload` `ontimeout` `onloadent`
方法 ： 
    `abort()` : 终止请求， readyState 状态 变为0， 且不会触发  onreadystatechange 事件
    `getAllResponseHeaders()` 获取所有响应头
    `getResponseHeader( name )` : 获取指定 name 的响应头
    `open()`  : 初始化一个请求
    `send()`
    `setRequestHeader( header, value )` : 设置一个响应头, 一般 push 要指定编码 content-type, 
        header : 
IE 会有中文编码问题 
<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/encodeURI"> MDN </a>

**get 的坑** post 则没有， post本身就有自己的编码， 也不会用url  来请求
`encodeUTI()` 可以将中文编码 %EC `decodeUTI()` 可以解码 
IE 缓存问题 ： 当后端有文件改变是 , 前端会有缓存而不去重新请求。 
缓存的原理是： URL 地址一样。 
可以加个`时间戳`  或是每次加个随机数。

**json 浏览器的内置对象**
github 里面有 json 源码， 可以去看一下
<a href="http://www.json.org/json-zh.html">json 源码 </a>
`JSON()`  
    `parse()` ： 解析
    `stringify()` : 转字符串
woe.json 
    严格格式 : 末尾不能有 `,` ; 不能有注释； 要求 {} | [],.


- `ajax({url, data, dataType, })`  => defered 延迟对象。 可以 then . 
  - 
- `$.get(url, {data},  function(){}, [,dataType])` = 》 defered 。 
  - 回调函数可以放在 then 里面。 
  - then 里放回调函数
- `$.post()` 

ajax 轮询
innerHTML  的替换原理。

json : javascript Object notation 
`http://json.org` : 兼容IE 67

```
input:text
```

ajax 的进一步封装
```js

function ajax( options ){

    var defaults = {
        methtod : options.method || 'get', // 给个默认值 'get'
        data : options.data || ''  , 
        url : options.url,
        successd : options.successd || null,
        error : options.error || null,
    }
}
```

## 瀑布流思想。 

: 可视区域的高 + 垂直滚动过的距离 > 最短li的高 + 最短li 距离浏览器顶部的距离。 则 请求。
: 

### 三级联动, 省， 市， 区 查询。 
areas_db 数据库。 
核心 : 
    select 标签的value 值是  被选中的option 的value. 
    value 值改变时 触发 **change** 事件

解除耦合性 ： 依赖没有改变。 优化代码 . 
各个请求中存有依赖。 可以用 premise 模式来 设计。


### 留言系统
userSystem ： sql 
css 

`word-break: break-all;`  单词换行。

`config.php`
192.168.5.149 : 老师的IP
192.168.5.47 

焦点失去触发请求。onblur 
小工具函数
- 注册账户 (验证-后台),  事件用 onblur 焦点失去
  - 1) 验证功能 。 red , green. 
- 登录， post , a是 接口
  - 2） 登录
- 退出 
  - 3) 
  - 展示 注册页面。 
- 留言 : 判断 是 什么标签发过来的。 才能判断是否是留言。 
  - content 你的留言;
  - send  : 

清空 用 input : value ,  innerHTML . 

cookies : 浏览器自动保存 cookies . 
    登录后 ， 刷新 都是由 cookies 来判断。 
    用 cookies 判断 用户是否登陆过， 选择 如何渲染页面首页
        登录过 ： 注册框隐藏， 信息宽展示。 

页面刷新 ： window.location.reload(); 

**获取 cookie**
属性 ： `document.cookie` : 可读可写。 

后端可以跨域， 前端不可以跨域。 浏览器有限制。 

前后端不分离 - 前后端的文件在同一服务器下。 

前后端分离 ： 有两个 - 多 服务器。 
后 ： MVC model view contorl 
前 ： mvvc 

同源策略： 
跨域问题 ： 
1 后端可以设计 允许或不允许跨域 ( 所有或某个IP )
2 nginx 服务器**反向代理** ( nginx是个代理服务器 ) 
    负载均衡， 缓存， 
3 flasg插件( 可以放代码， 制作动画， 不安全。可以携带数据跨域 )，  网页制作。 dreamweaver , 
4 后端脚本代理， 后端是可以跨域的 。 
5 jsonp  , 需要后端配合返回指定数据 ( json with padding  ), json 填充
    利用 script 标签来引入别的网站 的数据， 可以跨域请求数据。
    <script src="..data..">
    <script src="aa.txt">  ```txt  alert('123')```
    后缀扩展名 ： 只是引导 计算机的文本的打开方式。 
    指针问题 ： 桌面的文件只是 指针的删除。 内容还是在的。 
    文件系统， 轨道，自导 ， 打格子。 格子， 磁道 。。。。

6 前端的小技巧 ： 
    postMessage ( window.open(url).postMessage("data", url)  )
    
                ,  iframe , window.domain( 主域名一样， 子域名不一样。  ) 

```js
postMessage ... 利用页面 跳转传输数据
```
百度的接口 ： 
    sp0.baidu.com/

去重 ： 双重循环。