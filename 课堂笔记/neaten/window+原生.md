

## Location   -> url 对应网络地址。
> 位置地点 主要是 url 相关的信息

- href        完整的地址
- protocal    协议
- host        主机  
- port        端口  
- pathname    路径
- search      参数 -> query ?
- hash        哈希值 ->  flagment #  
- username
- password
- origin      源头 -> 未解析的原生字符 unicode ->   




## ajax 

#### 属性

#### 方法

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

