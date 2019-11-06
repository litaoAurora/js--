
## 取余的作用
    - 1000 % 8   取多少的余 就 能得到 多少的范围

## js 插值
```
let name = "jjj";
let p  = `${name}`;
```

## alt 的作用
    - 描述图片，让搜索引擎能识别。

## 路径#
    - 相对路径
        - ./ 当前
        - ../ 父级路径
    - 绝对路劲
        - c://
        - fill://c:

## 图形(位图) ，图像(矢量图)
    - 位图，点阵图（用色彩渲染图形）
    - 矢量图，（几何构建图形）

## html 颜色
    - bgcolor red 
    - rgba(0-255) : 256**3
    - #16 : ff00cc  -> ff(红) 00(绿) cc(蓝)

## 图片是有分辨率的，宽度-> 高度会自动调整。
    - width: height: 会失调。


## 实体字符
    - 转义字符的文字编码  
    - &

## 度量单位
    - % 
    - px 相对物理的 单位
    - rem 
    - mm 绝对单位


## document事件是 html 事件
    - on..

## background:
    - size
    - position : px  %   九宫格  top left right bottom， 偏移量offset 
    - repeat   no-repeat;
    - 颜色 || url()
    - clip() 剪切
    - background: yellow url(...) no-repeat center center ;
    - background-position: 负值是方向， 百分比不用加负号。
    - -(负值->图片移动方向) 负值 是 图片自己 往左 和 往上。
    - 精灵图标。 背景位置

## 路径有特殊符号--> 问题

## 字体 
- 计算机可用字体 -> 控制面板 -> 字体 里面有的才能加载出来。Windows -> fonts
- 浏览器默认大小是16px, 最小是12px. 就是设置 小于12px的不能渲染出来。
- 阿里巴巴矢量图 -> 建项目 -> link -> css 样式 -> class=".@font-face. .图标名. "
- @font-face : 预定义字体。 -> 网络字体 支持网络字体。
- font-family : 
- font-weight: bold 粗细 bolder  small 。
- font-variant : 以小型大写字体 或正常 字体显示。 variant 不同的， 变化的。
- 


## css 选择器
    - 伪类选择器 :hover(鼠标悬停) : visited已 :active(点击时) : link 未
    - div>p 

## 灵活布局 
- **有一些布局 有时为**
- **以在外面再套一个无意义的 盒子。 方便达到效果。**

## 边框属性
- border 
- border-style ： 线形(solid , dashed 虚线) 粗细 bold  solid(线性) 
- border-width ： 粗细bold  px 
- border-color : 颜色
- border-   left top right bottom :  
- radius 倒角 border-top-right-radius:   top left right bottom: px 半径
- radius :一个参数 3px 5px ; 两参 两对角， 三参数 左上1 右上(2)，左下(2) 右下3  四参数. 简写。。。
- radius 的度量单位是从外边框开始的，box 的 border + padding + content 

## 阴影 box-shadow
- 边框阴影
- 盒子阴影
- box-shadow: h-shadow v-shadow blur spread color inset| outset;
- box-shadow : 5px 1px 3px spread #ccc; 整个阴影为对象，将他偏移 水平偏移量 垂直偏移量 模糊度blur 颜色color  spread 尺寸  inset | outset (内外阴影)

## css3 变形
- 平移，旋转，缩放
- transform: translate(x(offset),y(offset)) scale(x(n*100%),y(n\*100%))
- translate rotate scale 
- 旋转-> 3d 与 2d 旋转没有区别。  
- rotate(45deg) ：默认 绕z 周中心点。  rotateX(45deg)  rotateY(45deg)
- rotate3d(0,0,1,45deg) -> 0 | 1 *45deg .
- transform-origin: x-axis y-axis z-axis;   旋转参考点 origin 默认正中央

## 3d 变形 transform 
```
两面翻转核心是：
1. 背面不可见
2. 转变效果保留 -> transform-style: preserver-3d; 
3. 两个盒子定位，并同时转变。 transform:rotateY(180deg);
- 可选 ： perspective: number; 视点。
```
- transform 
- transform-style : flat | preserver-3d   **转变效果**
- perspective  : none | number ;     **视点**
- backface-visibility :  hidden | visible    **背面是否可见**


## css3 过渡(状态)
- 一般 可以度量的 可以过渡 , 或 颜色， 大小  px 
- 核心是 转态的 转变
- 有两种状态， 中间有时间相连     元素从一种样式逐渐改变为另一种的效果。
  - transition简写属性，用于在一个属性中设置四个过渡属性。	3
    - all 表示 hover 中所有设定的样式
    - transition-property规定应用过渡的 CSS 属性的名称。3
    - transition-duration定义过渡效果花费的时间。默认是 0。3
    - transition-timing-function规定过渡效果的时间曲线。默认是 "ease"。3
  - transition-delay规定过渡效果何时开始。默认是 0。

## 版心幅度
    - 一般不会有**水平**的滚动条
    - body 默认超出会有滚动条
    - 版心width   960 1200            <-1366()

## 定位和浮动 
    - 一般脱离文档流 会变成行内块 inline-black 
    - 会变成 inline-block

## 数组 Array()
    - 属性
    - 方法 
        - map() 映射 (fun(i, index , arr), this ) => new Arry()  返回一个新的数组。可以把指针传进去
        - forEach()  (fun(i, index, arr))   = > 不改变常量， 但改变对象。
        - filter
    
        - from(arryLike , mapfn, thisArg) -> 方法从一个类似数组或可迭代对象中创建一个新的，浅拷贝的数组实例。
            - arryLike 来源数组， 映射函数， thisArg 回调函数


## javascript 的函数传参
    1. 位置对应
    2. 可以用 参数解析获取 一个参数中的多个元素
    3. 传多的参数 解析器会 忽略掉。

## 量图软件
    - pxcook 



## canvas api
### 获取，定义
    - HTML中的元素canvas只支持一种原生的图形绘制：矩形。
    - 1. 获取标签 convas -> convas = Document.getElementById();
    - 2. 获取渲染上下文  -> ctx = HTMLCanvasElement.getContext();
    - 3.实际渲染    -> CanvasRendeeringContext2D 接口完成实际绘制。

### 绘制矩形：
    - ctx.fillRect();  // 填充矩形
    - ctx.strokeRect() // 绘制矩形
    - ctx.clearRect()  // 清除矩形

### 路径
- canvasRenderingContext2D ->
- beightPath();   //创建新路径
- closePath();    // 闭合路径， 末端绘画直线到起点，用于填充
- moveTo();   // (抬起) 移动到(x,y)坐标
- lineTo();   // 连接点 (x1,y1,x2,y2)
- arc(x, y, radius, startAngle, endAngle, anticlockwise);   // 向当前路径添加圆弧。单位是弧度=(Math.PI/180)*角度。 pi ,2pi npi 就是弧度
- arcTo()  // 使用给定的控制点和半径向当前路径添加弧，通过直线连接到前一个点。
- ellipse() // 加椭圆弧。
- rect();   // 矩形

