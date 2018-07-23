欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
vue项目中持续踩坑做一些记录，以便后面翻阅

项目的url中会自带#，看起来很不是舒服，其实是vue-router在搞怪，router跳转有两种实现方式：
1. hash（带#）值模式，vue-router 默认 hash 模式 —— 使用 URL 的 hash 来模拟一个完整的 URL，于是当 URL 改变时，页面不会重新加载；

2. history模式，如果不想要很丑的 hash，我们可以用路由的 history 模式，这种模式充分利用 history.pushState API 来完成 URL 跳转而无须重新加载页面。

### history模式
vue-router默认是hash模式的，我们要切换到history模式，只需在router初始化时，设置mode为history即可。[官方文档](https://router.vuejs.org/zh/guide/essentials/history-mode.html#%E5%90%8E%E7%AB%AF%E9%85%8D%E7%BD%AE%E4%BE%8B%E5%AD%90)

```
new Router({
  mode: 'history',
  routes: [ ]
})
```
这里面还有一些问题，就是需要考虑到用户直接输入URL的页面不存在的情况，显示404感觉会不舒服。

这时我们需要有一个通用的页面，当404时就返回这个页面，当然这个页面可以为你的主页，也可以为其他提示页面，我是这么处理的
```
new Router({
  mode: 'history',
  routes: [
    {
      path: '*',
      name: 'allPage',
      component: AllPage
    }
  ]
})
```
通用的页面，如果404就跳转到此页面

### 修改默认页
我们知道router默认显示的页面是配置项中的 '/'，如果我们需要让页面打开默认显示 '/home'页面呢，这里就引出了路由的重定向配置，具体如下图

![image](http://olv6wm3nj.bkt.clouddn.com/18-7-23/47168145.jpg)

如果您觉得我没讲清楚，可以跳转至[官网文档](https://router.vuejs.org/zh/guide/essentials/redirect-and-alias.html#%E9%87%8D%E5%AE%9A%E5%90%91)查看

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[https://github.com/vue -- 如何去掉url默认的锚点#.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/vue/vue%20--%20%E5%A6%82%E4%BD%95%E5%8E%BB%E6%8E%89url%E9%BB%98%E8%AE%A4%E7%9A%84%E9%94%9A%E7%82%B9%23.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com