http://yanhaijing.com/es5/#73 

主体文件， 生成虚拟节点的
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>   专门处理视图的。 

## 陌生的单词或专业术语。 
forceUpdate  手动强制之只更新当前组件。 是一个**局部更新**的方法。 
    force ： 力量， 武装。 

React.Fragment  react 在挂载根组件时不会删除原先的标签。 而每个组件也需要唯一的根组件就会多出很多 莫名的更标签。 
                **用 React.Fragmen 这个虚拟标签来代替根标签。**   flag 爆炸，碎片。 
onChange  事件时react 中修改了的事件
defaultValue
React.createRef();
this.input.current; 来获取当前的DOM


父传子。 
this.props.msg 子组件用这个， 
this.props.children 是默认有这这个的子集的。 在父组件引用子组件的 闭合标签中传入的 子集。 **类似于 slop 插槽**。 
                    children 是个数组。 
msg = this.msg 父组件传这个

state     和 props 都是个异步追踪的集合。 
state = {}
    this.setState( {}, callback )  来修改state 的数据。
                    setState 是个异步函数， 视图更新完后会调用 callback 。

ref={}   放在模板中
    React.createRef()



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

Uncaught TypeError: /Inline Babel script: Duplicate declaration "Cart"
me : 未能不活的 类型异常。  在内联babel 脚本中 重复声明 `Cart` ;  大白话就是  cart 重复定义了。 
youdao : 未捕获的类型错误:/内联Babel脚本:重复声明“Cart”;

Warning: Invalid DOM property `class`. Did you mean `className`?
me : 警告 ： 无效的 文档属性 class ， 你的意思是 className 吗
youdao : 警告:无效的DOM属性' class '。你是说“className”吗?


Warning: validateDOMNesting(...): Text nodes cannot appear as a child of <table>.
me : 警告 ： 无效的动作DOmNesting ;  文本节点作为一个孩子显示在table标签中。  
youdao : 警告:validatedom(…):文本节点不能作为<table>的子节点出现。
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







## 生命周期
(   
    **挂载**
    constructor ,
    componentWillMount  , created
    render              
    conponentDidMount,

    **更新**

    componentWillReceiveProps,
    shouldComponentUpdate
    componentWillUpdate    beforeUpdate
    render
    componentDidUpdate      updated
)
都被getDerivedStateFromProps替代。


## redux 转态管理器
> 实现原理 利用闭包, 和发布订阅者模式。 

1) **创建一个数据容器 . store = Redux.createStore( reducer )**
2) **把修改数据的封装逻辑写好, 这个函数是放在   createStore 中或者 放在 combineReducers( {  冲突函数  } )；**
    处理冲突的函数在被传入真正的数据前会被调用多次， 故要 return 一个默认值来。 
3) **如何获取共享数据 。  store.getState()**
4) **如何修改共享数据。 store.dispatch 来触发 mutation;**
5）**监听数据的变化。  subscribe( function(){} )**
6）**合并多个 store  ; => let reducer =  Redux.combineReducers( { newData, length } )**
7) **获取合并后的的数据 store.getState().数据名.**

**猜测 ：**                                                                                                                                                                                                                       
    store.despatch( { type: "", haha : "" } ) 
    store 中的数据  data = setData( data, { type: "", haha : "" } )
> 当调用 dispatch 时， store 是会把 本地的 state 和 dispatch传入来的 参数一并传入到  mutation函数中去做逻辑处理，
> 放回来的值 作为下一个 state 保存到 store本地。 


-------------------------------------------------------------------
```js

let store = Redux.createStore( setData ); //  创建容器
// setData 是专门用来修改数据的 setData 就是 mutation

// state 就是共享的数据， actions 就是用户行为。 
function setData( state="默认值", actions ){
    // 这里return的值是 下一次 传入的 state. 
    // 也是 getState 拿到的数据。 
    // 明白这个才是真理。 
    if( actions.type == 'GET' ){
        return actions.msg;
    }
    // actions 就是 despatch 传入进来的 json 对象。 
    else{
        return state;
    }


    switch (action.type){
        case 'get':
            return action.fileter
        default : 
            return state;
    }

}

store.despatch({
    type : 'GET',
    msg : this.str,
}); // 来触发，修改数据。 
// type 是必须的 。 来判断行为。 

store.getState(); // 获取数据。 

store.subscribe( function(){
    ReactDOM.render( <Root />, document.getElementById('Root') )
} )
```

----------------------------------------------------------------------


三大原则
redux 是单向数据流。 单一数据源
state 是只读的。 
使用纯函数来修改。 

redux 是 发布订阅者模式。 



# 结论

- 第一次用 bind 改变指向之后， 在用 bind 是不能再改变 this的指向的了。 fn.bind(null);  此后的操作都是 null了。 
: 可以得出 react中事件句柄的调用是用 call(null)来调用的。 而我先于 调用前用 `bind` 绑定就this指向不会变了。 


试一下这个 ： render 改变 state 。   this.setState( { str : Math.random() } ) 是否能成功。 







