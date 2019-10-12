- 字节(Byte)是计量单位，表示数据量多少，是计算机存储容量的计量单位。一个字节占 8 位。

- 字符(Character)计算机中使用的文字和符号，比如'A'、'B'、'\$'、'&'等。
- 英文标点占一个字节，中文标点占两个字节

# inherit line

```
  EventTarget ->    Node   -> element -> HTMLElement(任何html元素)  ↓
                           -> document (document.nodeType:9)     document.documentElement 
                           -> Attr
  (Event() 创建事件)Event  -> UIEvent ->  MouseEvent (给事件触发的元素的回调函数作为参数)
                    ->  FocusEvent 
                    ->  InputEvent
                    ->  KeyboardEvent
                    ->  MouseScrollEvent
                    ->  MouseWheelEven
                    ->  ProgressEvent       

```
**Eventtarget**: 只有方法 ->  `addEventListener()` `removeEventListener` `dispatchEvent 给this分发一个事件(Event() 创建事件)`

**Node** : 
- `childNodes` `firstChild` `lastChild` `nextSibling`  `parentElement` `ParentNode`   `outerText` `previousSibling`
- `nodeName` `nodeType` `nodeValue`(text: 本身，attr: 值)

- `appendchild()` `cloneNode()` `insertBefore()`  `removeChild()` `replaceChild()`  `compareDocumentPosition()`
- `contains() 是否后代` `hasChildNodes()` `` 

**Element**  : document.documentElement, head , body
element.nodeType = 1  ;  TagName, attr, opening tag , enclosed text content
-  `attributes (属性集合)`  `children` `classList (className 的集合)`  `childElementCount` `accessKey`
-  `clientHeight,Width, Top, Left`, `scrollTop,Width`

**HTMLElement** ： 任何element 
- `offsetTop,Width`

**Event** ： 
- `bubbles` `cancelable` `currentTarget (事件绑定的元素)` `target (事件触发的元素)` `eventPhase` `type`
- `createEvent(type)`  `preventDefault() (阻止浏览器的默认行为)` `stopImmediatePropagation() (阻止冒泡，并阻止哦同类,addE..)` `stopPropagation (阻止冒泡)`

