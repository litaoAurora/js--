
proxy :   代理模式 ， 拦截。 
类似于 ： python 的魔术方法。 
语法：  new Proxy( target, handler );  

target : 是目标对象
handler : {  get(){}, set(){} }..
    handler -> ;;
        handler.getPrototypeOf
        handler.setPrototypeOf
        handler.isExtensible
        handler.preventExtensions
        handler.getOwnPropertyDescriptor()
        handler.defineProperty()
        handler.has
        handler.get
        handler.set
        handler.deleteProoperty
        handler.apply()    当目标对象为函数，且被调用时触发


## set

函数api : 
- add()      : 添加
- delete     : 删除
- clear      : 清除所有
- forEach    : 循环遍历
- entries    : 隐射
- keys       : 键
- values     : 值得集合
- size       : 长度
- toJSON     : 转数组或是对象的 api.


/[0-9]\.\d+|[1-9]\d*|[1-9]\d*\.\d+/


