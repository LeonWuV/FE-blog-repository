欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

#### 前言
promise为es6引进的语言标准，为异步编程的一种解决方案；

阅读此文的前提是了解promise的基本用法和特性，比如他自执行特性、状态不可逆特性等

#### 抛出问题
且看下面代码和问题
```
setTimeout(function(){console.log(1)},0);
new Promise(function(resolve){
    console.log(2)
    for( var i=0 ; i<10000 ; i++ ){
        i==9999 && resolve()
    }
    console.log(3)
}).then(function(){
    console.log(4)
});
console.log(5);
// 这的问题是，为什么答案是 2 3 5 4 1
// 而不是 2 3 5 1 4
 ```
 既然promise.then和setTimeout都是异步的，那么在事件循环队列中  promise.then的事件应该排在setTimeout后面，那为什么promise.then却在setTimeout前面被打印了出来？
 
#### 答案

这个问题，我是这么理解的，浏览器读取script标签中的代码也是一个事件队列，Promise的任务会在当前事件循环末尾中执行，而setTimeout中的任务是在下一次事件循环执行

![image](https://segmentfault.com/img/bVPkJb?w=1350&h=926)

上图为《你不知道的JavaScript》中卷中第二部分的第一章第5小节的内容


github资源地址：[https://github.com/promise和setTimeout执行顺序的问题.md](https://github.com/LeonWuV/leonwuv.github.io/blob/hexo/source/_posts/promise%E5%92%8CsetTimeout%E6%89%A7%E8%A1%8C%E9%A1%BA%E5%BA%8F%E7%9A%84%E9%97%AE%E9%A2%98.md)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com
