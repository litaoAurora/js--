### vscode



  nodejs的内核中对于js的解析，使用的是谷歌的v8引擎。v8引擎内置有js虚拟机。通过v8虚拟机，可以将js代码编译为字节码。而v8虚拟机是能够识别和直接运行该字节码的。因此，以下执行逻辑成为可能：

1、js代码 -> js字节码
2、js字节码 -> nodejs ->运行  



###  原来 call bind apply 封装到了 Function 里面去了.

继承连 

object => Function => String | Number | Array

### 常量

- `const`      `construction`

声明同时初始化  `const a = 1;`, 不能事后初始化. 

### 变量

提升作用域 , 只在预编译, 与解释中 将 function`整个的块里面的内容,和声明提前了 ` , 和 `var 声明的变量提前.`

- 声明变量

`有两个步骤, 1. 声明 var variable; 2. 赋值 variable=1;`

> var 声明 变量为 undifined . 

- 声明 则变量存在, 而 之不存在. window 中有 var 声明的变量.

==`var 有提升声明作用域, 变量挂在在全局中. ``let 声明一个块级作用域 局部变量`==

```javascript
function func(){
    a = 1;
}
console.log(a); // => 会报错.  referenceError: a is not undifined

o() // => 1 , 标准的函数定义是个 特殊对象. 预先解析, 预编译
function o(){
    var a = 1;
    console.log(a);
}
test(); // => typeError : test is a not function , 或许,var 和函数都预解释了, 但是 赋值运算符并未有 运行, 古 a 的指针并没有指向 function 的内存标识.
var test = function(){
    var a = 1;
    console.log(a);
}

```

> 函数作用域的封闭很强.  a=1; 表示块作用域是全局的, 但是不是对函数.

> 常量和 变量的选择, 明确声明后 在后面的代码中==不更改他的 指针指向==. 则建议用常量, 以减少 bug ,



## 数据类型

> JavaScript 本身是个弱类型的语言, 就是 有个 隐式转化的 过程.

- number boolean  string null undefined symbol BigInt object 

- `Number` => 双精度, 浮点型.
    - NaN `Not a Number`
- `undefined` => 说明一个变量没有被分配值的一个原始值。==未定义值类型.==
- `unll`  =>  空对象, 也为空值, 说明一个值有了, 但是为空

> unll => object, 这个object 只有一个值为`unll`

> undefined  => undefined 只有一个值 为 undifined. 变量未定义,所以也就==不能类型装换为零的转换==. Number(undefined) => NaN; toString(undefined) ; =>[object Undefined]

- String
    - \`${name }\`  `插值`  必须是  tab上面的字符串加 $ 符才行.



### 类型转换

####  隐式类型转换

- `+` ‘’ 为 String
- 算术运算符  操作为 Number



**String**  单值+ 字符串

```javascript

console.log(a = 3 + 'megedu'); // '3megedu' String
console.log(a = null + 'megedu'); // 'nullmegedu' String
console.log(a = undefined + 'megedu'); // 'undefined3megedu'
console.log(toString(undefined)); // => [object undefined]不能类型装换
console.log(a = true + 'megedu'); // 'true3megedu' String
```

**Number**

```javascript
console.log(a = null + 8 typeof a); // 8 Number
console.log(a = undefined + 8); //  NaN Number, 不能类型转化
console.log(a = true + 8); // 9 Number
```

**boolean** 特殊的数字

```javascript
console.log(a = null + true typeof a); // 1 Number
console.log(a = undefined + false); //  NaN Number, 不能类型转化
console.log(a = null & true); // 0 Number  
// 算术运算符 所以 当数字看了. + - * / & | .. + 特殊, (字符串拼接 和 运算)
```



**短路运算符** => 放回一个值 或 boolean , 就是短路时的类型, 没有类型转换.

```javascript
// && || ! 
// 那第一个值判断boolean , 
console.log(a = null && true); // null object 与 
console.log(a = false && true); // true boolean
console.log(a = true & `ff`); // ff String
console.log(a = true & ''); // String
// 空字符串为零. 
```

**null**

```javascript
console.log(a = null + undefined); // NaN Number  
```

```javascript
console.log(a = null + true); // => 1 Number
console.log(a = null + false); // => 0 Number
console.log(a = undefined + true); // => NaN Number
console.log(a = undefined + false); // => NaN Number
console.log(a = null & true); // => 0 Number
console.log(a = undefined + false); => 0 Number
```



## 字符串的转义字符字符

|   名称   | 说明                        |
| :------: | --------------------------- |
|    \0    |                             |
|    \b    | 退格                        |
|    \f    | 换页                        |
|    \r    | 回车 光标移到行首.          |
|    \t    | Tab制表符                   |
|    \v    |                             |
|    \n    | newline 换行, 光标移到行尾. |
| `&emsp;` |                             |

## String

> 继承于 Function对象

> 所有的字符串 应该都是放回==新的字符串==. 应为 字符串是个字面量, 本身不可变.

- 属性
    - String.prototype  原形连
    - String.length  长度
- 方法 => 
    -  concat  charAt  endsWith  includeof  replace slice substring trim valueof

```javascript
 + 和 \
 let a = 'let \
jji ' // 太长 用 + 或 \ 来 分割多行来写, 但还是一串.

