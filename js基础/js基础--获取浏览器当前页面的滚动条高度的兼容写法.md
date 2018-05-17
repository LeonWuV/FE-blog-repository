##### 欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
在开发中，兼容性问题是最常见的，今天就来介绍一下关于获取滚动条高度的兼容性写法，宽度同理，我在这里就不一一解释了
#### 各浏览器的写法
- IE6/7/8 

```
document.documentElement.scrollTop
```
- IE9以上

```
window.pageYOffset或者document.documentElement.scrollTop
```
- Safari

```
window.pageYOffset 与document.body.scrollTop
```

- Firefox

```
window.pageYOffset 或者 document.documentElement.scrollTop
```

- Chrome

```
document.body.scrollTop
```
#### 具体的写法
通过上面列出的主流浏览器的兼容性，其实我们不难看出，其实只要我们判断到document.body.scrollTop和document.documentElement.scrollTop就会包括上面所有的浏览器；故最终的写法

```
var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
console.log(scrollTop);
```
如果需要监听滚动条，那么就监听onscroll事件即可；如

```
document.body.onscroll = function(){
    var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
    console.log(scrollTop);
}
```

**我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**