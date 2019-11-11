
有个属语表： <a href=" https://developer.mozilla.org/zh-CN/docs/Glossary "> https://developer.mozilla.org/zh-CN/docs/Glossary </a>
# HTML  : 层叠样式表

## 标签结构 elements
> 开始标签 属性 结束标签  内容  --> 元素

标签名： tagName, 
属性  ： attribute , 附加信息，对标签进行， 限制，定义，修改标签的功能或样式。 
内容  ： Enclosed text content, 封闭的内容

## 类型划分

1) 块级元素  : 独自一行
2) 内联元素  : 行内元素，
3) 空元素 : 单标签

: margin 是受两个标签的共同作用的。 `共同影响` 决定自身的是 left 和 top

默认行为， 默认样式。 

## 全局属性
> : 1 基本的全局属性  2 XML: lang 和 XML: base  3 事件处理  如 `onclick`

: XML: lang :  主要语言  <div XML:lang="en">this is a englist
: XML: base  :  给单独的标签设置基本 URL 没有用过

### 基本全局
> 有用的  `class  data-* draggable  contenteditable id title spellcheck`

#### accesskey 生成快捷键方式
> 没有用过

### autocapitalize  自动大小写 *移动
<a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/autocapitalize">https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/autocapitalize</a> 

> 是否自动大小写以及大小写的 模式。 
> pc 端调试过是无效的， 应该是在移动端才有效。 

- value 值 : 
    -  **`off`**  离开， 关闭。 小写
    - **`on`**   开， **句首大写**
    - **`words`**  词首打写
    - **`characters`**  所有大写

### class 
> 是一个空格分离的列表   `className`  `classList`  `getElementsByClassName`;

### contenteditable  内容是否可编辑
> content edit able  ： true， false .
切改变的是 `text` 与 value 无关. 
提问？ 在Vue 中如何实现它 text 的数据双向绑定？？？？ 

### contextmenu 上下文菜单。 浏览器的默认行为事件也叫 contentmenu
> 只有火狐支持， 右键点击时出现

### data-*  自定义数据属性
> HTMLElement 接口可以访问， -> `HTMLElement.dataset`

### dir 文本方向

### draggable  是否可拖动 ,
> 浏览器的默认行为是图片不可拖动， 应该用此属性来修改。

### hidden  可以被 css diaplay 覆盖。 

### id 
### inputmode 
> pc 端看不出来效果。 

### title 
### spellcheck  语法检查
### tabindex   tab键次序
### translate  

# 根元素 `<html>`
> : 所有元素的祖先。 只跟 head  和 body
- 属性 : 
    - xmlns : XML 的命名空间。 

: 命名空间 namespace  名称空间。 ( 分类 )
: 为什么要有命名空间： 为 解决命名冲突，变量 重用 而生。 相当于 **`相同的变量名寄生在不同的对象之下。`**

## 文档元数据
> 元数据 ： metadata -> 包含页面相关信息， 包括样式，脚本，及数据。 -》 SEO 利于优化， 
> 更好地渲染页面 ： pc 和 移动端的 规定差别在于 元数据的差异。 

### `<meta>`

> 接口都是给 js 用的。 ,,  meta 其实是个很复杂的标签。 

**接口：   `HTMLMetaElement`**  ;    EventTarget ->  Node  ->   Element  ->  HTMLElement  -> HTMLMetaElement

<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta#attr-http-equiv"> Meta MDN  说明文档</a>

<a href="https://www.notion.so/meta-8cd558ba52d843058292b5beb485ee1f"> 别人的说明总结 </a>

| perproty         | content        | description                        |
| ---------------- | -------------- | ---------------------------------- |
| **`charset`**    |                |                                    |
| **`content`**    |                |                                    |
| **`name`**       | `viewport` ... |                                    |
| **`http-equiv`** |                | 能改变服务器和用户引擎行为的编译。 |



###  `<link>`  : 外部资源链接元素

> 规定了当前文档与外部资源的关系;    属性也有好多， 