### 绘制路径
- fill(); //填充
- stroke(); // 绘制子路径
- 

### 合成(不透明度)
- globalAlpha  : -> 属性， 不透明度
- globalCompositionOperation    ： 全局 合成 操作。 通过 globalAlpha 应用，设置如何在已经存在的位图上绘制图形和图像。


### 线性
- lineWidth : 线的宽度。默认 1.0
- lineCap : 线末端的类型。 允许的值： butt (默认), round, square.
- lineJoin : 定义两线相交拐点的类型。


### 绘制路径流程
    1. 创建起点 -> ctx.beginPath(); -> ctx.moveTo();
    2. 用画布命令画出 路径。 -> ctx.lineTo(); ->
    3. 把路径封闭  -> closePath();
    4. 描边 || 填充 路径渲染出效果。 -> fill(); stroke();


    - ctx.fillStyle='' ; -> 样式
    - ctx.fillRect(10,10,150,100); 形状


## 



 <hr>


## html  超文本
- hyper Text  markup language

## 文本类型 .txt 
- 区分文件类型 <- 决定打来方式

## html 
- 有内容就渲染。
- 不在html 里面也都可以 渲染。
- w3c 只是一个约束 规范。

## head 头 配置信息
- title 
- meta 元信息 配置配置当前网页元数据 <meta charset="utf-8" name="keywords" content="">
  ```charset 自字符集(utf-8 编码格式)  name=  content http-equiv 交互信息  viewport 移动端的像素 ```
- 保存时可以选编码格式
- 注释 - 》 标注解析
- hr br strong好壮，强调  em好斜， i
- 实体字符 `&nbsp;`牛逼视频 -> 空格 `&emsp; `em  space 大空格
- p 段落 : P 标签不能嵌套别的 标签。 准确的说，是不能嵌套块级标签，内联标签还是可以嵌套的。
- &gt; &lt;   <p><A></p> 浏览器会自动-> <p><A></A></p> ;<p>&lt;A&gt;</p>
- 引号 " -》 &quot;
- &copy; 版权信息  -》 特殊字符
- &yen;  人命币 符号 ￥ 
- $ 直接输入
- &nbsp; &emsp; &gt; &lt; &copy; &yen; 

## 标签嵌套规律的基本使用
- 规则：
1. 双标签 闭合
2. 单标签也尽量闭合-》 迎合 xhtml 
3. 双标签 会换行 和 不会 换行的 双标签
4. 单标签一般是功能标签
5. 会换行的双标签 可以嵌套 任何标签
6. 不会换行的 双标签 仅仅可以再起内部 嵌套渲染普通标签 或不会会换行的单标签。行内嵌套行内。


- 标签构成
1. 标签名
2. 标签内容
3. 属性名和属性内容 ： 属性名体现属性功能

```可以自定义标签，自定义属性 但优先识别默认的标签和属性 ```

## img 
- src : source 来源，源头，源文件
- alt : alternate 交替
- width height title  默认是原始宽高的内容(只设置一个时，另一个会自适应)
- 绝对路径： 自己的路径和别人的路径不一样， 一般开发会避免 绝对路径
- 相对路径： 相对自己当前的路径

## 属性与css 样式的区别
- 属性不加单位

## a anchor 
- 
- href : hyper reference , 域名地址 或 路径文件  跳转链接
  ``` http:www.baidu.com ```
- target : 目标， 打开方式 _self _blank 
### 锚链接
- 超链接打开一个新的 页面
- 锚链接 跳转： id(任意位置，任意标签)  name(两个a 标签的跳转) 
- ’#‘ 锚的符号
```
id : identifier  (全局唯一)标识符
href="#id值"
href="#name值"  name="name值" 打开窗口到 iframe 带有name属性的 的方地方。
href="./.....#id" -> 超链接路径 + 锚点
```
- name 属性一般是 表单的 属性

## 列表
- ul (unorder list ) 
- li list item 
- ol order list 
- order 顺序，命令
- <ul type="disc"> type="disc"  列表项属性，  disc实心黑圆   circle 空心圆圈  square 实心黑方块
- <ol type="1"> type="A" 1  a i(罗马数字)
- dl dt dd   定义列表  d definition
- 每一项列表都必须包含一个标题 dt  - > 标题列表
- dl ==> ul ol 
- dt  definition(定义)   title(标题)    dd (内容)
- 

## 表格 table 
- 先有行再有列， 列是把行划分
- row  
- column 
- cell  单元格  单元格合并， 行合并colspan，列合并 rowspan="行数" 合并之后会有多余，
- table 容器标签
- tr   table row 行 
- td   
- border 边框    space 空白 cellspacing 单元格空隙 cellpadding 单元格内填充 width  height 
- style =>  border-collapse:collapse； text-align:center;   collapse : 合并边框，边框折叠
```html
<table border="1" cellspacing="0" cellpadding="10" width="500" height="300">   border 默认0 外边框 最外层的容器，cellspacing单元格空隙  
    <tr colspan="4"> border 默认1 
        <td>性别</td>
        <td>年龄</td>
        <td rowspan="4">
    </tr>
</table>
```

## iframe  内联框架 可以跨域 传递数据
- iframe  inner frame  ： 打开,嵌套另一个页面
- src   html5 仅存属性
- 与a 标签联用,联动，点a 跳到iframe 中   target 链接 iframe 的name 值
```html
<a href="https:www.baidu.com" target="iframeName值">
<iframe src="https:www.baidu,com" name="target" >
```
## form 表单里面的标签样式修改可以借助 label 标签来跳墙

- 可以将 input 或 select 修改 visibility 设置为 hidden 
  - 用 `label` 来修改 表单 radio CheckBox 的选中样式。

## form 表单
> 单就标签来说 就只有 form 标签可以和后台 交互
- `method` : `get` `post `
- `action`  : 表单提交地址
  ```  <form method="get" action="http:www....">```
- post不限大小,数据隐藏到报文中form data 。  get 2kb ,数据拼接到url 中 ，get 提交速度快
- 
> form 里面的表单控件标签 
```html
type ：  
    text password  redio单选  checkbox 多选   
name : name值
value :  value 值， 可以不写
size : 框的长度
maxlength ： 限制内容**字符**的最大长度； maxlength="4"
```
> 设置单选按钮时 需要设置统一的 name 值 给与分组。
- checked=checked;   设置一开始时默认值， 当 属性名和属性值相同时 属性值可以忽略不写
  - checked -> 选中是 true, 没选是 false .
