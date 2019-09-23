模板字面量
`hello world` `hello ${who}` who 是一个变量 `variable`

### 转义字符
| code | output                              |
| ---- | ----------------------------------- |
| `\0` | null 空字符 console.log('\0') => '' |
| `\'` | 单引号                              |

> javascript 不区分单双引号

### 长字符串
> `+` 运算符 或  `\ ` 长字符串换行表式。

```javascript
let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable.";

let longString = "This is a very long string which needs \
to wrap across multiple lines because"
```

## 基本字符串和 new String() 的区别
'my' JavaScript 会自动把 'my' 提升为 String 对象。
new String('my')  为 Object 类型
```javascript
var s_prim = "foo"; // String
var s_obj = new String(s_prim); // Object

console.log(typeof s_prim); // Logs "string"
console.log(typeof s_obj);  // Logs "object"
```
## 解惑
>` 'my name' `直接声明的字符串为 `String` 类型
>` new String('f')` 为 `Object` 类型. 
>故 String.prototype....   为直接声明的` 'my name'`字符串的 Prototype.property method 
>Number 和 Boolean 也一样的.
## 属性
- String.prototype.length    只读

   

- String.prototype.constructor
  `用于创造对象的原型对象的特定的函数。`

## 方法
> param 为 [, ...] 的是 可选可不选


- 语法
    - 解析
         - 用法



功能： 

1） 拼接多个字符串。 concat(…str)

2) 	根据索引位置找值  charAt(index),  根据值找索引  indexOf( str ); 

3)	是否包含 includes(str)

4)    以什么为结尾 endsWith(), lastIndexof(), 

```javascript
str.charAt(index);// 索引值获取 单个字符值  char字符 At at
str.concat(string2, string3[, ..., stringN]); // 和原字符拼接字符串。多个字符串。
str.endsWith(searchString[, length]); 
		// 原字符串 到 length 为止是否以searchString 结尾
		// return true false 
str.includes(searchString[, position]);
		// 原字符串 到 length 为止是否包含searchString 
		// return true false
str.indexOf(searchValue[,fromIndex]);
		// 原字符串 从 fromIndex 开始 ，寻找 searchValue的位置。
		// return indexValue 或 -1(没找到)
str.lastIndexOf(searchValue[, length]);
		// 原字符串 从 0 开始 到length结束，寻找 searchValue最后一次出现的位置
		// return indexValue 或 -1(没找到)
referenceStr.localeCompare(compareString[, locales[, options]])
		// 还未了解
		// 功能是 你补 js 以首位字符的 unicode 编码的不足。比较字符串 以 排序。
str.match(regexp);
		// 正则匹配， 和 全局 global 连用。 regexp 正则表达式
		// 全局 g return []  or null(没有匹配)
		// 普通 匹配一次， return []
str.matchAll(regexp); // =》 迭代器
		// regexp 必需全局的 。  可以用 exec 加循环实现。
str.normalize([form]); // 方法会按照指定的一种 Unicode 正规形式将当前字符串正规化.
		// [form] : `NFC` `NFD` `NFKC` `NFKD`
		// str= "\u1E9B\u0323";  str.normalize(); // => same as above
str.padEnd(targetLength [, padString]); // padding end  原生环境不支持。
		// targetlength 目标长度，  padString 填充的字符串
		// return paddstr
str.padStart(targetLength [, padString]); // // padding end  原生环境不支持。重写方法在文档里面有
		// targetlength 目标长度，  padString 填充的字符串
		// return paddstr
let resultString = str.repeat(count);// 重复 conut 次 str 字符串 效率比 + 要好
str.replace(regexp|substr, newSubStr|function); // 替换字符串
		// param1 : 可以是字符串和正则  param2 : 可以是字符串和回调函数。 
		// return newstr

str.search(regexp); // 放回 索引.
		// regexp 可以字符串 可以 正则
		// return  索引值。
str.slice(beginIndex[, endIndex]); // 由 闭合索引值得 某段字符串
		// beginIndex 开始索引值 endIndex 索引，可选
var str = 'abc def g';
str.slice(2,-3); // 可以赋值， 但是 是 正向的
		// beginIndex , [, endIndex]
		// return c de 

str.substring(indexStart[, indexEnd]); // indexString indexEnd 负值 等于 0
		// indexString 开始， indexEnd 结尾。 如果都是零的化， 就 都为0
		// return `sting`

var str = 'abc def g';
str.substr(-2, 2); // " g"
		// 

str.startsWith(searchString[, position]); // 是否 以什么开头  true 或 false。
		// return true false 

str.split([separator[, limit]]);  // => 分离 成字符串
		// return [], 
str.trim(); // 剪切两端的 空格。
		// return newstring ;
str.trimRight();  str.trimLeft();
str.valueOf(); // new String('f').valueOf() => 'f' 
string[Symbol.iterator]; // => return iterator 生成器

```







- `match(regexp)` demo