<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/link">link:MDN</a>       其中 rel ->  <a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Link_types" style="color:blue;" >relationship 关系的值</a>

**常用** : 可以引入图标， 可以媒体查询。 

```html
<link rel="icon" href="favicon.ico">
<link href="print.css" rel="stylesheet" media="print">
<link href="mobile.css" rel="stylesheet" media="screen and (max-width: 600px)">
<link href="fancy.css" rel="alternate stylesheet" title="Fancy">  可供替代的样式
```

**目前已知用途:   引入样式， 引入图标， 媒体查询来引入不同的 样式**

### `<title>` 标题



## 分区根元素

###  `<body>`

> js : `document.body` 可以快捷访问

<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body"> body descriptor</a>

> 其中可以有少的事件是可以给body绑定的。 

**`onbeforeunload`  `onblur`  `onerror` `onfocus` `onhashchange`  `onload` `onmessage`   `onpopstate`  `onresize`   `onstorage`  **

> 单词应该多认识吧  storage ：仓库;;  
>
> 不加载前     失去焦点时    文档加载错误时     哈希值改变时     加载完成时    文档接受到消息时     
>
> popstate 回退历史记录时     文档尺寸改变时    当storage( local storage 或 session storage ) 改变时。 



## 内容分区

**` <address>`  `<article>` `<aside>` `<footer>` `<header>`  `h1-h6` `hgroup` `<main>` `<nav>` `<section>` **
: group : 组 的意思  hgroup： 对标题的分类，处理， 但是已从标准中删除， 不过大部分浏览器还是实现了该功能。
: 地址 (通讯地址-> 联系信息)   文章   旁白   脚部  头部  标题   组  主内容  导航栏   节( 一小节 )

**上面这些都是以内容作为分区， 就是一个页面常常需要的结构**

### `<address>`  联系信息
> 默认样式 ： display : block; font-style: italic;   也没有什么特殊的。 
> 应该是为了增强 语义化。 
**语境:** : 联系信息， 真实地址， URL, 邮箱， 电话， 社交媒体， 地理坐标。
也可以放在 文章的开头指明作者的信息。  不要加入与联系信息无关的内容， 如时间等。
**注意：** 不能嵌套 其他的块级的语义化的标签, 如 h1, article, section
接口:  `HTMLElement`

### `<article>`
> 其意在成为可独立分配的或可复用的结构，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。​​
接口 ： `HTMLElement`

### `<aside>`
> 通常用于侧边栏
接口： `HTMLElement`

### `<footer>`
> 页脚
接口 ：  `HTMLElement`

### `<header>`
> 辅助到喊的使用元素

### `<main>`
> 页面文档的主题内容。  比 估计是要比 article 要范围大， 也是不一定的。
接口： `HTMLElement`

### `<nav>`
> 导航栏 ：  菜单， 目录， 索引
> 对于屏幕阅读障碍的人,可以使用这个元素来确定是否忽略初始内容.
接口： `HTMLElement`


### `<section>`
> HTML 的独立部分, 一般来说会有包含一个标题。
接口:  `HTMLElement`

## 文本内容
> 在body  标签中的块或章节内容。 这些对于 accessibility 和 SEO 哼重要。
**`blockquote` `dd` `dl` `dt` `div` `figcaption` `figure` `hr` `main`  `pre` `ul` `ol` `li` `p`**

: figure : 数字， 描绘。   
> difinited list  div: division 划分，  horizontal rule ： hr水平分割线.  caption 标题。  preformat 预格式化
> unordered list ： ul 无需列表。   order list  list  paragraph ： 段落  quote: 引用， 引述。 

### `<blockquote>`   就是默认是有 缩进的  `<cite>`
> 块引用， 块引述。 对文章， 内容进行标注， 补充说明。  
> 引文引文， 就是引用别人的文件， 引用别人的话。  默认有缩进。 *{} 给干掉 了就体现不出来。
> 默认样式 ： margin-block-start: 1em.
<a href="https://developer.mozilla.org/en-US/docs/Web/CSS/margin-block-start"> 没有见识过的样式，writing-mode, margin-block-start </a>
接口： `HTMLQuoteElement`

