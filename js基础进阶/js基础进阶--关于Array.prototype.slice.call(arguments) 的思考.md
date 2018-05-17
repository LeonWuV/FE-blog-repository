欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

Array.prototype.slice.call(arguments)的作用为：强制转化arguments为数组格式，一般出现在框架活插件的源码中

### 如何理解

上面的代码等价于[ ].slice.call(arguments)

或者随便一个数组调用都行 [1,2,4].slice.call(arguments)  

因为，前面的调用者的作用只是沿着原型链向上找，最终找到Array为止，slice为Array原型上的一个方法

slice内部的实现原理大概是这样的

```
Array.prototype.slice = function(start,end){
     var result = new Array();
     start = start || 0;        // 如果不传则取默认值
     end = end || this.length;  // 如果不传则取默认值
     
     //this指向调用的对象，当用了call后，能够改变this的指向，也就是指向传进来的对象，这是关键
     for(var i = start; i < end; i++){
          result.push(this[i]);
     }
     return result;
}
```


数组和字符串都有slice方法

如果对slice不是很了解，请看这篇文章：[slice（）与splice（）的用法和区别你清楚吗？](https://blog.csdn.net/wxl1555/article/details/79388292)


call方法的作用为：改变调用者的this指向并且执行调用者，


```
    function fn(a){
        console.log(this.a);
        console.log(this);
    }
        
    var obj = {
        a : 2
    }

    fn.call(obj); //  2 
                  //  {a : 2} 
    // 解释一下 fn的this指针指向了obj ，并且执行了fn函数
 
```
如果对call方法还是没理解，请看这边文章       [js基础--深入理解call、apply、bind](https://blog.csdn.net/wxl1555/article/details/80327397)


arguments 为函数实参的一个集合，数据类型为对象类型

### 写一个例子吧

```
    function ary(){
        console.log(arguments,typeof arguments,arguments instanceof Object)
        
        // 自己实操一下  看看上面这行代码能打印出什么
        
        return [11,12].slice.call(arguments);
        
        //这里的[11,12]可以被替换为任意的数组，不影响结果
    }

        var a11 = ary(1,2,3,4,5,6,888,9,222);
        
        console.log(a11);   [1, 2, 3, 4, 5, 6, 888, 9, 222]
        console.log(typeof a11);            //"object"
        console.log(a11 instanceof Array);  //ture
        
        
```

### 技术延伸
其实要实现将arguments强制转化为数组，还有几种方式

#### 利用es6的Array.from()


```
    function fn(){
        var a = Array.from(arguments);
        var b = Array.from(arguments).slice(1);
        console.log(a);
        console.log(b);
    }
    
    fn(1,2,6,3,4,12);
    // 结果分别为 1,2,6,3,4,12  和 2,6,3,4,12

```


#### 利用es6的展开表达式


```
    function fn(){
        var a = [...arguments];
        var b = [...arguments].slice(1);
        console.log(a);
        console.log(b);
    }
    
    fn(1,2,6,3,4,12);
    // 结果分别为 1,2,6,3,4,12  和 2,6,3,4,12
    
```
本文完

---

github资源地址：[https://github.com/关于Array.prototype.slice.call(arguments) 的思考.md](https://github.com/LeonWuV/leonwuv.github.io/blob/hexo/source/_posts/js%E5%9F%BA%E7%A1%80%E8%BF%9B%E9%98%B6--%E5%85%B3%E4%BA%8EArray.prototype.slice.call(arguments)%20%E7%9A%84%E6%80%9D%E8%80%83.md)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com