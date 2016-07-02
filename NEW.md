```javascript




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
