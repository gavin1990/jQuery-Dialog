jQuery-Dialog
=============

一段简单的jQuery弹出层代码，适用于提示，弹出层，不固定大小.......

源代码：

```
<!Doctype html>
<html>
<head>
<meta charset="utf-8">
<title>弹出层</title>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script>
$(function(){
	var x_Dialog ={
		/**定位弹出层*/
	    dialogBox: function(){
			var objW = $(window),
			objC = $(".dialog"),
			brsW = objW.width(),
			brsH = objW.height(),
			sclL = objW.scrollLeft(),
			sclT = objW.scrollTop(),
			curW = objC.width(),
			curH = objC.height(),
			left = sclL + (brsW - curW)/2,
			top = sclT + (brsH - curH)/2;
        objC.css({"left":left,"top":top});
		},
		/**弹出层位置响应*/
		winResize:function(){
			$(window).resize(function(){
			   if(!$(".dialog").is(":visible")){
				   return;
			   };
			   x_Dialog.dialogBox();
			});
		},
		close:function(){
				$(".dialog").removeClass("dialog").hide();
				$(".mask").hide();
		},
		/**显示弹出层*/
		showDialog:function(btn,boxCon){
			$(btn).click(function(){
				$(boxCon).addClass("dialog").show();
				x_Dialog.dialogBox();
				$(".mask").show();
			});
			x_Dialog.winResize();
		}
	};
	/********************************************/
	x_Dialog.showDialog("#tipShow","#dialog_1");
	x_Dialog.showDialog("#tipShow2","#dialog_2");
	$(".close").click(function(){
		x_Dialog.close();
	})
	
})
</script>
<style type="text/css">
html body{_width:100%;height:100%}
body{font-size:14px;padding:0;margin:0}
*{margin:0;padding:0}
.fr{float:right}
.mask{position:fixed;_position:absolute;top:0;left:0;display:none;width:100%;height:100%;background:#000;fiter:alpha(opacity=60);opacity:0.6;z-index:100}
.dialog{position:fixed;_position:absolute;border:3px solid #666;z-index:101}
.box1{width:360px;}
.box2{width:600px;}
.box1 .dia_til{padding:10px;background:#fbaf15;color:#fff}
.dialog .dia_til img{cursor:pointer}
.dialog .dia_con{height:40px;padding:35px 70px;background:#fff}
.dialog .dia_bom{text-align:center;background:#eee}
.btn{border:1px solid #666;padding:2px 10px;margin:10px;}
</style>
</head>

<body>
    <input type="button" id="tipShow" value="弹出层" class="btn">
	<div class="mask"></div>
	<div id="dialog_1" class="box1" style="display:none">
		  <div class="dia_til"> <img src="close.gif" width="20" height="20" alt="单击此处关闭" class="fr close"><strong>删除提示</strong></div>
		  <div class="dia_con">你真的要删除吗？</div>
		  <div class="dia_bom"><input type="button" value="确定" id="sure" class="btn"><input type="button" value="取消" id="cancel" class="btn close">
		  <div style="font-size:1px;clear:both"></div>
		  </div>
	</div>
	<input type="button" id="tipShow2" value="弹出层www" class="btn">
	<div id="dialog_2" class="box2" style="display:none">
		<div class="dia_til"> <img src="close.gif" width="20" height="20" alt="单击此处关闭" class="fr close"></div>
		<div class="dia_con">这里是内容区域，可以把对话框中的内容放在这！！！！</div>
		<div class="dia_bom"><input type="button" value="确定" id="sure" class="btn"><input type="button" value="取消" id="cancel" class="btn close">
		  </div>
	</div>
<div style="width:200px;height:1200px;background:#eee"></div>
</body>
</html>
```