```html
<input type="radio" name="1" value="man" >
<input type="radio" name="1" value="women" >
```
> 选择按钮的name="wodd" ； 都为 wodd 的 为一组
> ``` name 作为分组用 ```

###下拉菜单select

```html
<form>
  <select name="city"> 
    <option value="shanhai">上海</option> //  :selected 伪类选择器。
    <option value="guangzhou">广州</option>
  </select>
</form>
<!-- &city=shanhai-->
```

### 多行文本框 textarea

- `rows `: number
- `cols` : number

```html
<form>
  <textarea style="vertical-align:top;" rows="8" cols="50">
  
  </textarea>
  <select>
    按钮
  </select>
</form>
<!-- textarea 行内块  vertical-align 只作用在行内块 -->
```

### 表单按钮-多种

```html
1. <button>按钮</button> 
2. <input type="button">   <!-- 仅仅给 js 用, 最没用， 其他的都是提交表单-->
3. <input type="submit" >
4. <input type="reset">  <!--  重置 初始值 -->
5. <input type="image"> src="./.." alt  <!-- -->
```

### 上传文件 file

- 文件与表单，**一旦有file 上传标签  提交方法必须method -> post , 并且要设置 enctype 属性 将文件分块上传 **

```html
<form enctype="multipart/form-data" multiple>
  <input type="file" enctype accept capture >
</form>
```

**`enctype`=`multipart/form-data` 分割表单数据进行提交，服务端程序一点一点接受处理**

`enctye`可能是个传输编码协议 (应该是编码格式)  enc -> encoding
> enctype ： MIME编码，设置表单传输的编码。, 1. appliction/x-www-form-urlencoded 2. multipart/form-data 3. text/plain ； 

`multiple` = multiple   : 可以多选文件上传, form 默认值能上传一个 、 **pc 端 ctrl 可以多选**
`multiple` : multiple 是否可以多选

`accept`="image/*,audio/mp3, video/mp4"  :”image/jpeg“  允许接受文件类型。jpg=> jpeg, 没有 jpg 类型

`placeholder` : 站位符

