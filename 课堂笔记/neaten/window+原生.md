

## Location   -> url 对应网络地址。
> 位置地点 主要是 url 相关的信息

- href        完整的地址
- protocal    协议
- host        主机  
- port        端口  
- pathname    路径
- search      参数 -> query       ?username=jjj&password=...&22222
- hash        哈希值 ->  flagment #  
- username
- password
- origin      源头 -> 未解析的原生字符 unicode ->   




:  encodeURI  decodeURI , JSON JSON.parse  JSON.strigfy()  FormData FileReader
## ajax   有兼容性。 
构造函数   :  XMLHttpRequest()
IE       :   activeXobject()

#### 属性
```
状态 ：         readyState      获得当前的状态值 0-4
响应正文 ：      response
响应文本 ：      responseText
响应类型 ：      responseType    值有  "" document json text ...被视为什么作为解析
响应URL :       responseURL     
服务端的转态码 :  state            200   404  
文本状态码 :     stateText   'ok' 'not found'
响应超时     :   timeout 
事件追踪器 :     upload  
XML状态改变事件 : onreadystatechange   对应readyState 的状态。 
```
![状态值](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/readyState)
#### 方法
```
+ open( method, url, async, user, password )     : 始化一个请求
- overrideMimeType( Mimetype )        : 指定一个MIME类型用于替代服务器指定的类型
+ setRequesHeader( header, value )    : 设置请求头;  post 的send 需要 ContentType : application/x-www-form-encoded. 
+ send( FormData data )               : 参数 请求主体( 请求数据 )；如果请求方法是 GET,HEAD， null。因为get的请求数据在 url 中。 
- getAllResponseHeaders()             :   获取所有的响应头
+ getResponseHeader(name)             :   获取所有的响应头
- abort()                             :   手动终止请求

```
![open方法](https://developer.mozilla.org/zh-CN/docs/Web/API/XMLHttpRequest/open)
#### 请求方式 与 差别

- get 

1. 数据在 url 的后面拼接
2. url 长度有限制 4k
3. 安全性较差一点

- push 

1. 数据在 form-data 中 ( 在 send 方法中。  )
2. 数据大小理论上可以无限  当时后端有配置 post_max_size = 10m
3. 安全性较比 get 要高一点。 
4. 请求头中需要做编码格式设置  Content-Type

##### 编码格式 与含义 Content-Type
```
1. text/plain                               纯文本格式     ->   plain 平原的， 无格式的。 
2. application/x-www-form-urlencoded        键值对的格式    ->  send 中数据直接拼接在 send的的个参数中就可以了。 
3. multipart/form-data                      非文本格式      -> 音频等大文件 一般是多个包的二进制编码
```

##### 服务端状态码
https://baike.baidu.com/item/HTTP%E7%8A%B6%E6%80%81%E7%A0%81/5053660?fr=aladdin

200 成功
301 永久重定向
400 错误请求
403 没有权限    fortidden
404 资源找不到  Not Found
405 请求方法不对 method no allowed 





## FileReader  缓冲文本读取
> io 操作， 渲染， 动画， 等等 需要过程的都是 异步函数
### 属性

```
error        : 
onabort      : 
readyState   : 表示当前读取状态
result       : 结果
```

### 方法
```
abort()                      
readAsArrayBuffer()       
readAsBinaryString()        
readAsBinaryString()    
readAsDataURL()         : 拿缓存的内容url
readAsText()            : 
```


## FormData  把ajax  要发的数据在这里编码
> 一种表示表单数据的键值对的构造方式

构造函数 ： 
    new FormData( <form> )  : form 是 <form> 表单元素


## 方法
```
append( name, value [, filename] );
delete( name )
entries() ;     放回值 是个二维迭代器。 [[name, value],[]]
get( name );     name 的第一个值。 
getAll( name );  -> name 的所有值 [value1, value2 ]
has()  
keys()        :  Iterator 接口
values()      :  Iterator 接口
```



## 概念

1. 纯对象 -> 上一级的 原型链是 Objct.prototype 就是纯对象
2. 跨域 浏览器有限制 -> 同源策略 -> 域名 协议 端口相同
3. 前后端分离 -> 服务器不同， 开发人员 有分

4. 运算符优先级。 ++a 是真的运算符高于 ++a
静态作用域 (词法作用域)


实现跨域的手段 ： 
1. nginx 反向代理
2. jsonp 需要后端配合指定数据形式
3. window.postMessage  -> open(url).postMessage('data', url)
4. iframe 标签。 
5. window.domain  www.baidu.com  ->  aaa.daidu.com 可以跨域。。 