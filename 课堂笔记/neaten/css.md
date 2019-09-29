## 路径

- 相对路径
  - ./ 同级
  - ../ 父级 (../../../) 多级父级
- 绝对路径
  - c://
  - fill://c: ... (fill 装满)

## 图形(位图) , 图像 (矢量图)

**位图** : ( 点阵图 )
**点阵图** : ( 几何构建图形 )
**格式** : png jpg(jpeg) svg webg

## 颜色 opacity 不透明度

`color`

- `keyword` 关键词 ( `red` `green` ``)
- rgba(r, g, b, a) : ( 0-255 ), a - alpha 阿尔法
- #16: ff00cc -> ff(红) 00(绿) cc(蓝)

## 度量单位

1. `%`相对父级的百分比
2. `px` 相对物理屏幕分辨率的 1px
3. **rem**(root em) **em**( 相对父级文本的字体的倍数 )
4. `mm,cm ,pt(point)` 物理的绝对单位

## background ( 背景 )

> ps 注意: 当简写时，没有声明到的属性会继承初始值并覆盖之前单独声明的属性。 **故，简写就全部都简写， 单独写就全部都单独写**, <span style="color:green">background : url() repeat rigth top red;<span>

1. `background-color` : transparent(透明)，red
2. `background-image` : url("./image/...")
3. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat"> `background-repeat`</a>: ( repeat,重复平铺 ) x 轴 和 y 轴(双值)
   1. `repeat`(default) `no-repeat` `repeat-x`[x|y] `round(中心环绕)` `space (间隔)`
4. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment">`background-attachment`</a> 依附, 图片随着当前屏幕的变化而如何变化
   1. `scroll(元素)` `fixed(视口)` `local(元素内容)`
5. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size">`background-size`</a> 尺寸，比例，包含， 剪切
   1. width, height, contain(原比例) , cover(拉伸)， %
6. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip">`background-clip`</a> (box,border)
   1. `border-box` `padding-box` `content-box` `content-box` `text`
   2. **盲区**: 以什么对象为标准剪切 **text**
7. `background-origin` : img 的原点(起点)位置
   1. border-box padding-box content-box
8. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-position">`background-position`</a> 位置。
   1. `top right bottom left` (`left 50px top 50px`) `%`
   2. 关键字加 --
9. 简写 : 图片等级高， 颜色等级低. ->(image,repeat,position,color)
   1. background : url() repeat rigth top red;

## border ( 边框 )

1. `border-width`
2. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-style">`border-style`</a>
   1. `none` `dotted` `inset` `dashed solid` `hidden` `groove`
3. `border-color`

- 简写 : border: 1px silid red;

## margin ( 外边框 )

1. 取值 : top bottom rigth left;px
   **外边距合并(margin collapsing 折叠)** - (前)bottom 和 (后)top 会取其大者。
   **外边距塌陷(top)**
   - 父级是个空元素或 .. 子元素 的 margin-top 会把父元素带走。

## padding (内填充)

## text (module 文本样式)

1. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/hanging-punctuation">`hanging-punctuation` 标点符号挂起</a>`first` `last` `force-end` `allow-end`
2. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/hyphens">`hyphens` 断字规则</a> `none` `manual(手控)` `auto`
3. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing">`letter-spacing` 字母间距 </a> `normal` `px` `em` <span style="color:green">( letter 字母，信)<.span>
4. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-wrap">`overflow-wrap` 单词断行</a> `normal` `anywhere` `break-word`
5. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/text-align"> `text-align` 文本水平对齐 </a>
   1. `left right center(左， 右 中)` `justify(两端)` `string` `start end match-parent`
6. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/text-indent">`text-indent` 文字缩进</a> 一般都是首行
   1. `length (px)` ``
7. `text-justify` 修饰 text-align : justify
8. `text-transform` : 文本大小写
   1. `capitalize 单词首字母大` `uppercase` `none` `full-width`
9. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space"> `white-space`</a> 如何处理空白字符。 \n 换行符当空白符处理
   1. `normal (常规)` `no-wrap (不换行)` `pre (连续空白符保留)` `pre-line` `break-spaces (空白符当换行符))`
10. <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/word-break">`word-break`</a>单词内断行
    1. `normal` `break-all` `keep-all` `break-word`
11. `word-spacing` 单词空白符,单词间距

<div style="color:green;font-size:18px;">`text-align:center` `text-indent:length`  `white-space:nowrap`(强制一行) `text-transform:capitalize `(单词首字母大写)</div>
<div style='color:red;'>letter-spacing 字与字的间距，word-spacing 空白符的长度</div>

## css Basic User Interface(基本用户界面)

