欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 前言
promise为es6引进的语言标准，为异步编程的一种解决方案；

阅读此文的前提是了解浏览器event loop的机制，还有promise的基本用法和特性，比如他自执行特性、状态不可逆特性等

### 抛出问题
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
 
### 重要概念
event loop 的概念

- Javascript是单线程的，所有的同步任务都会在主线程中执行。

- 当主线程中的任务，都执行完之后，系统会 “依次” 读取任务队列里的事件。与之相对应的异步任务进入主线程，开始执行。
- 异步任务之间，会存在差异，所以它们执行的优先级也会有区别。大致分为 微任务（micro task，如：Promise、MutaionObserver等）和宏任务（macro task，如：setTimeout、setInterval、I/O等）。
- Promise 执行器中的代码会被同步调用，但是回调是基于微任务的。
- 宏任务的优先级高于微任务
- 每一个宏任务执行完毕都必须将当前的微任务队列清空
- 第一个 script 标签的代码是第一个宏任务
- 主线程会不断重复上面的步骤，直到执行完所有任务。

### 我的理解
我们来捋一遍代码的执行过程，

所有的代码都写在script标签中，所以读取所有代码是第一个宏任务，我们开始执行第一个宏任务。

我们首先遇到setTimeout，他是第二个宏任务，将它扔进宏任务事件队列里先排队。

下来我们遇到promise，promise执行器里的代码会被同步调用，所以我们依次打印出2和3。

下来遇到promise的回调，他是一个微任务，将它扔进微任务事件对列中。

下来我们接着打印出5，然后执行微任务并且打印出4.

我们第一个宏任务执行完毕，执行下一个宏任务，打印出1，到此，所有任务都执行完毕。

所以我们最后的结果为2 3 5 4 1。

##### 结束

github资源地址：[js基础进阶--promise和setTimeout执行顺序的问题](https://github.com/LeonWuV/FE-blog-repository/blob/master/js%E5%9F%BA%E7%A1%80%E8%BF%9B%E9%98%B6/js%E5%9F%BA%E7%A1%80%E8%BF%9B%E9%98%B6--promise%E5%92%8CsetTimeout%E6%89%A7%E8%A1%8C%E9%A1%BA%E5%BA%8F%E7%9A%84%E9%97%AE%E9%A2%98.md)

csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com