**属性：**  `cite`, 标注引用的信息来源文档或相关的url 
```html
<blockquote cite="https://tools.ietf.org/html/rfc1149">
<!-- https://tools.ietf.org/html/rfc1149 标注下面的内容来源于哪里。  -->

</blockquote>

```
### `<dl>` `dt`
> 自定义列表
```html
<dl>
    <dt>
    <dl>
</dl>
```

###  `<dd>`  
>  用来指明描述列表 `dl` 元素中一个术语的描述
> 必须要有 一个 dt 元素
**属性**  `nowrap` : yes | no  ;  默认是 no 。

### `<div>`

### `<figure>`  描绘
> figure 出现， 计算， 描绘 ，认为。 
> figure 元素代表一段独立的内容， 经常与说明 figurecaption配合使用
> 作为一个独立的引用单元， 在主文中引用 图片， 插图， 表格， 代码等。 当迁移不会影响主体。
<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/figure" > MDN</a>

### `<figcaption>` 标题
> 做 figure 的标题

### `<hr>` 水平线

### `<ul> <ol> <li>`
> li : value , type 两属性
> ol : value ,  type, reversed, start 
> ul

### `<p>`
> 段落标签， 内部是不能嵌套其他的块级标签的

### `<pre>`
> 预定义格式文本。  空格也会被渲染
同常也会 和 `<code>` 标签联用

**接口：** `HTMLPreElement`

## 内联文本表签
> 定义一个单词， 一行内容， 或任意文字的语义结构或样式。 



### a anchor 
> : 超链接标签。 实现跳转功能
https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element
href : Hypertext Reference 。 超文本，  引用

**属性：** 
`download`      `href`    `ping`      `rel`  `target`          `type`
下载href地址内容   文本引用    追踪        关系    目标， 在哪里打开     建议类型

接口： HTMLAnchorElement接口： 
**属性：**
```js

anchor.hash  哈希
anchor.href  整个的超文本引用
anchor.host  主机， 主域名 www.baidu.com
anchor.origin  原点， 还未明白
anchor.port  
anchor.protocol  协议
anchor.rel     关系
```

### `<abbr>`  abbreviation
> 缩写元素 ;   abbreviation 缩写的意思。 

**属性**   title 定义对缩写的完整描述。 

接口：  HTMLElement

### `<b>`  bold
> 吸引读者。  html5 中变得不那么重要的， 最后没有其他标签是才使用他
> html5 : 
标题 h  
强调 用 em  
重要的 strong  
标记，高亮 mark.



###  `<bdi>`

> 文本双向隔离  . 还不懂 
>
> 会隔离可能以不同方向进行格式化的外部文本. 
>
> 当不知道是从什么方向嵌入文本，如来自于数据库的文本（有起数据库的文本方向）的时候，该元素是十分有用的。



###  `<bdo>`

> 用于覆盖当前文本朝向



### `<br>`

> 换行

接口 ：` HTMLBRElement`

<br>



### `<cite>`   以般 用在 blockquote 里面

> 表示一个作品的引用。 
>
> 它必须包含引用作品的符合简写格式的标题或者URL，它可能是一个根据添加引用元数据的约定的简写形式。

接口 ： `HTMLElement`     firefox : `HTMLSpanElement`

<a href="https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/cite">MDN address</a>



### `<code>`   一般与 pre 标签联用

> 书写代码的标签
>
> 




	<code>
			function(){
				console.log(this)
			}
	</code>  

<code>console.log( 'the style of code' )</code>



### `<data>` 与机械可读

> 一个指定内容和机器可读的翻译联系在一起。但如果内容是与 time 或者 date 相关的，一定要使用 [``](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/time)。



### `<dfn>`  表示术语的定义

<dfn>递归 ： recursion</dfn>

### `<em>`  强调文本， 重读