```javascript
全局下
var str = "前端对于网站来说，通常是指，网站的前台部分包括网站的表现层和结构层。因此前端技术一般分为前端设计和前端开发，前端设计一般可以理解为网站的视觉设计，前端开发则是网站的前台代码实现，包括基本的HTML和CSS以及JavaScript/ajax，现在最新的高级版本HTML5、CSS3，以及SVG等。"
var str1 = str.match(/(前端)/g);
console.log(str1); // ["前端", "前端", "前端", "前端", "前端", "前端"]

var str1 = str.match(/(前端)/);
console.log(str1); // [str, groups, index, input] 
/*     分组 多个个1 : '前端'。
{0: "前端" 
1: "前端"
groups: undefined  
index: 0     
input: "前端对于网站来说，通常是指，网站的前台部分包括网站的表现层和结构层。因此前端技术一般分为前端设计和前端开发，前端设计一般可以理解为网站的视觉设计，前端开发则是网站的前台代码实现，包括基本的HTML和CSS以及JavaScript/ajax，现在最新的高级版本HTML5、CSS3，以及SVG等。"}*/
length: 2

```



### 匿名函数可以解决 回调函数 的传参问题。

- 箭头函数没有 arguments 

```javascript

function replacer(count) {
  // p1 is nondigits, p2 digits, and p3 non-alphanumerics
  count++;
  console.log(arguments);
  return count;
}
// replacer(1);

var newString = 'abc12345#$*%'.replace(/([^\d]*)(\d*)([^\w]*)/, (...arg)=>{
  var count=1 ;
  
  var argr = arg;
  replacer(count,argr);
});
console.log(newString);  // abc - 12345 - #$*%
```



- slice 和 substr 和 substring 的区别。

```javascript
console.log()
console.log(str.substr(0,str.length);) // SyntaxError: missing ) after argument list

var str = 'this is a test';
console.log(str.substr(0,-2));// ''
console.log(str.substr(3,0));// '' 
console.log(str.substr(0,str.length)) // this is a test
console.log(str.substr(-2,-1), typeof str.substr(-2,-1)) // '' String
console.log(str.substr(-2,-3)) // ''
console.log(str.substr(-2,str.length)); // st

//substr : 总结 第一个数可以是 负值， 第二个不可以。

var str = 'this is a test';
console.log(str.slice(0,-2));// 
console.log(str.slice(0,str.length)) // this is a test
console.log(str.slice(-2,-1), typeof str.substr(-2,-1)) // 's' String
console.log(str.slice(-2,-3)) // ''
console.log(str.slice(-2,str.length)); // st

// sllice ： 总结  当 startIndex 为负值是 , endIndex 不能比 startIndex 小
// slice ： 只要顺着能通， 啥值都可以

var str = 'this is a test';
console.log(str.substring(0,-2)); // ''
console.log(str.substring(3,0)); // thi
console.log(str.substring(0,str.length)) // this is a test
console.log(str.substring(-2,-1), typeof str.substr(-2,-1)) // '' String
console.log(str.substring(-2,-3)) // ''
console.log(str.substring(-2,str.length),'end'); // st

// substring 哪个小哪个为开始。 
```









# 箭头函数 

- 没有arguments 





## Array

###  静态方法 



- `Array.from(arrayLike[, mapFn[, thisArg]]) ` // return ： 一个新的数组实例
  - array like  类数组， 伪数组， 
  - [,mapfn]  映射函数， 回调函数
  - [,thisArg]  执行回调函数 `mapFn` 时 `this` 对象。

- `Array.isArray( obj );` // return   true，false  是否是 数组
- `Array.of(...element0,1,2)`  Array.of(1,2,3) => [1,2,3]



- 因为 。length 比长度 大一。 故  不包含endIndex 

```javascript
var arr = [1,2,3]
var new_array = old_array.concat(value1[, value2[, ...[, valueN]]]); // 拼接数组
		// 可以拼接多个数组
		// return 一个newArray;  一唯的。
arr.join([separator]); // 把数组里的值 拼接唯一个 字符串
		// separator 分割符  separator = ','
		// return newString;  '1,2,3'
arr.shift(); // 从数组中删除第一个元素，并返回该元素的值。
		// 没有参数， 改变原函数。
		// return 删除的值。 
arr.unshift(element1, ..., elementN); // 数组数位添加一个值
		// element1 可以多个值
		// return 当一个对象调用该方法时，返回其 length 属性值。
arr.push(element1, ..., elementN); // 改变原函数， 后面追加
		// element1 多个参数
		// return  原函数的length
arr.slice([begin[, end]]); // 可以赋值， end 要比 begin 大。
		// 开始 , 可以负值
		// return newArray;
array.splice(start[, deleteCount[, item1[, item2[, ...]]]]); // 替换 值， 修改原数组。
		// start 开始索引值， deleteCount 删除(替换)多少个， [,item1] 可选,当有item 时 是添加。
		// return 删除 已删除的数组， 或 []。
		// splice 拼接， 用什么拼接。第三个参数不传就是''. 删除。 有则是添加
arr.pop(); // 尾部弹出， 修改原函数。
		// return 弹出的值

arr.copyWithin(target[, start[, end]]); //改变原数组,把从start,到 end 这一段，移动到 target
		// arr.copyWithin(0,3,4); 把 arr[3-4] 这一段 移动到 arr[0]
		// return 改变后的数组。 原数组会改变
arr.entries(); // 返回一个新的迭代器对象
		// next().value



```



```javascript




```



