### 先说原理
zoom和scale这两个东西都是用于对元素的缩放，但两者除了兼容性之外还有一些不同的地方。zoom缩放会将元素保持在左上角，而scale默认是中间位置，可以通过transform-origin来设置。另外他们执行的渲染顺序也不同zoom可能影响到盒子的计算。

### 我们看个例子
#### 这是几行伪代码
    <style>
	div {
	 	 width:300px;height:100px;
	  border:1px solid #CCC;
	  font-size:0px;
	  line-height:100px;
	  margin:10px;
	}
	span {
	  display:inline-block;
	  height:80px;width:200px;background:#F5F5F5;
	  vertical-align:middle;
	  overflow:hidden;
	}
	</style>
	

	----------

	<div>
	  <span style="-webkit-transform:scale(0.5);"></span>
	</div>
	<div>
	  <span style="
	    -webkit-transform-origin:top left;
	    -webkit-transform:scale(0.5);
	  "></span>
	</div>
	<div>
	  <span style="zoom:0.5;">
	  </span>
	</div>
#### 下面看效果
![这是上面的效果图](http://www.web-tinker.com/pictures/3c10006d368f755f48ebade31f496f00.png?_=4495393)
#### 稍微解释一下
第一个测试中只设置了scale，于是元素以自己的中心为基点做缩放。
第二个测试中不仅设置了scale，还有origin来将缩放的基点设置到左上角，因此变化结束后元素呆在了左上角。虽然容器设置了和高度一样的行高，当它并没有在容器里居中，因为scale是先布局后变换的，变换不会对布局产生影响。
最后一个测试是使用zoom，虽然Firefox上不支持，但这是个很古老的特性了。它和第二个测试的区别是它先缩放，后计算布局。所以在例子中它得到了垂直居中效果。