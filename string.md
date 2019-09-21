- 模板字面量
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