> image/* : 图片的所有类型。 文件没有jpg 的类型 -》 jpeg

`capture`="" :  仅在移动端 调用设备

> `camera` 相机  `microphone` 录音功能

  ### 隐藏域

`input-hidden`

`disabled`  :  是否能用，禁用 `disable 和 nudefined`
表单的属性 ：  `disable` `enable` `selected ( 已选中的框 ctrl + 左键可以多选 )` `checked ( 已选中的复选框 )` 

`readonly` : 只读

### fieldset 

### legend 

### label for 

```html
<form>
  <label for="account"> 账户
  	<input id="account">
  </label>
</form>
```

> 文本关联 for="id值"

## 通用属性的使用方向
- class -> css , js；  一般是给 css 用的
- name ->  form 的 表单控件用的， 给 value 服务的。
- id   ->  js ,css; 常用在 js 中。 css 偶尔用

- h1 -h6  : h标签不能嵌套 其他 h 标签
- p : 标签不能嵌套其他块 选标签。 可以嵌套 行内标签


# css

## 选择器
- 条件 ： 限制结果，或范围；

`name` -> 给form提交数据用的， 给 value 服务的
`class` css
`id` -> javascript 

- `标签选择器` :  ` 一般快速排版 会用于`
- `class` : `.` ; 可以复用 =>list     
- `id` : `# `   ; js 只能拿 最后一个 id值  identify
- `后代` ： 主要针对 场景是当标签嵌套时 ，父标签给 子标签设置样式。 ``` h1 h2{}  空格隔开，权重是 h1 + h2  = 2. 但是h1 不能嵌套 h2```
- `交集` ： `div.class|#id|tag {}   开头必须要 (tag)标签开始`; **用途 : 复用的 class，但是标签不一样时 使用。**
- `并集选择器` ： `div, p, {}`

- 子代选择器 `div>p`
- `相邻选择器` `div+p` (同级选择器,同辈且(仅仅)是自己的下一个)  `div 和 p 在同一级`
- `同辈选择器` `div~div` div 之后的所有 同级div

## 伪类选择器
- a 好像只能触发四个, **普通只能触发 hover**
- `:hover` ; ` 划过触发` `hover 能触发所有的`
- `:link` ;
- `:active` : 
- `:visited` : `visited 只有 color 才能生效， 其他的一切皆无效`
- 顺序 ： ``` 先写 :link(前) :visited(后) :hover(划过) :active() ``` **顺序不能改**

- 目标伪类 `div:target`    : `当div被 # 锚到时触发` `http:www.baidu.com#div`
- 位置伪类
- `li:first-child` `选择li父类的第一个li,父标签第一个子标签必须是 li 才能选择到`
- `li:last-child` `选择li父类的第一个li `
- `li:nth-child(n)`(从第0个开始索引，支持公式) (-n+3)
在使用位置选择器是，最好不要用后代搭配，而是用子代选择器 ul>li:nth-child()

- `li:first-of-type` `父标签下第一个 li 标签` 与 `first-child ` 有本质区别
- `li:nth-of-type(n)`   `li:list-of-type`
- 属性选择器 
- [class] - 选择含有class 属性的标签 [属性名] 
- a[class], .dvi[class] #div1[class]  含有id = div1 和class 的标签
- #div1[class="monkey"]  
- #div1[class*="yao"] class值里面 有 you 的都行
- #div1[class^="首"]  class 里以首开头的
- #div2[class$="尾"]   class 里以尾结尾的
- #div2[class~="class有de"]  class="de" id=div2
- #div[class|="b"]  class="b-ddd"  class里含有b-  的标签
- `::selection`  :鼠标选择文本是的样式。
- `input:disable` : disable : true, false , disable, undefined.
- `input:enable` : enable : true, false , disable, undefined.
- `input:checked` : checked : checked , true, false , undefined.
- `option:selected` : selected : 用于 option 里的 选择。
- `:target` : #样式， 设置锚到的样式。

### 权重 1 - 1000
- 权重, 可以叠加 , **各种选择器的 混用 权重会叠加。** 
  id (100)> class (10)> tap(标签)(1) 

- 标签选择器的权重为0001
- class选择器的权重为0010
- id选择器的权重为0100
- 属性选择器的权重为0010
- 伪类选择器的权重为0010
- 伪元素选择器的权重为0010
- 包含选择器的权重：所包含选择器的权重之和
- 子选择器的权重：所包含选择器的权重之和
- 交集选择器权重为选择器之和
- 继承样式的权重为0000
- 行内样式的权重为1000


### 样式继承
- **只要不影响标准文档流的渲染规则的样式，应该都可以都会继承，影响的则不会继承。**
- 样式的属性有可继承性； true | false
- 样式的属性 可继承性 限制在 标签里面。
- 字体 font 和 文本 text: 和 伪类样式也可以继承 ;  字体里面的属性 和 文本里面的属性 color , 等一些 可以继承
- color : true ; 


## div span 
``` 在实际的网页开发中,会换行的双标签一般有自己的使用规范， 基于 搜索引擎做推广优化(SEO);
规则： h1 是能用一个， h 标签不能嵌套别的 h 标签 。p 标签 不能嵌套 其他会换行的双标签；
故此： w3c 出了 俩 无语义化 标签 div span 
```

## 字体样式
- `size` : 大小 单位 ; ``` 默认 16px 最小识别像素是12px  ```
- font-family: "Microsoft YaHei";`字体family不同， 字体占高也不同` 
  ``` Microsoft Yahei   Arial 英文的在前面 中文字体渲染中文字体， 英文字体渲染英文字体 ```
- font-style: "italic" , `oblique`; ``` 字体样式 风格, 斜体，下滑线等```
- font-weight:  ``` normal 400 bold 678 bolder 900```
- 简写顺序： style -> weight -> size  -> family; ``` font: italic bold 50px "Microsoft Yahei"```
> style 和 weight  有就 添加 ， 当时 size 和 family 要一起出现。
## 文本样式

- text-align : center ;  ` 不会换行的双标签的内容 或 行内块 居中`
- text-indent : 32px;  ` 内容缩进缩进`
- line-height : 32px ; `行高`  ``` font: 32px/33px "微软雅黑"  33px 就是行高```
- text-decoration : none; ` none underline下划线 line-through删除线 overline头顶线 文本装饰 线(liner) `
- `white-space` :` 处理空白符` `normal` `nowrap` `pre-line`(保留换行) `pre-wrap`


## 鼠标样式 cursor 
- `cursor` : `pointer` `default` `wait` `help` `text` `crosshair`

## 背景 background 
- `background-color` :  关键字，transparent(透明)   ;` 背景颜色`
- `background-image` : url("./....");  `默认平铺(就是铺满)，`
- `background-repeat` : `repeat` `no-repeat` `repeat-x|y` ``
> 背景图的（上） 层级 会比 背景颜色高 (下)
>
> - `background-postion` ： 50px 50px ;  `沿着水平方向移动`
- background: 
  url() no-repeat, url() no-repeat, pink;`者个 简写 没有顺序` `简写可以支持多个背景图，仅支持简写`
  ``` 当多个 背景图同时写进来时 颜色 要写在最后 ， 背景图 会压颜色```
- `background-size` : width  height ... cover contain ; `等比， 一个吧`
  ``` background-size : 有两个关键词   cover(覆盖剪切) contain（优先填满一个边，）```
- `background-attachment`(附加在哪里) : `scroll(默认值)` `fixed (固定值))`

## list-style 列表样式
- `list-style-type`:`none` `circle` `square`; `列表符号`
- `list-style-image`:`url("")`
- `list-style-position` : `inside`(图标在内容里面，参与内容布局) `outside`(默认，图标在内容外部，不参与内容布局， 默认是底部对齐)
- `list-style` : 简写

## 标准文档流
> 不会影响布局的属性 可以继承 。 影响布局的 不能继承
>
> - w3c 规定的  块 自上而下 行级块 自左而右 行内块
- 块 ：block， `独占一行， 可以设置宽高, `
  `块级标签的规范`
```html
1. p 标签不能 放置 块级的 标签， 行内块是可以的， 块级的标签会被丢出来渲染。
<P><div></div></p> ==>被转成  <p></P> <div></div><p></p> // 加了个 封口，和开始。
<h1><h2><h2><h1>  ==>被转成   <h1></h1><h2></h2>
2. h 标签不能放入 h 标签 ， 其他的 块级标签可以放。
3. 行标签的 使用规范。    
行标签 不能嵌套 块级的标签， 不会丢出去，但是行标签限制不了块级的标签，块级也不会 在 行标签里渲染 
但是 可以  span{display:block; } 在嵌套
4. 行内的对齐方式 是 以底端对齐， 改了display: inline-block 后 则是 以内容对齐。 
5. display 其实是修改了 浏览器的渲染规则
```
- `verticl-align` : `baseline`(默认的) `sub` `super` `top` `text-top` `middle` `top` `length` `%` `text-bottom`
- 行 : inline  ``
- 行内块 ：inline-block `verticl-align ` 垂直居中值能在设置在 inline-block
- none :
- `verticl-align` : `行内块设置，或同一列内的 对齐方式，只在第一个行内块设置就行了`
```html
verticl-align ： 在第一个行内块设置是与第一个为 参考的
其他的也都可以设置， 但是对齐参考点不一样。
第一个设置 middle 与 第二个 设置 middle 并不一样。， 因为 对起点不同
```


## 盒子模型
- 得自己试一下 inline-block  和 inline 的对齐方式。
- `border` , `margin`, `padding`
- `margin  当前的标签与另外一个标签的距离`


## 隐藏
- display: none;  `完全消失，丢失`
- visibility : hidden; `隐藏可见性`
- 浏览器底层渲染机制 ->  不再渲染display 为none的标签， 还会渲染visibility ，位置还在，当时可见性被隐藏了。



## border 
- `border-width` : 1px;
- `border-style` : solid; `dotted`(点线) `dashed`(虚线) `double`(双层线)
- `border-color` : red;
- `brder-right-style` : 
- `border` : width style color;
- `border-radius` : 10px 20px 30px 40px ; `圆角半径` `值与角对应` `无论是1到4个值都是顺序对应`
- `border-radius` : 10px 10px/10px 20px ; `设置圆心` 左/右 斜线表示水平和垂直

## margin
- 行内元素 不能设置宽高，所以只能 设置 `margin-left` 和 `margin-right` ,
- 高本身就没有所以 不能 设置 `margin-top` 和 `margin-bottom`

## padding  
- 内填充 想调整标签内部的内容 的位置是 可以考虑padding
- padding 在所有的的盒子都能用, padding 应该是没有负值的。
- marging 在行 的 top bottom 会失效。

## text-indent 缩进
- `text-indent` ; 仅仅缩进内容而不影响 盒子布局。
```html
<a>首页<img src="./..."></a>  //  text-indent:9999; 把文字滚出去
```

## 层级 
- 盒子自己视图层级
```
border -> content -> 图片 ->背景-> padding 
```

## box-sizing
- `box-sizing` : `content-box`(默认模式), `border-box`(诡异模式)
- 排版 可以用，可以省去很多计算。
- `content-box` -> `padding+content+border` , 
- `border-box` -> `width+ height`;  其他的 padding border 随便用。

## float 浮动
- 让`块级`脱离标准文档流，在一行渲染显示；  行内，行标签本身就是 从左到右渲染的。
- `浮动不会覆盖内容的显示`。但是 盒子会浮动。
  解决高度丢失
```html
1. 设置宽高
2. BFC 模式触发 overflow 
3. `clear`:`left`,`right`,`both`. 
`clear` 加的位置是 在所有浮动的 最后面加个空盒子，在这个空盒子中加`clear`: `both` 样式
```
`clear`: `clear 属性定义了元素的哪边上不允许出现浮动元素。`


## BFC 块级格式化上文
> 另外一种渲染规则
> **==从左往右，从上到下==**
> 简书的介绍   https://www.jianshu.com/p/828023418450
```
bfc是一个独立的渲染区域，只有block-level box参与，它规定了内部的block-level box如何布局，并且与这个区域外部毫不相干。
    BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之也如此，包括浮动和外边距合并等等，有了这个特性我们布局的时候就不会出现意外情况了。
```
`block formatting context块级格式化上下文`
- float为 left|right
- overflow为 hidden|auto|scroll
- display为 table-cell|table-caption|inline-block
- position为 absolute|fixed
  BFC  特性
- BFC会阻止垂直外边距（margin-top、margin-bottom）折叠
- BFC不会重叠浮动元素
- BFC可以包含浮动
- BFC 盒子从左到右
```
按照BFC的定义，只有同属于一个BFC时，两个元素才有可能发生垂直Margin的重叠，这个包括相邻元素，嵌套元素，只要他们之间没有阻挡(例如边框，非空内容，padding等)就会发生margin重叠。

因此要解决margin重叠问题，只要让它们不在同一个BFC就行了，但是对于两个相邻元素来说，意义不大，没有必要给它们加个外壳，但是对于嵌套元素来说就很有必要了，只要把父元素设为BFC就可以了。这样子元素的margin就不会和父元素的margin发生重叠了。
```

## margin-top 塌陷
就是标准渲染理解错了， bug .
`两个块级的盒子渲染规则一样， 并重叠在一起了，所以渲染出来的是 两个盒子top合并了，是标准文档流的误会处理。`
`要触发 BFC 或  border 或 不让他们合并。`
`加了overflow: hidden 后，外层哈子则进入了BFC模式，外层盒子将自己作为一个独立的块元素处理，不在将内层盒子渲染在了一起。`

## overflow  溢出处理
x,和 y 轴溢出处理： 块 或 行内块的溢出处理。
> 所有标签都有 overflow 样式
- `overflow-x` , `overflow-y` : ...s 
- `visible` : `溢出可见`
- `hidden`  就是修改了超出的渲染规则，BFC ,所以可以出发BFC 改正盒子top 的合并，分开处理。
- `hidden` : `溢出可见性为不可见`
- `scroll` ： `溢出隐藏并加滚动条， 可以滚动展示隐藏的内容， 会给横向 。向加滚动条` `并不常用`
- `auto`  : `那端超出，那端出现滚动条`， `还是比较常用`

## position 定位
- position + margin 配合
> 所有标签都有 postion 样式， 通用样式
- `static` : 默认值 ， 静态的， 不触发定位的值
- `fixed ` : 固定定位. 基于body 定位的。`可以脱离标准文档流， 原本的位置会丢失`
- `absolution` : 绝对定位 `可以脱离标准文档流， 原本的位置会丢失` 
- `relative` : 相对位置 ，相对自己原来的标准文档流的位置来变化的 `并不会脱离标准文档流， 位置还在`
- `值` : `top`:+-px , % ,  `left, right bottom`
  `当 top bottom 同时设置是， top 优先级会更高`
  `left right ， left 会更高`
### 原点坐标
`浏览器左上角， x->(往右) y|(往下) ` `x 轴top 向右， y 轴 left向下` 
`left , top , bottom , right  就是修改坐标的参考轴，设置数值。`


## z-index : position
`z-index 的作用对象是 position： relative , absolution , fixed `
作用是 修改层级等级。仅作用在position 
`z-index`:0-999
index z 轴索引。

## opacity 透明度 0-1
- `visibility(是否可见)` 与 `opacity (透明度)`
- `opacity`(0-1) 是高版本的设置透明度的方法, 低版本则是 `filter: alpha(opacity=50)` (`0-100`)
- `IE 9或以上是高版本。`


## 单位
- `px` : `像素` 
- `em` : `倍数` `相对当前父默认的标签的字体大小`
  `html 默认是 16px，最小字体大小12px` 别的都是 相对`html的` 
- `rem` : `是根据html根节点来计算的`


## xml 数据格式
-xml (Extentsible markup Language 可扩展标记语言)
- 数据存储，传输 Js而 html 是数据的呈现
  html 
```html
<!-- 可以有多个html 根标签-->
doctype html 

```
```
xml 只能有一个根标签,要求严谨，会报错
<?xml version="1.0" encoding="utf-8"?> <!-- 这个声明只能在第一行-->
```
`标签和属性的 都是自定义的`
`encoding utf-8 utf-12 bgk2312 bgk`

区分
- html不区分大小写， xml 严格区分大小写
- html 可以不闭合， xml 一定要闭合

## xhtml


## 浏览器内核
- 渲染引擎 - (引擎) 渲染拼处理 html 核css 的内和引擎
- 解析引擎 预编译核解析 js 
  `从引擎的角度`
  `谷歌， 火狐， 微软IE safari(苹果) opera(欧鹏)`
  wekit 谷歌，欧鹏safari
  Trident IE 

## 补充
- h1 只用一次 SEO 
- p 标签会在上下自动生成 空白
- <font> 以前的版本文本格式化标签
- 文本格式化标签
    - 粗体 ： `strong` : `b`
    - 文本倾斜标签 : `em` : `i`(图标)
    - 删除线 `del` : `s`
    - 下滑线 `ins` : `u`
- 如果是纯英文字母不会自动换行(被认为 是一个英文字母)
- a 标签的技巧 
    - <base target="_blank" /> 定义全局的 a 标签的打开方式 可选
    - <base href="http://www.baidu.com/views"> 基准链接,全局路径, 自动拼接 + a a,,,, 外链不受到影响。
- `letter-spacing` : `可以设置中文字符间距`
- `word-spacing` : `可以设置英文单词之间的间距` `不管中英文只要有空格就可以设置`
### 特殊字符，实体字符
<a href="https://www.cnblogs.com/fml1com/p/5149269.html">实体字符地址</a>

- `\2713` √
- & `&amp;` `&deg; 摄氏度` 
- 正负号 `&plusmn;`
- 乘号 `&times;`
- 人民币 `&yen;`
- `divide` `&sup2;` `&sup3;`
- `&emsp;` 与 字体大小的有关


## 语义化概念：
- 根据内容的结构化(内容语义化)， 选择合适的标签(代码语义化)便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫(搜索引擎优化)和机器很好地解析。
- 好处 -》 主要是推广优化， 可开发维护， 减少差异化。
    1. 没有CSS 的情况下， 页面也能呈现出很好地内容结构，代码结构
    2. 用户体念更好， `title` `alt`(图片) 解析名词或解析图片信息。`label` 标签是表单元素操作更容易。
    3. 有利于SEO ， 和搜索引擎建立良好的沟通，有利于爬取更多的有效信息。
    4. 方便其他设备解析，(如 屏幕阅读器) 以意义的的方式来渲染页面
    5. 方便团队开发和维护，(遵循`w3c` 标准) 减少差异化。

- 表单域要用fieldset标签 包去来， legend 标签说明用途。
- table -> caption thead tbody tfoot 都有时 


## BFC (block Formatting content )



## 弹性盒子 伸缩盒子 dispay: flex;
- `display` : `flex`
- `flex-direction` : `row` `column` `row-reverse` `column-reverse` ``
- `justify-content`(水平布局平铺方式) :  `flex-start`(开始位置水平平铺) `flex-end` `center` `spac-between`(每个子盒子之间均匀分布，左右两边盒子贴着父盒子两边) `space-around`(均匀分布，两边不均匀分布)
- `flex-wrap`(如何包装，是否换行显示) : `no-wrap`  `wrap`

## html5 新增语义化标签-> 突出语义化
- `header` 头部标签， 存放logo 或内容跨度头部标题
- `nav` 
- `section`
- `article`
- `aside`
- `footer`
- `address` :  `存放地址的`

- `blockquote` : 自带首行缩进和 padding
- `pre` : `支持换行和空格显示`





- shift + 右键 cmd 
- ctrl + shift + / 多行注释*


- niconico
  ctrl + z: 
  ctrl + y : 
  ctrl + home 
  ctrl + end 
  shift + Tab 

## vscode 
alt + shift + f  一键快捷键
ctrl + /
alt + b ； 打开当前编辑 在浏览器



- On Windows 　　**Shift + Alt + F**
- On Mac 　　**Shift + Option + F**
- On Ubuntu　　 **Ctrl + Shift + I**


# 长期--作业。
- 产品 - 功能， 接口。。。。
- 


# JavaScript 
- 堆 存储引用类型
- 栈 基本数据类型(Number, Boolean,String)，对象的地址

> `从数据存储方面来说：`
> `栈空间中一般存储基本数据类型，对象的地址；`
> `堆空间一般存放对象本身，block的copy等。`
`堆空间的内存是动态分配的，一般存放对象，并且需要手动释放内存。`
`栈空间的内存是由系统自动分配，一般存放局部变量，比如对象的地址等值，不需要程序员对这块内存进行管理，比如，函数中的局部变量的作用范围（生命周期）就是在调完这个函数之后就结束了。`

## 魔


## 

## 内存与垃圾回收机制
- `程序的运行需要内存`， 只要程序提出要求，操作系统 或 运行时就必须要 供给内存。
- 而持续运行的服务进程， 必要时 及时释放内存，(如果内存占用越来越高 ， 程序会崩溃)

### 内存泄漏
- 不在用到的内存，没有`及时释放`，就叫做`内存泄漏`。

### javascript 垃圾回收机制
- 周期性 (定期回收)
- 标记清除 引用计数-个数为零 则回收。


## 变量
- 变量是内存的基本组成单元。
- 起名规则 : 
1. 要有一定的含义
2. 开头必须是 下划线 英文 和 $ 符才能开头，并且英文首字母小写。
3. 驼峰式命名法
- 推断式变量数据类型。 js 就是由`值`来判断`变量类型`。
- java 等则是(int, char ) 等，声明变量类型。

- `typeof` `typeof()` 运算符来判断数据类型。 但是不准确。
- 真实的 数据类型 用原型来获取
- `Object.prototype.toString.call()`



## 数据类型
#### 数据的坑
- 精度问题
  - 小数 二进制 为 `0011` 的 小数相加， 会无限循环， 精度丢失。 `0.1 + 0.2` ,
    - 解决： `(0.1*100 + 0.2*100)/100`
  - `0` 开头的是一个 (012)八进制数。 而不是一个十进制的数。
  - 科学计数法， (3e + 2 ) 是一个科学计数法



### 基本数据类型 - 8大基本数据类型
- `number` : 小数， 整数， NaN
- `string` , `规范是使用单引号， json 使用双引号`
- `Boolean` :  `true` `false`
- `null` : `null(空对象-> typeof object)` 是会占内存的， 浏览器会为null 专门开辟一个专门的空间
- `Undefined` : 未定义，(内存没有开辟) 
- `BigInt` : 长整数
- `Symbol` : 
- `object` : 引用数据类型。 就是对象， 复杂数据类型。

`null 和 undefined 的区别 : null 内存会开辟空间， undefined 只是声明提升， 而还没有开辟内存空间`
`能够比较的 数据类型 number string boolean  <-  == `
`==` : 会转化 为上三个 基本数据类型比较  如  undefined == null   ==> false == false

#### number 属性和方法
- .toFixed(n);  保留小数位数， 四舍五入。


### 类型转换

- 优先级 与 运算符 有关。 
- + 优先给 字符串。 
- NaN (Not a Number)

- 隐式类型转化(优先级) 
  1. 字符串

- 强制类型转化


### 逻辑运算符的优先级
- ! 到 || 到 && 
`先运算 ! 再 运算 && 最后 || `

`() -> 算术 -> 比较 -> 逻辑 `


## 代码规范
`let variable = null;` : 尽量不要定义变量undefined ，最好要赋个 null 值。

## 判断语句
- if else
```javascript
if(condition){
  
}else if{

}else{}
// condition 语句=>true,false  () 
```
`同一个if else 语句只执行一次， 故此要有逻辑性`
- Number.isNaN() ; 
> 我的理解是 每个NaN 都相当于python 一个类的不同实例， 故此， NaN 不等于NaN.

- switch case break default;
```javascript
switch(num){
  case num1:
    statement 
    break;
  case num2:
    statement
    break;
  default :
    break;
}
```
- if else 和 switch case 的区别。区间范围型(if else) 和 单值型(首选switch)。

## 循环语句
- while(condition){  循环体  };
- do{ `循环体` }whilt( `condition` ) ; 先执行一次

- for(;;){} // 死循环。
`for(statement variable; condition ; statement black)`: `for (global var)的 括号里面是可以拿到外面的 变量的。`
`for(var i,n ; i< number; i++, n--)) 可以定义 多个变量， 多个语句块`

- `break` : 终止，跳出；`continue`: 继续;(`结束当前的循环语句的本次迭代，并继续执行循环的下一次迭代。`),就是continue 之后的代码本次不执行。
```javascript
for(var value of [1,2,3,4,]){
  console.log(value);
}// 1 2 3 4 
```

- prompt(''); 确定是 '', 取消是 null.

## 断点调试
- add folder to the workspace
- 按步调试
- 按行调试

## 数组
- [,1]  第0个 -> undefined

`在javascript 中 没有值得， 肯定没有开内存空间，肯定是undefined`
### 方法
- `sort()` =》 每个索引的第一个字符作为排序参照， 没什么用
- `push(variable)` => 推入，追加 => 取代方法 `arr[arr.length] = "ff"`
- `pop()` => 弹出， 推出数组的最后一个元素。  `delete arr[arr.length]`


## 作用域 

- {var a = 'a'; let b = 'b';}
  - 不能限制 var 声明的变量， 但是能挡住 let 的。
```javascript
{var a = 'a'; let b = 'b';}
console.log(a,b);  // 'a' ReferenceError: b is not defined.

for(var i=0; i<5; i++){
  var num4 = 4;
}
console.log(num4, i);
for(let i=0; i<5; i++){
  let num4 = 4;
}
console.log(num4, i);
// 循环语句没有 作用域限制。
function test(){
  var te = 'ff';
  n = 'n';
  console.log(te)
}
test(); // 'ff'
console.log(te); // ReferenceError: te is a not defined;
console.log(n); //n 
// n 在外部没有声明， 自动归到window 里。

var a = 1;
b = 2;
let c = 'c'; // 局部变量， 不挂载在window中，全局变量只是不再作为全局对象的属性而存在了，但是依然在全局作用域中。
// 挂载在 script 中
console.log(window.a); // 1
console.log(window.b); // 2
console.log(window.c); // undefined 
```
> 函数有独立的作用域， 能进不能出。 return -> 

==let 全局变量只是不再作为全局对象的属性而存在了，但是依然在全局作用域中。在 scope 域中==

```javascript
const a = 123; debugger  // => scope : a
var b = 1245; debugger
let c = 1233565; debugger // => [[Scope]] : a c

function abcd(kk) {
    console.log(a);  // abcd函数的作用域能访问到a
    arguments[0] = 'ff';
    console.log(arguments);
};
dir(abcd);

```
![scope](https://img-blog.csdn.net/20180928173335609?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L05FVkVSX1dC/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## Array 类型转换

- Array.from(arguments);

## iterator 迭代器
`string` `伪数组` `数组` 
`String、Array、TypedArray、Map 和 Set `
`在低层都是继承了 iterator 对象`
```javascript
迭代器是通过使用 next() 方法实现 Iterator protocol 的任何一个对象，该方法返回具有两个属性的对象： value，这是序列中的 next 值；和 done ，如果已经迭代到序列中的最后一个值，则它为 true 。如果 value 和 done 一起存在，则它是迭代器的返回值。
for(var value of [1,2,3,4,]){

  console.log(value);
}
for(let value1 of [1,2,3,4,]){

  console.log(value1);
}
console.log(value1); // ReferenceError : value1 is not defined;
```

## 集合 Set
- new Set();
- new Set().add();
- new Set().has();
- new Set().delete(); // () 只能删除变量指向的 元素， 和单一实体。

## 函数重载
> 函数名一样。 但是函数的参数不一样。 传的参数不一样是调用不一样的函数。
> 前端没有重载， 只有重写。
> 但是有重载的思想。 
```javascript
function reloat(num1,num2,num3){
  switch(arguments.length){
    case 1:
      ();
      break;
    case 2:
      ();
      break;
    case 3:
      ();
      break;
    default:
      ();
      break;
  }
}
let a = new Array(1);
a.prototype

```

## 闭包
- 函数作用域链

## 回调函数
- `callback hell 回调地狱`
- `callback` , 见一个函数作为参数，传到另一个函数中去按需执行的过程。
- 回调函数的短路效验  `func && func()`
```javascript
function (one, two , func){
  let a = one + two;
  func && func(); // 如果func 存在 则调用。
}
```

## 递归
- 函数自己在调用自己
```javascript
var count = 0;
function recursion(count){
  if(count > 10 ){
    console.log('结束了', count);
  }else{
    console.log(count, 'haohaoxiexi');
    count++;
    recursion(count);
    console.log('调用自己之后', count);
  }
}
recursion(count); // 此次只是传入了0 这个字面量
console.log(count); // 0
'----------------'
function func(count){
  count++;
}
let count = 0;
func(count); 
console.log(count); // 0

// 一百之和 递归。
function recursion(n){
  if(n == 100){
    return n;
  }
  console.log(n);
  return n + recursion(n+1);
}
let sum = recursion(0);
console.log(sum)

// 斐波那契数列 1 1 2 3 5 8 13 21 ... 
// 相当于 二叉树  递归下去 都是 1 相加。
function func(n){
  if(n <=2){
    return 1;
  }else{
    return func(n-1) + func(n-2);
  }
}
let nen = func(6); // 第二十个数。
console.log(nen);
```

## 修正
- `作用域`， `参数`
==全局作用域，局部作用域，(参数 <- 变量指向字面量， 对象， 数组)==
```text
如果 变量本身指向字面量
`字面量` ——》 只是把`字面量的值传了进来`
`其他对象` —— 》  把 对象指向地址

```

**函数也是一个对象， 有自己的作用域，在里面定义的变量被这个函数的作用于限制。并不属于这个函数的属性**


## 匿名函数
- 匿名函数在闭包中可以有效的释放内存。
- 在面向对象闭包封装开发时， 用匿名函数保护对象作用域。
- 小括号 ()提高优先， 把匿名函数作为一个独立块。
```javascript
(function(){})(); 

```

## 函数的柯里化(高阶函数)
- 定义：`参数是函数，返回值是函数 二者满足其一。就是高阶函数。`
```javascript
function(func){
  return func;
} // 函数柯里化，=》  装饰器。

```

## 对象
1. 描述信息名词
2. 具象化 (实例化)
1. 特征 (属性， 字段)
2. 行为 (方法)

> 继承， 封装， 多态

```javascript
function con(a,b){
  this.a = a;
  this.fun = function(){console.log('fun')};
}
console.dir(con,);  // f con(a,b)=> arguments, caller, length, nemae, prototype(=>  constructor, __proto__ ),__proto__
// caller -> 在哪个范围内被调用
// arguments => 
let a = new con('f','b');
class con{
  constructor (a){
    this.a = a;
    console.log(this);
  }
  ding(){
    console.log(this);
  }
}

let ne = new con('f');
console.log(ne);
console.log(con.prototype,"com");
console.log(con.__proto__, "con");
class con{
  constructor (a){
    this.a = a;
    console.log(this);
  }

  ding(){
    console.log(this);
  }
}

let ne = new con('f');
console.log(ne);
console.log(con.prototype,"com");
console.log(con.__proto__, "con");
console.log(ne.__proto__, "con");

class ji{

}

```



对象的设置模式

- 单一原则， 一个对象实现一个功能

```javascript
function zhu(){
  this.cpu = '';
  this.graphicsCarad = '';
  
  this.setCpu = function(cpu){
    this.cpu = cpu;
  }
}
let c = new zhu();
// 设置了一个 setCPU 方法来修改里面的值。
// python 来说有私有属性，私有方法，
// js 可以直接在外满修改对象里面的值。


```



## 全局对象 windo

- n

w

`name` = '';





## js 的私有属性间接实现

### 一： 闭包实现

```javascript

function private(){
  var _perp = '';
  this.setPrivate = function(varr){
    _perp = varr;
  }
  this.getPrivate = function(){
    return _perp;
  }
}
let test = new private();
test.setPrivate('f');
test.getPrivate()

function(){
  var name = '';
  var age = 0;
  var gender = '';

  return {
    setName : function(){name = prompt('')},
    getName : function(){return name}
  }
}
// 也是一种闭包，私有属性的 方法。
```



## ` json `  javascript Object Notetion

`new Object` => `json`
- `json` 就是 `new Object()` 的语法糖。
可以直接使用
```javascript
var obj = {
  key : value,
  name : '',
  show : '',

}
// obj 就是json ， 键值对`key-value pair`.
// 键 是值 字符串。

```
## let 声明一个块级作用域
- `所有的块级`
```javascript
for(let i =0; i <5; i++){

}
console.log(i)// Reference is a not defined

let a = 'a';
if(true){
  console.log(a); // ReferenceError ：  a connnt a before initialization
  let a = 'b';
  console.log(a); // b
}
console.log(a); // a
```

## 静态方法,静态方法

- 静态属性和方法只能写在函数的定义外面。
```javascript

function student(){
  this.name = 'hah';
  this.stud = function(){};
  var baba = 'baba';
}
student.a = 'a;'; 
student.endo = function(){ console.log(this.stud,student.a, student.baba)}; //'undefined' this=> student代码块函数本身,。
student.ende = function(){ console.log(this.name,'sfdsf')}; //'student' this=> student代码块函数本身,。
student.endo(); // 静态

```
- 紫色 方法
- 蓝色属性
编辑器


## this 的指向。
- this-> window, this-> obj;
- 静态中， this -> 函数模板，代码本身。

`ECMAScript` 
- 改变 this 指向的方法
- `call() 普通参数`, `bind() `, `apply() 数组`
- 这些方法是封装在 Function中的方法。 所有函数都继承于此对象。 很多对象也都继承于他。
- `bind 与 call() 和 apply() 的区别。 bind 不会马上调用， 而是放回绑定后的函数，再调用。`
```javascript
var a= 'f';
function test(na, zha,yan){
  console.log(na);
  console.log(this);
}
test('na','zha','yan'); // 
test.call(Object, 'na','zha'); // param:() Object(想要改变this指向的参数)
test('na','zha','yan'); // 
test.call(a, 'na','zha'); // String() 


test.apply(Object,['na','zha','yan']); // 数组
let newtest = test.bind(Object,'na','zha','yan');
newtest();
```

## 原型链

++ 
new Array()
function(){}   new Function()
json    new Object()

- 基于原型的面向对象编程语言。
- 一切皆对象， 一切皆函数 Function 
- 所有函数都有一个 `prototype`, 没有 `__proto__`
- 所有的 对象 都有一个 `__proto__`
`所有的__proto__ 都指向 prototype`
- `prototype`, `__proto__`;

- 继承 `inherit`
==先继承,后再添加自己的东西==
==原型链 函数有 `prototype`; new Object()有 `__proto__` new Object()(`__proto__`)指向构造函数(`prototype`)==

```javascript
function Person(name,address){
  this.name = name;
  this.address = address;
}

Person.prototype.show = function(){
  console.log('ddd');
}
var xia = new Person('fd');

Object.prototype.ha = function(){console.log('test')};
var aa = 'fdfdfdsf';
aa.ha(); // 修改原型链


function fun(a,b){
  this.a = a;
  this.b = b;
  this.liu = function(){console.log('fff')};
}
fun.prototype.lll = function(){console.log(this.a)};
let func = new fun('f','ff');
console.log(func, func.__proto__);
console.log(func === func.__proto__);
```

- `继承都是对象之间的继承。 {} 与 {}`
## 继承解耦合
- 子对象仅仅继承 父函数的 prototype(而不是父函数的实例化 `__proto__`)
- 这时需要一个`中间的实例化`来解耦合
==**此方法可以使继承通用化， 任意两个对象之间都可以继承。**==
```javascript
function f1(){
  this.a = 'a';
}
function f2(){
  this.b = 'n';
}
'--------------'
f1.prototype = f2.prototype;
f1.prototype.hh = 'hh';
console.log(f1.prototype,f2.prototype)
'---------------'
f1.prototype = (function(fatherPrototype){
  function midd(){}

  midd.prototype = fatherPrototype;
  return new midd();
})();
// 借助中间函数来 仅仅继承父函数的 prototype ， 而不是父实例`__proto__`

```

### 函数名

- 函数名， 每个函数都有一个函数名。 且这个函数名不能更改。
```javascript


`this.name` => 函数的名字。
`首相是this 的指向函数本身，故 只能是 函数本身.别的函数 this 才指向 函数本身。`
function test(){
  console.log(test.name);
}
test.call(); // 此时 call()方法里的 this 才指向test ， 在 call() 里面 才能 this.name ;
//此时 call()方法里的 this 才指向test ， 在 call() 里面 才能 this.name ;





function na(){

}
```
> 此时 call()方法里的 this 才指向test ， 在 call() 里面 才能 this.name ;

## 引用类型的经典错误理解


```javascript

var obj = {
  a : 'a',
  b : 'b',
}
function test(obj){
  obj.fd = 'fd';
  console.log(obj);
  obj = {
    name : 'name',
    b : 'b',
  }

}
test(obj); console.log(obj); // {a: 'a', b : 'b'}; 
// 看似 外面的 obj 和 里面的 Obj 是一样的。 
// 通过传参 其实里面的obj 变量 和外面的变量,是两个不同的变量，只是两个变量都指向同一个个引用类型。
// 两个变量指向同一个引用类型。 里面的 obj = {name : 'name'}, 只是重新赋值了，重新指向。

function a (){
  console.log(a.name);
  console.log(typeof a)
}
a.jjj = 'fd';
// a.prototype.show = function(){console.log('pp')};
Object.defineProperty(a, name,{
  configurable : false,
  writable : true,
  enumerable : true,
  value : 'name'
});
console.log(a[name]);
console.log(a.jjj);
```
>>>>>>>>> my2.md

快捷键 ： 
ctrl  + shift + d : 向下复制；

div:必须 ,  {} , :  [] ,

站位符的作用： 先占着一个固定的位置， 等你再把值给传进来。 这就是站位符的作用。