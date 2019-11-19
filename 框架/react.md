
主体文件， 生成虚拟节点的
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>   专门处理视图的。 

## 陌生的单词或专业术语。 
forceUpdate  手动强制之只更新当前组件。 是一个局部更新的方法。 
    force ： 力量， 武装。 

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
```js
ƒ test() {
    _classCallCheck(this, test);

    this.a = "a";
}

// 这个就是  class test{ contructor(){ this.a = "a" } } 的打印结果。
// 其实就是调用了 _classCallCheck() 函数调用检查函数。  
```

# 结论

- 第一次用 bind 改变指向之后， 在用 bind 是不能再改变 this的指向的了。 fn.bind(null);  此后的操作都是 null了。 
: 可以得出 react中事件句柄的调用是用 call(null)来调用的。 而我先于 调用前用 `bind` 绑定就this指向不会变了。 











