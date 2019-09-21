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
```

```javascript

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



s

```javascript


function replacer(count) {
  // p1 is nondigits, p2 digits, and p3 non-alphanumerics
  count++;
  console.log(arguments);
  return count;
}

var newString = 'abc12345#$*%'.replace(/([^\d]*)(\d*)([^\w]*)/, ()=>{
  var conut=1 ;
  var arg = arguments;
  replacer(arg);
});
console.log(newString);  // abc - 12345 - #$*%
```

报错了。



