
有个属语表： <a href=" https://developer.mozilla.org/zh-CN/docs/Glossary "> https://developer.mozilla.org/zh-CN/docs/Glossary </a>

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

### contextmenu 上下文菜单。 浏览器的默认性为事件也叫 contentmenu
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

**`onbeforeunload`  `onblur`  `onerror` `onfocus` `onhashchange`**



### a anchor 
> : 超链接标签。 实现跳转功能
https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element
