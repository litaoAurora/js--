- 字节(Byte)是计量单位，表示数据量多少，是计算机存储容量的计量单位。一个字节占 8 位。

- 字符(Character)计算机中使用的文字和符号，比如'A'、'B'、'\$'、'&'等。
- 英文标点占一个字节，中文标点占两个字节

# inherit line

```
  Eventtarget ->    Node   -> element -> HTMLElement(任何html元素)
                           -> document (document.nodeType:9)
                           -> Attr
```

|     | window | Eventtarget | Node | element | document | Attr | HTMLElement |
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
- `var elements = document.getElementsByTagName(name);`

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