> `emphsize` 强调

> 产生斜体的效果

<em>我是签掉标签  i is a emphsize</em>

### `<i>`  区分普通文本的一系列文本

> 例如技术术语， 外文短语

<i>我是 i 标签  i is a iteral</i>

### `<kbd>`   ： 表示键盘的键位

>  **key borad**   表式键盘的键位

<kbd>ctrl + s</kbd>



### `<mark>`  高亮标签‘

<mark>表示为引用或符号目的而标记或突出显示的文本，这是由于标记的段落在封闭上下文中的相关性或重要性造成的。</mark>



### `<q>`  短的行内文本

```html
<q cite="http://en.wikipedia.org/wiki/Kenny_McCormick#Cultural_impact">
     Oh my God, you/they killed Kenny!
   </q>
```

<q cite="http://en.wikipedia.org/wiki/Kenny_McCormick#Cultural_impact">
     Oh my God, you/they killed Kenny!
   </q>

###  `<ruby>`  用来展示东亚文字的拼音或字符注释

<ruby>
漢 <rp>(</rp><rt>han</rt><rp>)</rp>
字 <rp>(</rp><rt>zi</rt><rp>)</rp>
</ruby>

### `<rb>`  ruby base element  `<rp>`rp  `<rt>` 

> 是 ruby 标签的子元素 ,  title, top  rp 
>
> rb  ruby base element   rp    rt 

<ruby>
漢 <rp>(</rp><rt>han</rt><rp>)</rp>
字 <rp>(</rp><rt>zi</rt><rp>)</rp>
</ruby>

```html
<ruby>
  漢 <rp>(</rp><rt>han</rt><rp>)</rp>
  字 <rp>(</rp><rt>zi</rt><rp>)</rp>
</ruby>

<ruby>
  <rb>漢</rb>字
  <rp>(</rp><rt>han</rt>zi<rp>)</rp>
</ruby>
```



### `<del>`  `<ins>`  `<s>`  编辑标识

> del  delete    表示从文本中删除的文字内容

> ins  insertion 插入文本   样式是下划线   b表示是 插入到文中的内容

> s  删除线来渲染文本； 仅仅用来表示样式

<del>this is a del</del>

<ins>this is a new insert wort</ins>



### `<samp>`  计算机的程序输出

> **samp :  定义范例计算机代码**  



<samp>output typeof Object</samp>



### `<small>`  附属和注释

> **个元素被重新定义为表示边注释和附属细则，包括版权和法律文本。**

> 样式是 是文字变小



刑法<small>：风萧萧兮易水寒</small>



### `<span>`



### `<sub> `  下标   subscript 



我是 <sub>下标</sub>

### `<sup>`    super

我是 <sup>我是上标</sup>

###   `<time>`  表示时间或日期

**属性** ： **datetime**

<time>20:00</time>



### `<var>`  定义变量

<var>x = y + 2 </var>

## 图片和多媒体

> **`area    audio 	img	 map 	track 	video  `**

>  区域       音频     图片      映射       追踪        视屏



### `<area>`  热点区域



> 兼容性是个问题

i

接口 ： **HTMLAreaElement**

**属性 ：** 

-  `acceskey`   访问键位 ： 获得焦点的快捷键
-  `alt`  alteration  代替
-  `coords`   坐标,  了解这个属性是重点
  - 矩形 ： (x1,y1),(x2,y2)  圆形 ：  x, y, r
-  `download`   属性存在，把超链接作为下载资源
-  `href`    area  的超链接
-  `hreflang`   链接资源的语言类型
-  `media`    定义媒体资源的类型
-  `rel`   包含 href 的锚， 用于描述 指定目标与链接的关系
-  `shape`    定义形状
-  `target`   
-  `type`  类型



###  `<audio>`  音频标签

接口 ： `HTMLAudioElement`



### `<img>` 

> 支持的格式 ： **`jpeg`  `gif`   `png`  `apng`  `svg`    `bmp`  `ico`  `pngico`**

























