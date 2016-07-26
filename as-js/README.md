#AS & JS

###AS要点

+ 必须导入包
+ addCallback中三个参数，一般其它地方搜索到的是两个

	import flash.external.ExternalInterface;
	function hello():String{  
	    return "js call flash";  
	} 
	ExternalInterface.addCallback("helloas",this,hello);
	ExternalInterface.call("changeImg");