console.log('hello'.concat('word')); // + 可以用加来代替, 连接合并
console.log('hello'.charAT('word')); //[n] 来代替, 索引
console.log('is'.endsWith('s')); // true 以什么结尾
console.log('is my.'.includes('my'));// 是否包含
console.log('is my'.indexOf('my'));// 索引值 45

console.log('is my'.replace('my','you'));// 替代
console.log('is my'.slice(beginIndex(number), endIndex));// 切片,
console.log('is my'.split('my'));// 分割, my 作为分割符
console.log('is my'.substring(0,2));// is  子串
console.log('is my'.trim());// 剪切两端的空白符.  
console.log('is my'.valueOf());// 等于 String.prototype.toString() 通常是在js内部使用的.
```



## Number

> 要注意 数 有 二进制数, 八进制数, 十六进制数

- => 双精度浮点型
    - -(2^53-1)~2^53-1

- 二进制 `0b0010`
- 八进制` 0755 ` 
- 十六进制  `0xAA`

```javascript
console.log(0b0010); // 2
console.log(0755); // 493
console.log(0xAA); // 170
```

###  属性

- Number.NaN
- Number.POSITIVE_INFINITY
- Number.Max-VALUE, MIX_VALUE
- `Number.infinity`

> NaN 就好比两个 不同的实例.  不是同一个实例间 不能相等.

### 方法

- `Number.isFinite( instance )`; 是否有穷
- `Number.isInterger(实例)`;   是否为整数
- `Number.isNaN( 5 )`;  // 是否 NaN
- `Number.parseInt()`;  // 该方法和全局的 [`parseInt()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/parseInt) 函数是同一个函数：
- `Number.parseFloat()`;// 

> ```js
> Number.parseInt === parseInt; // true
> Number.parseInt('0011', 2 ); 与原来是什么进制的 转为十进制.
> ```

- `Number.toFixed(n)` ;  // 固定小数点.

> 3.14156.toFixed(2); // 字符串, 3.14



## Math 内置对象

> 包含挺多的 数学方法. 

- `Math.random()`; // [0-1)



## 运算符

>  运算符, 操作符 应该都是 运算符重载过了的.

### 算术运算符

`+` `-`  `*` `/` `%`  `**`(幂)  `+` `-`(一元正负)  `++`  `--`

++ 要比 += 快. 



### 比较操作符

`==` (宽等) `===` (严格等)  `!=`   ` !==`    `>`   `<`    `>=`  `<=  `

`==` ,   `>` ,`<` , `!=`: 有类型转换,

`===` : 类型相等的情况下 比较是否相等.

```javascript
console.log( '30' > '200'); // true
console.log( 30 > '200'); // false 
  
```

```python
'在python 中'
'20' > '300'  : => true
```



```javascript
    let strn = new String('foo');
    let str = new String('foo');  // 不同的实例
    console.log(strn == str); // =>false
    console.log(strn === str);// => false
	不是同一个实例, 应该是不能比较的.
```

>  `>`   `<`    `>=`  `<=  `  `==`
>
> 当都是字符串时, 是比较  字符串的  字节码的
>
> 当有 Number 时 , 有类型转换, 转换成  Number 再比较, 要 留意 NaN 



### 逻辑运算符, (短路)

`&&`  `||`  `!`   与或非

- 短路运算

```javascript
1 && 2; //2 第一位为真, return 第二位
0 && 2; // 0第一位为假, return 第一位
1 || 2; // 1 
0 || 2 ; // 2 
!2 ;//false 往布尔转 
```

- if 的判段 => boolean, 就都是 布尔了.



###  位运算符

`&` `|` `^` `~` `<<` `>>` 

位与, 位或, 异或, 取反 左移右移.

### 三元运算符

conditon ? one : two ;

条件为真 放回 -> one , false -> two

one 可以为值和 语句.

```javascript
// 三元运算符 可以由 if语句改造.
if(condition){one}else{two}
```

###  逗号操作符

```javascript
// 一条语句, 有多个 (多个表达式) 赋值表达式
// 赋值表达式本身也是有值的 ,值为 = 左边的
let a = 4+5, b = 'hh', 
```

### 其他

