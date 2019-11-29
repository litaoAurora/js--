

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

- 引入组件 ->  json.usingComponents:{  组件名：组件路径 }
- 获取共享数据 
    - this.properties.数据名  类 props
    - this.data.数据名   - 类 state

- 父传子
    - 现在组件自定义标签上 <Box msg="{{nsg}}">
    - 子组件 需要(全写)  properties : { msg:{
        type : String,
        value : ''
    } }

- 子传父  利用函数修改自身的 this 属性
    1.  父 ： 自定义函数 传给子组件调用
    2.  子 ： 触发  sonEvent,  this.trggerEvent( 'sonEvent', 子组件数据 )
- 兄弟传兄弟 。 (  A 传数据给 B )
    1. 父 ： 接受 A 的数据
    2. <A bindsondEvent='fn' />  子组件A触发 sonEvent 事件后触发父组件的 fn 方法。 
    3. A 触发 sonEvent, this.trggerEvent('sonEvent', num)
    4. B 组件 <Box num='{{num}}' />
    5. B 需要设置  
        properties : {
            num : { type : Number , value : 0 } } 

- 组件的 observers (就是 vue的 watch)  可以监听 data 数据和 properties 数据
    - 就是 监听的num 值发生变化是时 触发函数。 
    1. observers : {
        num (){  'obj.name'(){},  'obj.**'(){}  }
        }
- 小程序的计算属性  -> 结构是我可以理解的
    -  'count, price' : function(){
        this.setData({ total : count * price })
    }

- Behavior  是啥？？ 

- 页面跳转
    - wx.switchTab({ url : "相对文件地址" })
- 声明周期
    1. created() -> created
    2. attached()  -> beforeMount
    3. ready()    ->  mounted
    4. moved()   组件在页面的位置发生了变化触发
    5. detached()  组件从页面节点中被移除， 隐藏 触发。   

- 本地存储 

- 全局变量在 App.js 中设置。 


## 遇到的问题
pages 的第一个配置项不是首屏 ： ->   把模式调为 插件模式。 


mpvue, wepy 辅助开发。
![模拟数据的网站](http:www.easy-mock.com)







