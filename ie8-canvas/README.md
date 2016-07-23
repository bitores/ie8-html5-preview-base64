
IE6、7、 8原本不支持canvas标签，google提供了一个有效的解决方法ExplorerCanvas，简称excanvas.js。
所以excanvas让canvas这项新技术提前开始普及，网页中足以不借助 flash嵌入绘图区域，并支持主流浏览器，但是动画特效方面现在还很难让IE用户接受。

虽然使用了excanvas.js但是在需要保存下载图片的时候要用到canvas.todataurl（）方法，ie8不支持这个方法，现在还没有有效的解决办法。
也不支持一切 与其实现相关的函数，如getImageData


图片绘入 canvas，调用 getImageData
var tdu = HTMLCanvasElement.prototype.toDataURL;
HTMLCanvasElement.prototype.toDataURL = function(type)
{
 var res = tdu.apply(this,arguments);
 //If toDataURL fails then we improvise
 if(res.substr(0,6) == "data:,")
 {
  var encoder = new JPEGEncoder();
  return encoder.encode(this.getContext("2d").getImageData(0,0,this.width,this.height), 90);
 }
 else return res;
}

Please note that Internet Explorer 8 has a limit of 32 KB for data URI. Versions below have no support.