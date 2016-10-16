# JLite

[http://www.qq.ee](https://www.qq.ee/post/qqee_youMIGHTnotNEEDuseJQUERY_toobig_want_smaller_alternative.html)

###jquery太大了怎么替代？你可能并不需要jquery
---------------------------
#####如果你使用jquery只用到很少几个功能如选择器、取值赋值、遍历等，可以试试[JLite]，兼容jquery语法却只有4KB(gzip压缩后1.5KB)，你不需要引用额外js文件，复制原生代码到自己的js文件中即可替换jquery。
---------------------------
#####JLite是原生javascript编写的超薄封装
#####支持 JSON、选择器、AJAX、COOKIE
#####支持 onclick、window.onscroll 事件队列
#####兼容 IE6+
---------------------------
###CDN with http&https
#####//dn-cdncdn.qbox.me/jlite.min.last.js
#####//dn-cdncdn.qbox.me/jlite.min.0.0.6.js
---------------------------
```javascript
//onload
$( function(){alert("ok")} );


//选择器，返回 Element 或 Element数组
//仅支持无空格字符串，不支持多条件/子孙选择如: $("DIV #MYID") 或 $("#MYID.CLAST")
$("#MYID") //返回单个对象
$(".MYCLASS") //返回数组
$("div") //返回数组
//可选参数2指定父亲元素，用于选择子孙元素。留空时父亲为 document.body
$( ".item", $("#IDx") )
//例：所有 .onetab 元素被单击时，弹出触发元素中第3个 .lit 的内容
$(".onetab").click(function(){
	alert( $(".lit",this)[2].html() );
});


//选择器的方法、Element对象的方法
var a=$("#MYID");alert(a.html());
$(".CLAS").html("V") //v参数忽略时为取值，否则为赋值
$(".CLAS").text("V") //v参数忽略时为取值，否则为赋值
$(".CLAS").attr("DATA","v") //v参数忽略时为取值，否则为赋值
$(".CLAS").val("v") //v参数忽略时为取value值，否则为赋值
$(".CLAS").next() //取弟元素
$(".CLAS").prev() //取兄元素
$(".CLAS").parent() //取父元素
$(".CLAS").remove()
$(".CLAS").empty()
$(".CLAS").before('<a href="#">QQEE</a>') //头部添加兄弟对象
$(".CLAS").after('<a href="#">QQEE</a>') //尾部添加兄弟对象
$(".CLAS").append('<a href="#">QQEE</a>') //尾部添加子对象
$(".CLAS").prepend('<a href="#">QQEE</a>') //头部添加子对象
$(".CLAS").addClass("ABC")
$(".CLAS").removeClass("ABC")
$(".CLAS").toggleClass("ABC")
$(".CLAS").each( function(k,v){...} ) //选择器返回数组时内置遍历方法


//css
$("#MYID").css("text-align") //取值
$(".CLAS").css("text-align","center") //赋值
$(".CLAS").css( {"text-align":"center", "font-size":"14px", "background-color":"#d0d0d0"} ) //连续赋值




//事件队列支持，可以为单个/多个元素绑定函数，多次绑定会在触发时按绑定顺序执行

//window.onscroll
//参数2可忽略，当参数2非空时清空队列中其他函数
$.onscroll(function(){
	console.log(document.body.scrollTop); //滚动时显示顶部坐标
},1); //参数2为1，将清除旧绑定，此时队列中只有当前函数
$.onscroll(function(){
	console.log(new Date().getTime()); //滚动时显示时间
}); //参数2被忽略，此时队列中有2个函数，窗口滚动时将依次执行上述2个函数

//onclick
//参数2可忽略，当参数2非空时清空队列中其他函数
$(".MYCLASS").click(function(){ //为全部 .MYCLASS 元素绑定 click 事件
	alert(this.html());
},1); //参数2为1，将清除旧绑定，此时队列中只有当前函数
$(".MYCLASS").click(function(){
	console.log(this.text());
}); //参数2被忽略，此时队列中有2个函数，click触发时将依次执行上述2个函数




//遍历
//遍历函数返回1时停止遍历
$.each($(".MYCLASS"),function(k,v){...}) //通过外部函数遍历
//$.each可遍历数组和对象
var a=[1,2,3];
var a={a:1,b:2,c:3};
$.each(a,function(k,v){
	alert(k+"===>"+v);
	return 1; //此处返回1时停止遍历
});


//返回数组或对象的长度，返回整数0~n
$.len(a)

//浏览器是否为ie，布尔值，非函数
$.ie

//网站是否采用https，布尔值，非函数
$.https

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
//写入cookie，[键，值，参数(若忽略则过期时间为会话结束,path为/,secure)]
//expires的单位是天
$.cookie() ////取回全部cookie如[a=1;b=2;c=3]
$.cookie("k") ////取回对应键的值，不存在时返回空字符""
$.cookie("www.qq.ee",$.now()); //set cookie use default config:[7 days, /]
$.cookie("www.qq.ee",$.now(),{"expires":300,"path":"/","secure":1}); //set cookies
$.cookie("") //delete all cookie
$.cookie("k","") //delete "k" cookie


//ajax操作
$.ajax({
	type:"GET",
	url:"/test.json",
	async:1,//异步，默认为1==true
	dataType:"json",//json或空
	timeout:5000,//毫秒
	headers:{//HTTP额外头部
		"Content-type":"application/x-www-form-urlencoded",
		A:"AAA",
		B:"BBB"
	},
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

//原生取value
$("#MYID").value.length

//原生事件绑定:
$("#MYID").onclick=function(){}
obj.onfocus=function(){}
obj.onchange=function(){}
obj.onblur=function(){}
window.onscroll=function(){}
document.onkeydown=function(ev){
	var e=ev||window.event||arguments.callee.caller.arguments[0];
	console.log("["+e.keyCode+"]");
};

//原生修改css/style:
$("#MYID").style.width="100px";
obj.style.display="inline-block";
obj.style.position='absolute';
obj.style.opacity=1;

//到顶部:
document.body.scrollTop=0;

//到网页底部:
document.body.scrollTop=$("#bot").offsetTop;
document.body.scrollTop=document.body.scrollHeight;

//原生修改src属性:
obj.src="/test.html?t="+$.ms();

//原生插入对象/代码:
var u=document.createElement("style");
u.innerHTML="div{color:red}";
document.head.appendChild(u);

//修改网页标题:
document.title="www.qq.ee";

//timer
setInterval(function(){...},1000);
setTimeout(function(){...},1000);


```





