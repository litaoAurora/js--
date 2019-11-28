

1. 注册账号
2. 微信公众平台注册 来注册。 
3. 下载一个专门的小程序开发工具 -> 工具
4. 前端和后端
5. 新建项目需要 Appid -> 登录成功  -> 开发设置。

undefined 是个变量耶  undefined = 100;


## 元素绑定事件
<button bindTap="fn" data-params="arguments" >
原生属性节点
- attribute  -> 属性集合
- dataset  -> data- 的集合

fn(ev){
    console.log(ev) 就是目标元素
    ev.currentTarget.dateset
    ev.currentTarget.attrbute
}

- 把数据绑定到内容 ： '{{ data }}'
- 把数据绑定到属性 ： id='{{data}}'

## 修改数据方法是 ?? 
this.setData({ key : val }, callback) ; 完成后的回调。

## 获取数据
this.data...
this

## 简单的修改响应数据
this.setData({
    'arr[0]' : 3
})

## triggerEvent  触发父组件传进来的函数(事件)


## 组件的生命周期
- create
- attached
- ready



## 标签对应

div ->  view


## 遇到的问题
pages 的第一个配置项不是首屏 ： ->   把模式调为 插件模式。 




至少3个。 项目。 
站长之家。 

