

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

## 遇到的问题
pages 的第一个配置项不是首屏 ： ->   把模式调为 插件模式。 