### box-sizing (盒子模式)

> border-box(诡异模式 width 包括边框) content-box width 内容
> <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing">MDN example</a>

1. box-sizing: content-box; 默认模式
2. box-sizing: border-box; 诡异模式

### caret-color (插入符 就是输入框的光标)

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/caret-color"> MDN address</a>

1. caret-color: color,( red )
2. caret-color: auto | transparent 透明。

### cursor (游标 鼠标样式)

<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/cursor">MDN address 太多了 请点此观看</a>

1. cursor: `help` wait crosshair (十字) `default`

### outline ( 轮廓 ) 与边框相序

> 轮廓与边框的区别： 轮廓不会占 `空间`, 且<span style="color:green">不一定是`矩形`</span>

1. `outline`: `color style width` 颜色， 框的样式 ， 宽度
2. `outline-color` : `color(red , rgba, hsla, currentcolor(与文本色一样))` `invert (颜色反转)` <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/outline-color">MDN address </a>
3. `outline-offset` : length,px <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/outline-offset"> 轮廓偏移 MDN</a>

### resize (设置 元素的可调整大小) 一般用于输入框

1. `resize` : `none (不能调整)` `both` `horizontal 水平` `vertical 垂直`

### text-overflow 发出未显示的内容 `信号`

> 就是 用某些字符标记 省略的字符 ; 并不会强制“溢出”事件的发生,只是标记。

1. text-overflow: `clip` `ellipsis`
2. text-overflow: `string 如 ... abc 等` fade 是啥?

## css Positioning 定义如何将元素绝对定位，和相对定位

> float position display visibity z-index
> bottom left rigth top

### clear

> 指定一个元素是否必须移动(清除浮动后)到在它之前的浮动元素下面
> 就是清除浮动,应用于非浮动元素

1. clear: none , left, right, both,inline-start

### float (浮动)

> 脱离标准文旦流， 脱离的盒子 变成了 `inline-block`

**解决高度丢失**

1. 触发 `BFC` block-leavl formating context
2. `clear` 在最后一个中加入 clear: left;
   **标准的 `clearfix`**

```css
.clearfix:before,
.clearfix:after {
  content: ".";
  width: 0;
  height: 0;
  display: block;
  clear: both;
}
.clearfix {
  zoom: 1;
}
```

### positon 定位

> 脱离标准文档流 display 变成了 inline-block;

1. position: static, relative , absolute, fixed.

静态， 相对自己， 相对父级， 相对 body

### z-index  定位元素 x 轴的优先级。

> z-order(顺序) 决定哪一个元素覆盖在其余元素的上方显示

1. z-index : integer(整数) 负数，正数

## display 和 visibility
> display 指定了元素的显示类型, 取值有 out死的 inside listitem..

1) display:none 渲染引擎不会渲染。
**outside 外部样式 标准流的样式**
1) display: block, inline;
**inside 外部样式 标准流的样式**
> flow flow-root table flex  grid ruby
1) display: flow(流式布局) , table, flex, grid,ruby.

**legacy 遗产**
1) display : inline-block, inline-grid

#### visibility
> 影藏元素，而不更改 布局

1) visibility : visible, hidden, collapse(表格中).
#### visibility : hidden 和 display: none; 
> display: none; 渲染引擎不渲染
> visibility : hidden . 只是隐藏。


## FBC block formatting context

> `FBC` 是另外一种**独立**的渲染机制， 规定了内部 block-level box 如何布局，并且 与 外部毫无关系。可以解决 外边距合并，塌陷。浮动高度丢失等问题。

**如何触发?**

1. float
2. overflow:hidden;
3. display:
   1. table-cell ,table-caption, inline-block,
4. position : absolute;

**外边距重合 塌陷**

> 是浏览器理解错了。
> 思路是: 不在同一个 BFC 就行。

## overflow 


> 定义当一个元素的内容太大而无法适应 BFC 时，该做什么。
> <a href="https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow">MDN 查看</a>

1. overflow : visible;
2. overflow : hidden;
3. overflow : scroll; 滚动条
4. overflow : auto; 滚动条

## opacity 属于 color
> 不透明度 0-1

1) opacity: .5;
**兼容 filter 0-100**
1) `filter`: `alpha(opacity=50)`

## 一些规则

1) h1 一个页面只用一次
2) p 标签内不能嵌套别的块级标签
3) 

## 特殊字符，实体字符
- & `&amp;` `&deg; 摄氏度` 
- 正负号 `&plusmn;`
- 乘号 `&times;`
- 人民币 `&yen;`
- `divide` `&sup2;` `&sup3;`
- `&emsp;` 与 字体大小的有关