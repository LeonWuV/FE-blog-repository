欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 定义
函数柯里化就是创建已经设置单个参数或者多个参数的函数，函数变为接受一个参数，返回一个值

### 来个例子
```
    function add(){
    
        // 将传进来的实参转换为数组arr
        var arr = Array.prototype.slice.call(arguments);
        var mun = 0;
        
        for (let i = 0; i < arr.length; i++) {
            mun += arr[i];
        }
        
        // 返回传进来的实参之和
        return mun;
    }

    function carrying(fn){
        // 获取要复用的参数，除去第一个参数并转化为数组
        var argsOut = Array.prototype.slice.call(arguments,1);
        
        return function (){
            // 取的自身的参数并转换为数组
            var argsInner = Array.prototype.slice.call(arguments);
            
            // 合并复用和自身的数组
            var argsTotle = argsInner.concat(argsOut);
            
            // 调用传进来的fn函数，并将数组元素，利用apply的特点依次传入fn
            return fn.apply(null,argsTotle);
        }
    }

    var a1 = carrying(add,4,6,7);  // 4,6,7 为复用参数
    // 这里的a1为carrying函数中return出来的匿名函数
        
    console.log(a1()); //17  这里自身参数没有

    console.log(a1(2,3,45,66)) //133  这里2,3,45,66为自身参数
    
    var a2 = carrying(add,1);

    console.log(a2(4,2,3,4,66)) // 80
    
```

我的github资源地址：[https://github.com/js基础进阶--函数柯里化carrying.md](https://github.com/LeonWuV/leonwuv.github.io/blob/hexo/source/_posts/js%E5%9F%BA%E7%A1%80%E8%BF%9B%E9%98%B6--%E5%87%BD%E6%95%B0%E6%9F%AF%E9%87%8C%E5%8C%96carrying.md)

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的博客园地址：[http://www.cnblogs.com/wuxiaolong555](http://www.cnblogs.com/wuxiaolong555)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com