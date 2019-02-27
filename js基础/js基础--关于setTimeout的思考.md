欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 先热身
看看下面的代码会打印出什么？

```
    for (var i = 0; i < 5; i++) {
	  	setTimeout(function () {
	   		console.log(i);
	  	}, 100);
	}
```

> 上面的结果是 5  5  5  5  5
 
 这里和浏览器的事件队列和事件循环机制（event loop）有关系。
 
 建议大家可以看这篇博文 [promise和setTimeout执行顺序的问题](https://blog.csdn.net/wxl1555/article/details/80054538)，我在这篇文章中有讲到这个问题。

也就是说，setTimeout是一个宏任务，它在事件队列里排在了script标签这个宏任务的后面。

浏览器会先执行第一个宏任务，也就是读取script标签中的代码，遇到setTimeout时，将其放进事件队列中等待执行，循环5次，也就是事件队列中放了5个setTimeout，这时第一个事件执行完毕，再执行下一个宏任务，也就是依次执行setTimeout，这时i已经变成了5，所以会打印出5 5 5 5 5；

### 那么上面的额代码我们改如何修改才能打印出0~4呢？

```
	for(var i = 0; i < 5; i++) {
		(function(k){				
			setTimeout(function() {
				console.log(k);
			}, 100);
		})(i);
	}
```

> 没错，上面的代码可以打印出我们想要的结果，他的结果为0~4，可是为什么呢？
> 
> 我们所采用的解决方案是闭包，闭包可以延长其私有变量的生命周期，意思就是内部私有变量和函数保存下来，一直在内存中，之后到你用时他再给你

### 那么我们可以再把上面的题目延伸一下

```
    for (var i = 0; i < 5; ++i) {
	  	setTimeout(function () {
	   		console.log(i);
	  	},0);
	}
		
console.log(0);
//在for循环后面加了段代码，而且把延时器事件的触发时间改为了0，请先想想结果会是什么？
```

> 可能有会两种想法
> 
> 第一种为：5  5  5  5   5  0；
> 
> 第二种结果为： 0 5  5  5  5   5；
> 
> 那么哪一种结果是正确的呢？
> 
> **其实正确结果是第二种**
> 
#### 为什么呢？

道理很简单，还是我在刚开始解释的那样，setTimeout是排在script标签之后的宏任务，先读取script标签时，首先会打印出0，然后再执行setTimeout事件，依次打印出5，可以理解这里其实和setTimeout的延迟执行时间没关系。


---
github文章资源地址：[js基础进阶--关于setTimeout的思考]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com



