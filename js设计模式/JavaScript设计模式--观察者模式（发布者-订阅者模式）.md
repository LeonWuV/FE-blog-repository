欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)


### 简单列子

下面是实现发布—订阅模式的步骤：

1、先要指定好谁充当发布者（比如售楼处）

2、然后给发布者添加一个缓存列表，用于存放回调函数以便通知订阅者（售楼处的花名册）

3、最后发布消息的时候，发布者会遍历这个缓存列表，依次触发里面存放的订阅者回调函数（遍历花名册，挨个发短信）


```
    var publisher = {}; //定义发布者
    
    publisher.subHandlerList = []; // 定义发布者的缓存列表，来存放订阅者的回调函数
    
    publisher.listener = function (fn){ //  添加订阅者
        this.subHandlerList.push(fn); //订阅者的回调函数添加进缓存列表
    }
        
    publisher.trigger = function(){
        for(var i = 0,fn;fn = this.subHandlerList[i++];){
            fn.apply(this,arguments);
        }
    }
        
    publisher.listener(function(name){
        console.log('leon1收到' + name);
    });
        
    publisher.listener(function(name){
        console.log('leon2收到' + name);
    });

    publisher.trigger("哈哈");

```

参考文献: https://www.cnblogs.com/tugenhua0707/p/4687947.html



我的github资源地址：[https://github.com/.md]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的博客园地址：[http://www.cnblogs.com/wuxiaolong555](http://www.cnblogs.com/wuxiaolong555)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com