**MouseEvent** : 事件回调函数的参数。
- clientX, clientY : 当前与 可视body
- pageX, pageY : 整个body 
- screenX, screenY : 整个电脑屏幕
- `movementX` `movementY` (mousemove : 当前鼠标位置以上一次鼠标位置的差) currentEvent.screenX - previousEvent.screenX
![区别图](https://upload-images.jianshu.io/upload_images/18309556-28894242eac88b58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


|    | window | Eventtarget | Node | element | document | Attr | HTMLElement |
| --- | ------ | ----------- | ---- | ------- | -------- | ---- | ----------- |


# Attr

- 全局属性
- tabindex (-1,32767)

## 操作 document

- document.write(''); // 会刷新页面
  - document.open() 打开的文档流（document stream）。

# document

## 获取标签

> 每个标签都是一个对象(element)

- `document.getElementById();// return element || null`
- `document.getElementsByClassName(names)`
- `var elements = document.getElementsByTagName(tag);`
- `var elements = document.getElementsByName(name);`


# element(标签内容)

## 属性

- `element.innerHTML` 属性， 可以写标签。

## 方法

> 需要一个 element

- `let attribute = element.getAttribute(attributeName);`// return value || null
- `element.setAttribute(name, value);` // return undefined
  - `setAttribute('style', 'color:red');`// 甚至属性值
- `var result = element.hasAttribute(attName);`// return true ,false
- `var result = element.hasAttribute(attName);` // IE 返回 boolean 类型值，其他返回 undefined

# node

- hasChildNodes
-

# event 事件

> 事件本质都是函数。 跟 window 有关的可以不写。

- `window.onload` `on 触发(off 打开) load(加载)`

# window

- `window.onload` `on 触发(off 打开) load(加载)`

# 封装 DOM api, jquery 封装思想

![555379-20160611170932965-1842027079.png](https://upload-images.jianshu.io/upload_images/18309556-ede3a0939d536612.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```javascript
`我的局限性： 以为 myQuery.prototype.init 在后， \
return new myQuery.prototype.init(selector);在前。 \
其实， 真正是 return 是在调用之后才 执行。在 myQuery(), 才真正。`(
  /*
中介者模式， 隐式 中介者。
myQuery： 相当于一个 容器。
反向注入, IoCe (Inverse of Contorll) , 控制反转 的封装思路。
myQuery 用于维护， 添加，修改， 定义
init($) 用于使用， 简介，利于体念。

还有 链式编程 就是 可以不断的 set().get().arr() 出来。    return this; 返回对象{}本身。 {}里包含 set,get,arr
*/

  function() {
    function myQuery(selector) {
      return new myQuery.prototype.init(selector);
    }
    myQuery.prototype = {
      init: function(selector) {},
      xiaoming: function() {}
    };

    myQuery.prototype.init.prototype = myQuery.prototype;

    window.$ = window.myQuert = myQuery;
  }
)();

var newObje = $(); // 这样拿到的就是一个对象。而不只是一个函数
```

[{},{}] 复合 json

# document

document.URL -> 当前页面的 url
document.domain -> 主域名
document.referrer -> 跳转来源
window.Location -> 页面跳转

# window

window.navigator.userAgent;
// => 客户端的 user-Agent
// 判断兼容性。

### 当前可视窗口。

window.innerWidth : 可视窗口的宽度
window.innerHeigth : 可视窗口的高度

### 屏幕

与电脑客户端本机的 (物理显示屏)
screen.Width screen.Heigth
screen.availHeigth screen.availWidth avail (浏览器在显示屏的可用宽高)
screen.colorDepth (色彩深度)
screen.pixelDepth (色彩分辨率) 越高越好

### location (在 浏览器的功能是： 资源，页面，路径有关)网关，端口

location.href : 当前页面路劲(可以取值，也可以赋值)
location.hash : (获取)散列 直接获取当前路劲的锚链接值，(可那值可赋值， 赋值会刷新页面)
location.reload() : (F5) 刷新
location.search : (? 之后的值) 就是 `参数`(可那值可赋值， 赋值会刷新页面)
location.assign() : 接受超链接路径，跳转
location.replace() : 接受超链接路径，跳转
assign 和 replace 的区别 : replace 没有历史记录 hostory。

```javascript
element.onclick = function() {
  location.href = "https://www.baidu.com";
  location.assign("https://www.baidu.com");
  location.replace("https://www.baidu.com");
  location.href = "#anthor";
  var hash = location.hash;
  var search = location.search; // 拿参数列表。
};
```

### history

- back()
  - 背，后
- forward
  - 前
- go(num) 1 : forward, -1 : back ,2,-2

### setTimeout , setInterval, clearTimeout

> 异步函数(事件)是等 主线程完后才加入(线程池, 异步事件队列)，进入监听。
> js 是一个单线程异步事件队列的解释型语言。 队列
> 线程最多 2M
> 队列-> 数据结构 -> 先进先出的数据结构 , sequence(异步哪个先进入就哪个线运行。)

- 单位是 毫秒 (ms)
- var timeId = setTimeout(callback, ms); // 只触发一次
- var timeId = setInterval(callback, ms); // 间隔定时器
- clearTimeout(timeId,); // 移除
- clearTimeInterval(timeId,) // 清除

-

```javascript
function Person() {
  (this.age = 18),
    (this.show = function() {
      setTimeout(
        function() {
          console.log(this);
        }.bind(this),
        0,
        o
      );
    });
}
var per = new Person();
per.show(); // bind 绑定 this.
```

#### 获取页内，引用样式 | 获取样式 | 获取外联样式

obj.currentStyle[attr]; // 低版本的 获取当前渲染的样式
window.getComputeStyle(element[,pseudo])[attr];

- pseudo 伪元素，如果有的化话
- 样的属性

## 事件

> 在目标阶段的事件会触发该元素（即事件目标）上的所有监听器，而不在乎这个监听器到底在注册时》> useCapture 参数值是 true 还是 false。

>

<a href="https://www.w3.org/TR/DOM-Level-3-Events/#event-flow">事件流 查看文档</a>

> 我真正的了解事件的 顺序了， 首先： 触发事件时本身就是 父级先向下传递，
> 到 target 子元素， 传递的过程称"捕获"，
> target 元素再把事件向上'冒泡'
> 与 `useCapture` : Boolean，是否先与子元素触发事件。 true 则先， false 则在后 来理解。

- `onclick` 同类事件会覆盖，而 addEventListener 则不会
- `addEventListener(EventName(type), callback[,useCapture])`

  - `useCapture` : Boolean，是否先与子元素触发事件。 true 则先， false 则 后
  - `callback(e)` : `e : { eventphase : 0,1,2,3 }` 事件阶段
  - 底层的累加叠加事件。"追加事件"
  - 目标阶段
  - 捕获阶段
  - 冒泡阶段

- `attachEvent("onclick",function)` (低版本做兼容性的 addEventListener)
  - 后绑定的先执行。

```javascript
function test(var a = function(){console.log()}){}
console.log(a)

(var a = function(){};)
console.log(a)

```

- `mouseover`: 当前盒子，或当前盒子的子盒子 ，都会触发,(事件冒泡)
- `mouseout` : 当前盒子，或当前盒子的子盒子 ，都会触发, (事件冒泡)
- `mouseenter` : 当前盒子
- `mouseout`: 当前盒子
- `mousemove` : 好东西， 移动 。
- `mousedown` : 按下时 1
- `mouseup` : 松开时 2
- `click `: 完成整个 点击过程。 3 点击事件最后触发。有 两三百毫秒的延迟。

- `keydown`, collback(e){ console.log(e.keyCode) } : 高电平
- `keypress `: 按定时 可以一直显示。 
- `keyup` : 
- `e.keyCode` 可以查看 键对应的 acsii 码表。

KeyboardEvent-》 keyCode
<a href="https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent">KeyboardEvent 键盘对象</a>

- `scroll` 滚动事件 与 `srollTop` 等属性可以用
- `resize` 浏览器窗体改变是触发
- `hashchange` 锚链接改变时触发。**重** **虚拟 dom**
  - -> location.hash
  - 拿到 location.hash ,判断， 创建 innerHTML 虚拟 DOM -> 单页面 操作。
- `contextmenu` : `鼠标的右键事件`上下文菜单
  - `callback(e)` e.preventDefault(), -> 屏蔽浏览器的默认菜单。 prevent (阻止)
  - **右键点击时 触发，覆盖了浏览器本来的 右键菜单栏**
- `dblclick` 双击有间隔

- blur : 可以出来光标的才行。
- focus : 可以出来光标的才行。

- input
- change

## 事件对象 Event

![事件传递](https://upload-images.jianshu.io/upload_images/18309556-3e5cfdb173614a37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
如
<a href="https://developer.mozilla.org/zh-CN/docs/Web/API/MouseEvent/MouseEvent">MouseEvent</a>

- 有 `MouseEvent`
  - (继承于)UIEvent
  - (继承于) Event
- `button` 鼠标的那个按键按下的 0 左键 1 中间 2 右键
- `clientX` `clientY` **页面可视区**的鼠标点击位置
- `pageX` `pageY` **整个页面 包含滚动的 scroll**
- `offsetX` `offsetY` **鼠标距离当前元素原点的位置**
- `screenX` `screenY` **不知是浏览器， 是相对整个屏幕的距离**
- `shiftKey` `altKey` `ctrlKey` **是否按住了 shift,alt,ctrl 键来点击鼠标**

### 阻止事件冒泡,可以事件委托

- stopPropagation 阻止传播
  - cancelBubble (低版本)

### 事件委托 delegate

> 还未明白

本来事件的顺序是捕获-> 传到目标元素(事件) -> 目标元素再将(事件)往上冒泡
委托: 就是 在父元素中监听一次，通过 `target`找到目标事件`AT-TARGET`， 给他赋予动作

- `target` || `srcElement`
  - return Element(元素)

e.preventDefault && e.preventDefault();

```javascript
// 大盒子(父盒子) parent
var parent = document.getElementById('parent');
parent.addEventListener('click',function(e){
  e = e || event;
  var target = e.target || e.srcElement;

  switch (target.id){
    case childoneId: // 孩子标签的 id 属性。
      ...
      break;
    case childtwoId:
      ...
      break;
  }
})
```

## 浏览器默认行为

- 块级， 文本可以拖 动， 图片不能拖动，
- 图片要禁止默认行为。

> 浏览器的页面里自带的操作方式
> 比如 右键默认快捷菜单，图片拖坠

- 禁止浏览器的默认行为
  1. return 在监听的事件函数中 `return false` ,就能 阻止浏览器的默认行为了。
     1. 试过了，不行阻止。
     2. 试过了， 又可以了。
  2. prventDefault 高
  3. returnValue 低
  4. setCapture 超低

流程是 mousedown move up (把 move 事件清除就可以了)

## 一般把定时器绑定为 DOM对象，避免污染。

## 找需求

elementUI 框架。


## nextElementSibling 的模拟

```javascript
(function (arr) {
            arr.forEach(function (item) {
                Object.defineProperty(item, 'NextElementSibling', {
                    configurable: true,
                    enumerable: true,
                    get: function () {
                        var el = this;
                        while (el = el.nextSibling) {  // 这个判断就很有技术了。 有装饰器的原理了。 
                        // 第一次是  el.nextSibling  第二次是 : el.nextSibling.nextSibling 
                            if (el.nodeType === 1) {
                                return el;
                            }
                        }
                        return null;
                    },
                    set: undefined
                });
            });
        })([Element.prototype, CharacterData.prototype]);

```

框架中： 虚拟DOM 就叫 组件。
