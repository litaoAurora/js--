###  原生ajax 

1. 创建对象 XMLHttpReqest 对象
var xhr = new XMLHttpRequest();

2. 准备发送
xhr.open('get'," ./check.php?username=' ' " ,'true') ; //三参数  method url bool(是否异步)
			url可以带数据
3. 执行发送动作
xhr.send(null);  //必须有参数  get->null  post->

4. 指定回调函数
xhr.onreadystatechange = function(){}  
xhr.readyState  准备状态 number  4 准备好了，已发送
xhr.status 状态码  200
xhr.responseText  返回来的数据


兼容： 
var xhr = new XMLHttpRequest(); 
var xhr = new ActiveXobject("Microsoft.XMLHTTP"); //IE 老

post:
param = "name=122";

xhr.setRequestHeader("content-Tyoe","application/x-www-form-urlencode");
xhr.send(param);

xhr.onreadystatechange = function(){}
当readystate 的值改变时 就调用
readystate ->0 		  初始化时，xhr （创建或初始化)
readystate -> 1     	发送请求
readystate -> 2		  拿到了数据，(为解析)
readystate -> 3              正在解析
readystate -> 4		  解析完成


s
