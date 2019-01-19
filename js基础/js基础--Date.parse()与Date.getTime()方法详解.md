欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
这两个方法的返回值都是 1970/1/1 午夜距离该日期时间的毫秒数
### 如何使用

下面的例子中，我们将取得从 1970/01/01 到 2017/03/19 的毫秒数

1、Date.parse()的使用

```
// 返回自定义时间戳
 Date.parse("2017/03/19")
 
//返回当前时间的事件戳
 Date.parse(new Date());

//结果为1489881600000

```

2、Date.getTime()的使用

```
var dateNow = new Date();
var ff = dateNow.getTime();
console.log(ff);
//打印出来的是1489899243209
```
3、巧妙写法 +new Date（）

```
var aa = + new Date();
console.log(aa);
//返回值为：1520218413266
```
4、new Date().valueOf()


```
var aa = new Date().valueOf();
console.log(aa);
//返回值为：1520218413266
```
5、Date.now()

```
var aa = Date.now();
console.log(aa);
//返回值为：1520218413266
```

以上这些方式都可以返回时间戳，选择其中的一两种记住，然后使用在日常的开发中

我的github资源地址：[js基础--Date.parse()与Date.getTime()方法详解](https://github.com/LeonWuV/FE-blog-repository/blob/master/js%E5%9F%BA%E7%A1%80/js%E5%9F%BA%E7%A1%80--Date.parse()%E4%B8%8EDate.getTime()%E6%96%B9%E6%B3%95%E8%AF%A6%E8%A7%A3.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com