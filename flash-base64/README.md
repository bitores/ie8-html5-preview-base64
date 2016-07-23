#SWFObject完美解兼容各浏览器

###传统的方法

	<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000"codebase="<a href="http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,0,0">http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=7,0,0,0</a>" width="550" height="400" id="Untitled-1" align="middle"> 
	<param name="allowScriptAccess" value="sameDomain" /> 
	<param name="movie" value="mymovie.swf" /> 
	<param name="quality" value="high" /> 
	<param name="bgcolor" value="#ffffff" /> 
	<embed src="mymovie.swf" quality="high" bgcolor="#ffffff" width="550" height="400"name="mymovie" align="middle" allowScriptAccess="sameDomain" type="application/x-shockwave-flash" pluginspage="<a href="http://www.macromedia.com/go/getflashplayer">http://www.macromedia.com/go/getflashplayer</a>" /> 
	</object>


###用JS嵌入的方法

	用JS嵌入就是各有各的嵌入方法了，有嵌得好的有嵌得不好的。有人用 document.write 直接写，这法子说实话不大好，感觉 hack 成分多了，有点为了验证而验证的意思，而且没有体现出什么 JS 的优势。我觉得一个好的 JS 嵌入脚本，在保证 Flash 应有功能的基础上，要发挥 JS 的优势应该要有版本检测，要能很好解决可访问性问题（也就是用户在无法浏览 Flash 内容或禁用 JS 的时候应该如何处理的问题），要易于重复使用。
	我们这里要讲的是SWFObject这个解决方案：
	“SWFObject”是利用Javascript 插入flash，好处多多，代码简洁，不会出现IE6下的“单击此处以激活控件”的提示，并且能通过W3C验证。不同于传统的“object”插入flash的方法。
	SWFObject在新的2.x版本中，其最简单的调用竟只需一句话，并且不需要等待页面加载完成，这意味着你可以将这句话写在页面的任何地方。比以前的版本，要简便多了。


	<div id="swfid"></div> 
	<script type="text/javascript" src="swfobject.js"></script> 
	<script type="text/javascript">
	swfobject.embedSWF("test.swf", "swfid", "300", "120", "9.0.0", "expressInstall.swf"); 
	</script>
	
	注解：调用方法embedSWF——插入SWF文件，参数依次是@swf文件的地址；@用于装入swf文件的容器(如div)的id；@flash的宽度；@flash的高度（当然，这里的宽高都可以使用诸如100%这样的百分比来表示）；@正常播放该flash所需的最低版本；@当版本低于要求时，执行该swf文件，这里利用这个flash跳转到官方下载最新版本的flash插件。（该参数可以省略）在同一个页面插入多个flash到不同位置时，只要重复上面的语句，使用不同的容器id就可以了。