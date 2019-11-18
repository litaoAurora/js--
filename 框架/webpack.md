


## 四大核心概念
:核心是 在文件中有依赖才会打包。  有require() 就会打包。 

1. entry    入口
2. output   出口
3. loader   导航者: 处理 非 jsvascript文件
4. plugins  插件
5. model    模式



### entry 入口
> 入口配置就是 定义一个入口路径。 默认是 `.src` 

{ entry : './path/to/my/file.js' }



###  output 出口 
> 输出文件在哪里

```js
const path = require( 'path' );
{
    output : {
        path : path.resolve(  __dirname, 'dist' ),
        filename : 'my-first.bundle.js'
    }
}
```
`__dirname` : nodeJs中的一个全局的变量。 当前文夹路径字符串。 
`filename`  : 文件名。 


## loader 盗汗者
> 配置两个目标  test 和 use 

> test 尝试确定目标,  是个正则表达式
> use  确定用哪个  loader 

```js
{
    module :{
        rules : [
            { test : /\.txt$/, use : 'raw-loader' },
            { test : /\.css$/, use : 'css-loader' },
        ]
    }
}

module.exports = config; 
```
“嘿，webpack 编译器，当你碰到
    「 在 require()/import 语句中被解析为 '.txt' 的路径 」时，在你对它打包之前，先使用 raw-loader 转换一下。”
    「 在 require()/import 语句中被解析为 '.css' 的路径 」时，在你对它打包之前，先使用 css-loader 转换一下。”


## plugins
> loader 用于转换类型模块。 
> 而插件则可以执行范围更广的任务

使用插件 需要 require() 并添加到 plugins 数组中。 




## 在 npm 的配置文件中可以查看所有的 webpack 需要的包. 

`babel` 是一个将es6 转为 es5 的包
`vue-loader`   将 vue 文件转化为 js 的包。 


