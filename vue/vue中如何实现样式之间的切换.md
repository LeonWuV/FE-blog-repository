### 前言

 既然我们选择了vue，那么在做东西时就不要想着去操作dom，所有的都交给vue来解决。

下面来说一个很简单但是很常用的效果，可能人人都会用到这样的需求

### 请看下图

![这里写图片描述](http://img.blog.csdn.net/20170805170856509?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


----------


 导航栏的样式切换功能，如果我们使用jquery之类的东西来写，可能要写好多代码，那么我们用vue呢，
 


----------


### 代码如下


**html**

[附上vue中style与class绑定API](https://cn.vuejs.org/v2/guide/class-and-style.html#%E5%AF%B9%E8%B1%A1%E8%AF%AD%E6%B3%95)

```

<div id="wrap" class="box">
	<div v-for="(list,index) in navLists" class="nav" :class="{ red:changeRed == index}" @click="reds(index)">{{list.text}}</div>
</div>
```
**css**

```
			*{
				padding: 0;margin: 0;
			}
			.box{
				height: 40px;
				background: cyan;
			}
			.nav{
				line-height: 40px;
				display: inline-block;
				margin-left: 100px;
				cursor: pointer;
			}
			.red{
				color: red;
			}
```

**js**

```
//前提是必须引入vuejs哦！
var vm = new Vue({
			el:"#wrap",
			data:{
				navLists:[
					{
						"text":"首页"						
					},
					{
						"text":"组件"						
					},
					{
						"text":"API"						
					},
					{
						"text":"我们"						
					}
				],
				changeRed:0
			},
			methods:{
				reds:function(index){
					this.changeRed = index;
				}
			}
		});
```

仔细看看我们的js代码除了模拟的数据其实就只有一个简单的逻辑处理，比起之前的各种操作dom省了好多事。

有没有更喜欢vuejs啊

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**