> 属于运算符重载过了的, 本质上是对应到了一个函数上了.

| 名称       | 说明                                     |
| ---------- | ---------------------------------------- |
| instanceof | 判断是否属于制定类型的  ==实例==         |
| typeof     | return 类型字符串                        |
| delete     | 删除对象, 属性, 数组(数组原来的长度不变) |
| in         | true, false . 在..内                     |
| new        | 绑定 this 上下文. 构造出一个实例对象.    |

```javascript
let b = [2,1, 5];
let obj = {
    kk : 'K'
}
console.log( 2 in b); 
console.log( 'kk' in obj ); 
// console.log( kk in obj );  会报错 Reference Error: kk is noe defind
```

```javascript
// 数组 很像 python 的字典
// 0 : value; 1 : value
// index 索引和长度都是 数组的属性.
let arr = ['red', 'yellow','cyan'];
console.log(0 in arr); // true
console.log(4 in arr); // false 0 1 2 3 
console.log('lenght' in arr); // true
console.log('red' i arr); // false 
```



### 运算符优先级



单目运算符 > 双目运算符 > 

| 如下                             |
| -------------------------------- |
| . []                             |
| ( )  new                         |
| ! ~ - + ++ -- typeof void delete |
| * / %> + -                       |
| <<< >> >>>                       |
| < <= > >= in instanceof          |
| == === !==                       |
| =                                |
| ,                                |

## 生成器表达式

```javascript
// function* inc(){} => 生成器函数.
function* inc(){ 
	let i = 0;
    while(1){
        yield (++i)
    }
}
let g = inc();
console.log(g.next()) // {value:1 , done: false} 
// done ==标志生成器是否结束了.==
console.log(g.next().value) // 对象取属性.
```

## 函数 function

>  ==每个函数实际上都是一个`Function对象。`==

```javascript

var sum = Function('a','b','return a + b');
console.log(sum(2,6));

**属性**
    arguments  caller   length name displayName
**方法**
	call apply bind toString 
```

> 总结: 每个函数都是 Function的 实例对象. 在 Function 中 封装了
>
> call apply 宾得 toString 就是每个函数都能调用.

1. 函数表达式 let fn = function (){}
    1. 函数对象挂载在 一个标量中, 声明不会提升
    2. 需要 借助 别的表示符而已.

```javascript

var add = function _add(){
    console.log(_add); // [Function _add]
    console.log(add); // [Function _add]
    
} // _add 仅仅在内部可见.

```

2. function add(){}
    1. 声明会提升, 函数对象
    2. 有自己的标识符.

3.函数对象

```javascript
 let fn = new Function(‘console.log(‘hello’)’);
function fn(){} // 本质上是 new Function 的语法糖. 
```

### 高阶函数

> 定义: 函数作为参数或放回值是一个参数.

```javascript

function a(){
    
    return function inc(){
        console.log('i im inc');
    }
}
let func = a();
func(); // => 高阶函数的定义

// 计数器 => 高阶函数, 每调用一次, 就放回一个值,(高阶函数, 生成器)
let counter = function(){
    let i = 0;
    return  function (){ return ++i};
}
let count = counter();
count();

```

#### map 函数的封装

```javascript
// map 函数是对数组中每个元素的映射到另一个元素.
function map(fn, arr){
    let newwarr = [];
    for(x in arr){
        newwarr[i] = fn(arr[i])
    }
    return newwarr;
}
let newwarr = map(function(x){return ++x}, [1,2,3]);
```

### 箭头函数

```javascript
// ()=>{}, 没有绑定自己this 上下文.
(x)=>{return ++x}
x => {return ++x}
x => ++x;
```

1. 不会绑定自己的this 上下文, 但是会上一级==**函数**的this==继承. 没有call() 方法
2. 没有 argumens 
3. 箭头函数不能用作构造器，和 `new`一起用会抛出错误。
4. 箭头函数没有`prototype`属性。
5.  `yield` 关键字通常不能在箭头函数中使用.

==在对象 键值对映射时 不会继承this 的, 只有定义在函数中才能继承 上层函数的 this==



### 函数参数

> 定义参数(创建函数时)  传递参数(调用函数时)
>
> 位置对应, 没有关键字传参. 

#### rest parameters 剩余参数

`...args`

```javascript

const add = (...args)=>{
    console.log(args, typeof args);// {0 : [1,2,3,4]}, object.
    for(var n in args[0]){
        console.log(n)
    }
    console.log(args == arguments);
}
arr = [1,2,3,4];
add(); // arguments 对象

const sub = (x,y)=>{console.log(x,y); return x + y};
// 一个位置对应一个参数(基本数据类型或引用类型. 传多的 舍掉或保存在 arguments 里面.)

```

#### arguments

