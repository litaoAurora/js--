## 媒体查询

> 查询客户端的 屏幕的宽度和高度来做出适配



> 区间的,  等级的
>
> media , rem , flex :   可用于响应式的 三个 技术.
>
> ​	% , rem , em, flex . 
>
> 移动端的适配 :  <meta name="viewport" content="width=device-width">
>
> : 三大块 : 媒体类型 ,  判断端逻辑,  媒体功能 

**重点考虑宽度 width**

本身就是 : ==后面的 会覆盖前面的.== : 注意 条件的顺序. 

```css

@media mediaType and | not |   mediaFeatures 
and 后面要接空格.  and 接多个 功能条件. 
    
 @media screen and (min-width: 992px) and (max-width: 1000px) {
     body{
         background : red;
     }
}
----------------------------------------------
@media screen and (min-width: 768px){
    background-color : green;
}
@media screen and (min-width: 996px){
    body {
        background-color: red;
    }
}
```

#### 媒体类型 mediaType

**screen**  : 屏幕

**all**  : 所有

**print**  : 打印机

**speech**  : 读屏设备

沉淀下来的只有这几个了. 



`white-space: nowrap;`  : 空白空间不换行. no wrap : 包扎, 转弯, => 不转弯 => 不换行

**表格快捷键 : Ctrl   + t**

| 超小屏 | 小屏  | 中等屏幕 | 大屏  |
| :----: | :---: | -------- | :---: |
|   xs   |  sm   | md       |  lg   |



#### media Feature  媒体功能

> viewport(视窗) (min-width) ,   设备的宽度与高度(width-device-width) 
>
> 朝向 (横屏, 竖屏)  ,   分辨率    

|                  |                            |                             |
| :--------------: | -------------------------- | --------------------------- |
|    min-width     | 最小值(pc 和 移动)         | 向上兼用,向下覆盖(从小到大) |
|    max-width     | 最大值( document 的宽度)   | 从大到小写.                 |
| min-device-width | 设备的物理宽度; **移动端** |                             |

**device** : 设备; 

**在 link 标签中也可以  用媒体查询 , 不同的媒体 引用不同的样式**

`<link rel="stylesheet" media="mediaType and | not | only (midiaFeature)" href="mystyle.css">`



| condition  关键词 | 描述  description                |
| ----------------- | -------------------------------- |
| not               | 取反 卸载  screen 的前面         |
| and               | 判断多个媒体功能 and (min-wdith) |
| only              |                                  |



<hr>

# bootstrap 拿来主义

> 基于 less ( sass )  预处理脚本, 还不明白. 

css 样式来源于 less文件.   修改 less 文件重新编译 -> dist 文件夹

js  : 

font : 字体图标. 

ie8, ie9 :  还要引入=> Respond.js ( 不能本地打开, 只能 http 来 ). 

`<meta http-equiv="X-UA-Compatible" content="IE-edge">`  最新的IE最新标准

`<meta name="renderer" content="webkit">`  : 只有360浏览器才支持, 当双内核时





## 全局css 样式.

#### 栅格系统





## 组件





## 插件 js







## 如何用

1  配置环境 : `起步` -> `基本模板`

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--[if lt IE 9]>
      <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
      <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>

    <!-- jQuery (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
    <script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
    <!-- 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js"></script>
  </body>
</html>
```







##flex 弹性盒子

> box Alignment : 弹性队列。 



- 主轴，  侧轴

`https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content`

<a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/justify-content">MDN</a>



**方向**

| 容器/ 属性           |       |          |              |                 |     |
| -------------------- | ----- | -------- | ------------ | --------------- | --- |
| **`flex-direction`** | `row` | `column` | `row-revers` | `column-revers` |     |

| 容器/ 对齐方式         |              |            |                |                 |                |
| ---------------------- | ------------ | ---------- | -------------- | --------------- | -------------- |
| **`justify-content:`** | `flex-start` | `flex-end` | `space-around` | `space-between` | `space-evenly` |













**主轴** 

1  ``

**侧轴**

1 `align-items:` `flex-start`   `flex-end`   `flex-center`   `stretch`   ``



**调整主轴方向**

1 `flex-direction:`  `row`  `column ` `row-revers`   `column-revers`



**换行** ： 默认不换行 nowrap

1 `flex-wrap:`  `nowrap`   `wrap`  

**换行之后的排列方式**

1 `align-content:`  `flex-start`  `flex-end`  `center`  `space-between`  `space-around` `stretch`

**单独,  可以覆盖 align-items(侧轴的对齐方式)**

1 `align-self:`  `flex-start`



**缩放比例： 比例份数** : 控制子元素的占比份数。 

1  `flex:1;` `flex:2;` 

t



**子元素的排列顺序**

1 `order:number;`



`rem` `vw`  `vh`  : 适配。 

`cssrem`  : 

`easyless` :   语法



`.less` : 文件

`npm install -g less`  : 全局安装 less 插件。 

​       编译 `lessc style.less > bb.css`  ;   `lessc 路劲文件，less bb.css`

`kaola : 编译css`



hbuider :  前端开发IDE。 `Dcloud 公司` ： 在线云打包。 同个 hbuider软件， 链接 在线云打包



`nodejs : npm install cordova `  命令打包。 



### 多福多寿

逻辑像素点 ：  屏幕尺寸下 允许 的css 像素点。 



**视口**  ： viewport ;   980 1024  移动端。 物理屏幕

`<meta name="viewport" content="width=device-width">`   视口的宽等于 逻辑像素宽





`rem` `vw`  `vh`  : 适配。 

`cssrem`  : 

`easyless` :   语法

`npm install live-server -g` : `nodeJs--live--server` 开启一个本地服务器。 

`.less` : 文件

`npm install -g less`  : 全局安装 less 插件。 

​       编译 `lessc style.less > bb.css`  ;   `lessc 路劲文件，less bb.css`

`kaola : 编译css`

## less 语法

定义变量： 

```less
// 定义变量
@color: red;
@width: 100px;
// 定义一个混合， 混入
.bordered {
  border-top: 3px solid green;
  border-right: 5px dashed pink;
}
// 混合传参
.pre(@style, @val) {
  @{style}: @val;
  -webkit-@{style}: @val;
  -o-@{style}: @val;
  -moz-@{style}: @val;
  -ms-@{style}: @val;

}
// 嵌套
ul {
  width: 100px;
  li {

    a {

    }
  }
}
// 定伪类
ul {
  li {
    a {

      $:hover {
        // 这个是伪类
      }
    }
  }
}

body {
  width: @width;

}
body .cla {
  .bordered() // 调用上面的  .bordered. 
  .pre(width,)
}



```

