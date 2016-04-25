# JLite

[http://www.qq.ee](https://www.qq.ee/post/qqee_youMIGHTnotNEEDuseJQUERY_toobig_want_smaller_alternative.html)

###jquery太大了怎么替代？你可能并不需要jquery
---------------------------
#####如果你使用jquery只用到很少几个功能如选择器、取值赋值、遍历等，可以试试[JLite]，兼容jquery语法却只有4KB，你不需要引用额外js文件，复制原生代码到自己的js文件中即可替换jquery。
---------------------------
#####JLite是原生javascript编写的超薄封装。
#####支持 选择器、JSON、AJAX、COOKIE。
#####兼容 IE6+
---------------------------
```javascript
//onload
$(function(){alert("ok")});

//选择器，返回 Element 或 Element数组
//仅支持单一名称，不支持多条件/子孙选择
$("#MYID") //返回单个对象
$(".MYCLASS") //返回数组
$("div") //返回数组

//选择器的方法、Element对象的方法
var a=$("#MYID");alert(a.html());
$("#MYID").html() //不支持数组
$("#MYID").text() //不支持数组
$("#MYID").next() //邻居元素，不支持数组
$("#MYID").before("<a href="#">IM_NEW_LINK</a>") //加入内容，不支持数组
$("#MYID").after("<a href="#">IM_NEW_LINK</a>") //加入内容，不支持数组
$("#MYID").attr("DATA","value") //value参数忽略时为取值，否则为赋值，不支持数组
$(".MYCLASS").addClass("ABC") //支持数组
$(".MYCLASS").removeClass("ABC") //支持数组
$(".MYCLASS").toggleClass("ABC") //支持数组
$(".MYCLASS").each(function(k,v){...}) //选择器返回数组时内置遍历方法

//遍历
$.each($(".MYCLASS"),function(k,v){...}) //通过外部函数遍历
//$.each可遍历数组和对象
var a=[1,2,3];
var a={a:1,b:2,c:3};
$.each(a,function(k,v){
	alert(k+"===>"+v);
});

//返回数组或对象的长度，返回整数0~n
$.len(a)

//浏览器是否为ie，布尔值，非函数
$.ie

//返回10位长度时间戳(毫秒)
$.ms()

//返回13位长度时间戳(微秒)
$.us()

//返回时间字符如2015-01-10 01:24:55
//a参为10位长度时间戳，忽略则取当前时间
$.now(a)

//判断字符是否为数字(整数或浮点数)，返回布尔值
$.isnumber(s)


//json操作
//a参为字符返回解析后的对象
//a参为对象返回编码的json字符
var a={9999:"中文.a?",x:10,y:15,z:{z1:1,z2:222},arr:[{"a":1,"b":2},{"c":3,"d":4}]};
var b=$.json(a)
alert(b)
var a='{"9999":"\u6d93\ue15f\u6783\u002e\u005ca\u003f","x":10,"y":15,"z":{"z1":1,"z2":222},"arr":{"0":{"a":1,"b":2},"1":{"c":3,"d":4}}}';
var b=$.json(a)
alert(b.z.z2)


//cookie操作
//写入cookie，[键，值，参数(若忽略则过期时间为会话结束,path为/,secure为false)]
//expires的单位是天
$.cookie("www.qq.ee",$.now(),{"expires":7,"path":"/","secure":0});
alert($.cookie()); //取回全部cookie如[a=1;b=2;c=3]
alert($.cookie("www.qq.ee")); //取回对应键的值，不存在时返回空字符""


//ajax操作
$.ajax({
	type:"GET",
	url:"http://ip.taobao.com/service/getIpInfo.php?ip=8.8.8.8",
	url:"http://freeapi.ipip.net/8.8.8.8",
	dataType:"json",//json或空
	async:0,//异步，默认为1==true
	timeout:5000,//毫秒，忽略则不判定超时
	//data:"a=1&b=2",//仅POST时有效
	error:function(){
		alert("Error!");
	},
	success:function(s){
		alert("Ok:\n"+s);
		$.each(s,function(k,v){
			alert(k+"===>"+v);
		});
	}
});

//----------------------------------------------------------------
//其他用法请直接使用原生javascript方法，举例如下:

//事件绑定:
$("#MYID").onclick=function(){}
obj.onfocus=function(){}
obj.onchange=function(){}
window.onscroll=function(){}

//修改css/style:
$("#MYID").style.width="100px";
obj.style.display="inline-block";
obj.style.position='absolute';
obj.style.opacity=1;

//到顶部:
document.body.scrollTop=0;

//到网页底部:
document.body.scrollTop=$("#bot").offsetTop;

//修改src属性:
obj.src="/test.html?t="+$.ms();

//插入对象/代码:
var u=document.createElement("style");
u.innerHTML="div{color:red}";
document.head.appendChild(u);

//修改网页标题:
document.title="www.qq.ee";


```





