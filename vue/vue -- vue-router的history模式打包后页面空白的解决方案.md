欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 前言
采坑记录，以便后面翻阅

首先你需要确认页面空白不是由资源文件路径不正确引起的，如果资源找不到就将绝对路径改为相对路劲，具体解决方案看这里：[webpack--资源和css中图片引用打包为相对路径的方案](https://blog.csdn.net/wxl1555/article/details/81105204)

### 问题现象
在本地开发环境没有任何问题，路由也正常显示，但是打包并部到服务器之后，访问页面就是空白，看控制台也没有报错，当时就是懵逼状态！！

仔细想一下，history模式下就是在操作html5的history的一些api，所以肯定是url出了问题。

### 分析问题
本地开发环境中，我们访问的地址为:
```
localhost:8888
```
以上没什么毛病，一切都好使

但是，我们的项目并没有部署在nginx的根目录，而是在根目录的/aaa/目录下

所以我们默认的访问地址为：
```
www.xxxx.com:9999/aaa/   

//即去找aaa目录下的index.html文件

// 等价于开发环境的 localhost:8888


```
这里问题就来了，我们配的路由中并没有aaa，所以我们的路由不认识aaa，这就是问题

找到问题之后去看了下官方文档，还真找到了解决方案，请看这里[官方文档](https://router.vuejs.org/zh/api/#base)

解决方案就是给路由中加一个base的属性，值为 '/aaa'即可
![image](http://olv6wm3nj.bkt.clouddn.com/18-7-25/61418914.jpg)

### 引深
如果我们要直接访问某个路由，是不是直接在地址栏里输入url + 路由地址，例如
```
www.xxxx.com:9999/aaa/login
```
但是，当我们敲了回车之后，页面上一个很大的404

为什么呢？

我们来看一下后台服务器是如何处理个请求的，服务器会默认去找aaa文件夹下面的login文件，如果没找到就去找aaa/login/下面的index.html文件，如果没找到就会返回给前台404页面；

像这种直接在浏览器地址栏直接输入一个路由地址时，我们的路由值起不到任何作用的，只会返回404；

解决方案就是在后台服务器去做一些操作，官方文档也有这部分的说明，[文档](https://router.vuejs.org/zh/guide/essentials/history-mode.html#%E5%90%8E%E7%AB%AF%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90)

由于我们项目不是部署在根目录下，所以和官方给出的解决方案有点不太一样，我们用的是nginx；

```
location /aaa {
    root home/xxx/www   //你自己的根目录地址
    try_files $uri $uri/ /aaa/;     //这里的 /aaa/ 也可以写成/aaa/index.html
}
```
$uri为变量，代表你访问的地址。

上面配置的意思大概是，如果访问aaa/文件夹下面的某个文件，找不到时就返回/aaa/下面的index.html文件

这样之前的问题就解决了


我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[https://github.com/vue -- 如何去掉url默认的锚点#.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/vue/vue%20--%20%E5%A6%82%E4%BD%95%E5%8E%BB%E6%8E%89url%E9%BB%98%E8%AE%A4%E7%9A%84%E9%94%9A%E7%82%B9%23.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com