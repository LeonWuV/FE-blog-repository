## 方法
	

### 1. 在iframe中查找父页面元素的方法：
	jQuery的方法：$("#id",window.parent.document)
	
	原生的方法：window.parent.document.getElementById("#id");
	
		
	//有时候iframe会嵌套好几层，那么嵌套两层时就是：
	window.parent.parent.document.getElementById("#id"); //以此类推
	
	//嵌套好几层，直接找最顶层可以用这个方法
	window.top.document.getElementById("#id");

###  2.在iframe中使用父页面的变量或者方法函数
	parent.method
	
	parent.variable
## 实例

```
<!-- 父页面 iframeParent.html-->
	<body>
		<div id="parentBox">我是爸爸</div>
		<iframe src="iframeChildren.html" width="300px" height="200px"></iframe>
	</body>
	
	<script type="text/javascript">
		var _parent = 'hello';
		var _parent1 = 'world';
		
		function methodParent(){
			console.log( _parent);
		}
	</script>
```

```
<!--  内嵌的iframe页面 iframeChildren.html-->
	<body>
		<div id="childrenBox">我是孩子</div>		
	</body>
	
	<script type="text/javascript">
		//jQuery操作父页面的元素
		$("#parentBox",parent.document).css('color','red');
		
		//原生的方法操作父页面元素
		var parentRed = window.parent.document.getElementById("parentBox").style.backgroundColor = 'blue';
		
		//调用父页面的方法
		parent.methodParent();
		
		//使用父页面的变量
		var _children = parent._parent1;
		
		console.log(_children);		
	</script>
```

### 上面实例结果
![这里写图片描述](http://img.blog.csdn.net/20170829153004689?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**
