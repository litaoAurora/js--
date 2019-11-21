http://yanhaijing.com/es5/#73 

主体文件， 生成虚拟节点的
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>   专门处理视图的。 

## 陌生的单词或专业术语。 
forceUpdate  手动强制之只更新当前组件。 是一个**局部更新**的方法。 
    force ： 力量， 武装。 

React.Fragment  react 在挂载根组件时不会删除原先的标签。 而每个组件也需要唯一的根组件就会多出很多 莫名的更标签。 
                **用 React.Fragmen 这个虚拟标签来代替根标签。**   flag 爆炸，碎片。 

父传子。 
this.props.msg 子组件用这个， 
this.props.children 是默认有这这个的子集的。 在父组件引用子组件的 闭合标签中传入的 子集。 **类似于 slop 插槽**。 
                    children 是个数组。 
msg = this.msg 父组件传这个

state     和 props 都是个异步追踪的集合。 
state = {}
    this.setState( {}, callback )  来修改state 的数据。
                    setState 是个异步函数， 视图更新完后会调用 callback 。



## 错误集合
```js
Each child in a list should have a unique 'key' prop,
Check the top-level render call using <div>. 
我 ： 每个在列表中的每个孩子应该有唯一表示符 ‘key’属性， 检查顶层渲染
百度 ： 列表中的每个孩子都应该有一个唯一的“键”道具， 使用<div>检查顶级呈现调用

Uncaught SyntaxError: /Inline Babel script: Expected corresponding JSX closing tag for <input>
me : 不能捕获 语法错误： 在行babel 脚本 ： 期望一个符合 jsx 的闭合input标签。 
youdao : 未捕获的SyntaxError: /内联Babel脚本:期望对应的JSX结束标记<input>

Uncaught Invariant Violation: Expected onClick listener to be a function, instead got type string
: 未能捕获不变的冲突 ： 期望onClick 监听器是一个 函数， 而不是得到一个字符串类型。

```


es6 class 函数的语法糖。
class 的实例属性还可以定义在 constructor 函数的外面。 只是不能传参。 
```js
ƒ test() {
    _classCallCheck(this, test);

    this.a = "a";
}

// 这个就是  class test{ contructor(){ this.a = "a" } } 的打印结果。
// 其实就是调用了 _classCallCheck() 函数调用检查函数。  
```

## 受控组件

5.235:8000
###  下拉菜单 
什么时候 option 是选中转态 ?? 
1 select 的 value 和 option的 value 一样时
2 option 有 selected 属性时 。 

但是 react 中是不允许option 的selected 的。 
select 控制
    value  受控状态
    defaultValue 是非受控状态。 

```js
// value 是受控组件
// defaultValue 是非受控组件
<select value=""  defaultValue="" >

```

### 输入框的受控 与 textarea
react 自己定义的 onChange 事件。 次事件与原生事件已经不一样了.
受控 则添加 value , 有 value 就要添加 onChange 事件。 




# 结论

- 第一次用 bind 改变指向之后， 在用 bind 是不能再改变 this的指向的了。 fn.bind(null);  此后的操作都是 null了。 
: 可以得出 react中事件句柄的调用是用 call(null)来调用的。 而我先于 调用前用 `bind` 绑定就this指向不会变了。 



## 生命周期
(componentWillMount，componentWillReceiveProps，componentWillUpdate)
都被getDerivedStateFromProps替代。



试一下这个 ： render 改变 state 。   this.setState( { str : Math.random() } ) 是否能成功。 







