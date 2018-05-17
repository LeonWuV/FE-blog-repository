####  先简单介绍一下各个属性

1. ::-webkit-scrollbar        滚动条整体部分，其中的属性有width,height,background,border等。
2. ::-webkit-scrollbar-button  滚动条两端的按钮。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。
3. ::-webkit-scrollbar-track         外层轨道。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。
4. ::-webkit-scrollbar-track-piece  内层轨道，具体区别看下面gif图，需要注意的就是它会覆盖第三个属性的样式。
5. ::-webkit-scrollbar-thumb     滚动条里面可以拖动的那部分
6. ::-webkit-scrollbar-corner   边角，两个滚动条交汇处
7. ::-webkit-resizer        两个滚动条交汇处用于拖动调整元素大小的小控件（基本用不上）


![属性解释图，有注释](http://img.blog.csdn.net/20171222112553383?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
    
####  下面看几组比较

---
##### 效果一

![效果图1](http://img.blog.csdn.net/20171222112626423?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


上图滚动条效果的css代码,默认此部分为原始代码，后面修改都是在此基础上修改



```
/*css主要部分的样式*/

/*定义滚动条宽高及背景，宽高分别对应横竖滚动条的尺寸*/

		::-webkit-scrollbar {
		    width: 10px; /*对垂直流动条有效*/
		    height: 10px; /*对水平流动条有效*/
		}
		
		/*定义滚动条的轨道颜色、内阴影及圆角*/
		::-webkit-scrollbar-track{
		   	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
		   	background-color: rosybrown;
		  	border-radius: 3px;
		}
		
		    
	   /*定义滑块颜色、内阴影及圆角*/
		::-webkit-scrollbar-thumb{
		    border-radius: 7px;
		    -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
		    background-color: #E8E8E8;
		}
		
	    /*定义两端按钮的样式*/
	    ::-webkit-scrollbar-button {
	        background-color:cyan;
	    }
	    
	    /*定义右下角汇合处的样式*/
	   ::-webkit-scrollbar-corner {
	        background:khaki;
	    }

```

---
##### 效果二
在上面原始代码上加如下代码

```

        ::-webkit-scrollbar-track-piece {
        	background-color: darkred;
        		    
        }

```
![效果图2](http://img.blog.csdn.net/20171222112854508?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

可看出覆盖了之前::-webkit-scrollbar-track属性的样式

---
##### 效果三
在上面原始代码上加如下代码

```

        ::-webkit-scrollbar-track-piece {
        	background-color: darkred;
        	background-image:url(https://www.baidu.com/img/baidu_jgylogo3.gif);
        		    
        }

```
![效果图3](http://img.blog.csdn.net/20171222113030621?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

现在是不是能理解上面说的内层轨道和外层轨道之分了


---
##### 效果四

将原始代码的::-webkit-scrollbar-track属性改为

```

        ::-webkit-scrollbar-track{
		   	-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
		   	background-image:url(https://www.baidu.com/img/baidu_jgylogo3.gif);
		   	background-color: rosybrown;
		  	border-radius: 3px;
		}

```
![效果图4](http://img.blog.csdn.net/20171222113201284?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvd3hsMTU1NQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


大家仔细观察上面的几种情况，得出结论。

---
**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**