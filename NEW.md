```javascript




*************************
0.0.6
+val	:
	$("#MYID").val()			//get value
	$("#MYID").val("VALUEX")	//set value
	$(".CLAS").val("VALUEX")	//set value for all object
	$("input").val("VALUEX")	//set value for all object
+css	:
	$("#MYID").css("text-align")	//get style "text-align"
	$("#MYID").css("text-align","center")	//set style
	$(".CLAS").css("text-align","center")	//suport array
	$(".CLAS").css({"text-align":"center","color":"red"})	//set styles
+html	:
	$(".CLAS").html()	//get html string suport array
	$(".CLAS").html("<div>New</div>")	//set html string suport array
+text	:
	$(".CLAS").text()	//get text string suport array
	$(".CLAS").text("New String")	//set text string suport array
+click	:
	$(".CLAS").click( function(){ alert(this.html()) } )	//suport array and events queue
	$(".CLAS").click( function(){ alert(this.html()) } ,1)	//
	//当前版本click支持事件队列，允许绑定N个函数，会按照绑定顺序依次执行
	//最后一个参数1指清空click事件队列，仅保留当前设置的函数
+next	:
	$(".CLAS").next()	//允许返回N个邻居元素的数组
	$("#MYID").next()	//仍然只返回一个DOM对象
+prev	:
	$(".CLAS").prev()	//允许返回N个前面元素的数组
	$("#MYID").prev()	//仍然只返回一个DOM对象
+parent	:
	$(".CLAS").parent()	//允许返回N个父元素的数组
	$("#MYID").parent()	//仍然只返回一个DOM对象
+remove	:
	$(".CLAS").remove()	//删除多个DOM
	$("#MYID").remove()	//删除一个DOM
+empty	:
	$(".CLAS").empty()	//清空多个DOM
	$("#MYID").empty()	//清空一个DOM
+before	:
	$(".CLAS").before()
	$("#MYID").before()
+after	:
	$(".CLAS").after()
	$("#MYID").after()
+append	:
	$(".CLAS").append()
	$("#MYID").append()
+prepend	:
	$(".CLAS").prepend()
	$("#MYID").prepend()
	
*************************
0.0.5
+cookie	:
	$.cookie()			//get all cookies
	$.cookie("k")		//get "k" cookie value
	$.cookie("www.qq.ee",$.now());	//set cookie use default config:[7 days, /]
	$.cookie("www.qq.ee",$.now(),{"expires":300,"path":"/","secure":1});	//set cookies
	$.cookie("")		//delete all cookie
	$.cookie("k","")	//delete "k" cookie
+$.https:	Check the protocol is http or https, not function, a bool-vale.

*************************
0.0.4
+each	:	Add sub-function return 1 to break loop.
*click	:	Fix click method is overwritten.




```
