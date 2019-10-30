
index.less

1 视口设置  width=device=width; 可视宽度=逻辑宽度， initial-scale=1.0 ： 初始化宽度为1 
   `user-scalable=no`   : 禁止用户缩放



2 配置 rem 

var iW = document.documentElement.clientWidth;
iW = iW > 1080 ? 1080 : iW ;  // 最大适配 1080 。

document.querySelector('html').style.font-size = iW / 8 + 'px';

是否大于 1080px ; 

