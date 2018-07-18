## 前言
最近在用vue-cli+webpack做项目，项目架构搭好了之后，想build之后看看效果，但是build出来的index.html文件中的默认资源引用都是绝对路径，也就是相对于根目录的绝对路径；但是我项目如果部署到线上也不一定是在根目录里呀，所以这种默认相对于根目录的绝对路径肯定是不实用的；
## 解决方案
1. 我们的根目录下有个config文件夹，下面有个index.js，如下图，我们把build对象下的assetsPublicPath的值改为 './',代表当前路径，（之前的'/',表示根目录）

![image](http://olv6wm3nj.bkt.clouddn.com/18-7-18/22460434.jpg)

这样我们就解决了index.html中资源引用的问题，由原来的绝对路径改为了相对路径
2. 但是我们项目中css文件里的图片路径之前是不是这么写的
```
background: url("../../static/img/img.png")
```
打包后就变成了
```
background: url("./static/img/img.png")
```
这样肯定是不对的，所以css的资源引入路径也需要修改，我们打包后在dist文件下会有一个static文件夹，下面有一个img文件夹，里面放的是图片资源，同样在static文件夹下会有一个css文件，里面是我们的css文件，如下图

![image](http://olv6wm3nj.bkt.clouddn.com/18-7-18/73533934.jpg)

我们再来看一下，似乎我们之前css文件里的引用路径是没有问题的，所以我们就需要修改css打包的配置路径，我们打开build文件夹下的utils.js，在如下位置加上一段代码即可

![image](http://olv6wm3nj.bkt.clouddn.com/18-7-18/69751319.jpg)



我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com