> `...args` 与 `arguments` 的关系. 是一样的



## 定义类

> 基于原型 和 基于类是不同的 面向对象思维

```javascript

var obj ={
    a : 1,
    b : 2
};// 第一种 类定义方式
function obj2(x,y){
    this.a = x;
    this.b = y;
}// obj 与 obj2 => var objn = new obj2(1,2); 所得是一样的.
// var objn = new obj2(1,2); 构造函数,会调用一次函数.构造实例对象.

```



## 异常

> 异常应该是会冒泡的

```javascript

try{
    throw 1;
}catch(error){
    console.log(error, typeof error); // 拿到的类型并不准确
    console.log(error.constructor.name);
    
}// throw 把异常抛出来, catcht 捕获异常并处理.
console.log("error is my");// 上面的处理完了异常, 这句打印语句才能继续运行. 

```





###  constructor 构造器函数, 或 构造器属性

==所有对象都会从它的原型上继承一个 `constructor` 属性==

**nulll 和 undefined 各自只有 null 和 undefined 单值, 并没有 constructor 属性**

> constructor 能够拿到 原本数据的类型.  constructor.name



### this 的坑

> 箭头函数 没有绑定 this 的功能.

```javascript
var school = {
    name :'magedu',
    get : function(){
        console.log(this.name); // 'magedu'
        return function(that){   // 此return 是返回一个普通函数.
            console.log(this == global); // true, 此时this 丢失
            '--------'
            console.log(that == global); // 显式传入
        }
    }
}
var meth = school.get()();// this 会丢失

var meth = school.get(); // => function
// 解决this 丢失 使用 call 显式传入
meth(school); //1. 显式 传入
meth.call(scholl);

```

```text
总结:
	函数执行时,会开始新的执行上下文. Execution context
	创建this 属性. this 属性由调用方式决定.
	普通函数调用fun() this 指向 window 或 global
	obj.fun(); this指向 obj
	fun.call() 和 .applay() 看参数是谁.call() 本身也是在调用了 .前面的fun函数.
```

return fun(){} // => return 的  都是普通函数, this指向 全局.

==调用方式决定 this的指向. a = obj.get;a() 也是普通调用.==





## 闭包

==闭包的原理: 函数创建, 变量...压栈,弹出, 当变量或函数或对象没有被引用时,第一层的变量在调用完时时就会消亡,故在函数里面在创建函数来引用上一层的变量.return 内部函数.==

> 对象在堆中, (字面量, 变量, 函数创建)在栈中, 相同的字面量值是同一个地址
>
> 而同个不同的函数调用会得到不同的 对象引用. 
>
> 压栈, 创建变量, 创建对象, 弹出栈区, 不被引用到就会消亡.  

```javascript
function test(base){
        var base = base;
        var obj = {}
        function inc(step = 1){

        }
        return obj;
    }
    var foot = test(10);
    var foo = test(10);
    console.log(foot === foo) // false
    var obj  = {};
    var obj1 = {};
    console.log(obj === obj1) // false
```

> 为什么返回的 inc 是 不一样的呢?
>
> 里面的 inc 在外面是访问不了的, 
>
> 所以每次调用 test 所返回的 inc也是在不同的栈上生成的不同对象.

```javascript
// 计数器

function conut(base){
    var base = base;
    function inc(step = 1){
        base = base + step;
        return base;
    }
    return inc;
}
var foot = conut(10);
// 通过不断调用 foot() 可以得到计数器.
console.log(foot()); // 11
console.log(foot()); // 12
```



## 构造函数和原型

- **每个构造函数都有一个prototype属性**，指向另一个对象 `prototype`。

`prototype`—> 原型链—> (继承) 

### 原型

- `prototype` 为原型对象
- 共享方法

> 一般情况下， 公共属性定义到构造函数下， 公共方法定义到原型对象身上(相当于把公用的方法封装到祖先哪里， 与继承类似)



- 对象原型 `__proto__` —> 原型链—> (继承)

在实例中，系统自己添加了一个 `__proto__` 指向了构造函数的原型对象(`prototype`)

- 实例指向 `__proto__` 构造函数指向 `prototype` `__proto__` 指向 `prototype`

```javascript
// 

function star(a){
  this.a = a;
  this.__proto__.bin = function(){};
  console.log(this)；//// star {a: 'a'}  构造函数名， 实例对象。
}
let liu = new star('a');
console.log(liu); // star {a: 'a'}  构造函数名， 实例对象。
/*
star.prototype.constructor -> star; 
*/
```



### 构造函数， 实例， 原型三者的关系。

基本类型![屏幕快照 2019-09-17 08.57.39 PM.png](https://upload-images.jianshu.io/upload_images/18309556-50e7adb11a699d00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)













