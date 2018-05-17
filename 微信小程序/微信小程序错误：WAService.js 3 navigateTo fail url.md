
刚开始接触小程序，在做项目时会出现各种奇葩的问题，这里每天记录一点
### 错误： WAService.js:3 navigateTo:fail url "pages/location/location"
微信小程序页面跳转时，要跳转的目标页面需要在项目根目录下的app.json里注册，如果未注册就会报上面的错误

![根目录图片](http://olv6wm3nj.bkt.clouddn.com/17-11-30/520067.jpg)

如图，在pages里注册一下目标页面就能解决这个问题

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**