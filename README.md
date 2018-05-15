<!DOCTYPE HTML>
<html>
<style>
img{width:100px;height:100px}
</style>
<body>
    <div id="src">
        <img draggable="true" src="b.jpg" id="b"/>
        <img draggable="true" src="c.jpg" id="c"/>
        <img draggable="true" src="d.jpg" id="d"/>
		<img draggable="true" src="e.jpg" id="e"/>
    </div>
	<div id="target" style="border-style:solid;width:200px;height:200px;margin-top:20px">
		<p>将选择的图片拖拽到这里</p>
    </div>
	<span id="msg"></span>
    <script>
        var src = document.getElementById("src");
        var target = document.getElementById("target");
		var msg = document.getElementById("msg");
        var draggedID;
		
		src.ondragstart = function (e) {//开始拖拽元素时触发
            draggedID = e.target.id; //获取拖拽对象ID
			//var img = document.createElement("img");
			//img.src = "a.jpg";
			//e.dataTransfer.setDragImage(img,-10,-10);
			//msg.innerHTML="开始拖拽："+img.src;
			msg.innerHTML="开始拖拽："+draggedID;
        }
/*
        target.ondragenter = function (e){//拖拽时鼠标进入目的元素时触发
			msg.innerHTML="进入目的元素";
			e.preventDefault();
		} 
		
       target.ondragover = function (e){//拖拽时鼠标在目的元素内移动时触发
			msg.innerHTML="在目的元素内移动";
			e.preventDefault();
		}
		*/
		///*
		target.ondrag = function (e){//拖拽时鼠标在目的元素内移动时触发
			msg.innerHTML="在目的元素内移动";
			e.preventDefault();
		}
		
		//*/
		src.ondragend = function (e){//拖拽动作结束时触发
			msg.innerHTML="结束拖拽";
		}
		
        target.ondrop = function (e) {//在目的元素内释放拖拽元素时触发
            var newElem = document.getElementById(draggedID).cloneNode(false);
            target.innerHTML = "";
            target.appendChild(newElem);
            e.preventDefault();
        }
        
    </script>
</body>
</html>
