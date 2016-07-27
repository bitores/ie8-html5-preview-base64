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

+ as文件中只能写类 2.0

+ as3中行为只能写在时间轴上，而ad2可以写在元件上

	var fileRef:FileReference = new FileReference();
	fileRef.addEventListener(Event.SELECT, selectHandler);
	fileRef.addEventListener(Event.COMPLETE, completeHandler);
	fileRef.addEventListener(Event.OPEN, kais);
	button_1.addEventListener(MouseEvent.CLICK, chuan);

	function kais(event:Event) {
	        trace(fileRef.name);//获得文件名的方法
			ExternalInterface.call("console.log",fileRef.name);
	}

	function chuan(e:MouseEvent) {
	        var success:Boolean = fileRef.browse();
	}

	function selectHandler(event:Event):void {
	        var request:URLRequest = new URLRequest("http://php.dev/kqc/flash/upload.php");
	        try {
	                fileRef.upload(request);
	        } catch (error:Error) {
	                trace("Unable to upload file.");
	        }
	}
	function completeHandler(event:Event):void {
	        trace("uploaded");
			ExternalInterface.call("console.log","uploaded");
	}