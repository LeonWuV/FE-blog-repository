欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 前言
在github上clone了一个项目，npm install之后，启动项目时报了如题目的错误导致项目启动失败；
### 产生问题的原因
执行npm install命令时，其实是npm按照项目里的package.json文件来下载项目所有的依赖；

由于每个人的电脑环境等不同的问题，有些依赖会不支持当前的环境；

### 解决方案
先卸载之前的node-sass，然后再安装一遍node-sass就可以完美解决了，npm会自动智能的选择最新的并且支持本地环境的依赖；

#### 特别注意
node-sass被墙了，使用npm会下载失败，所以请用淘宝镜像cnpm下载或者使用翻墙软件下载；

cnpm的安装和使用请看这篇文章，[cnpm淘宝镜像的安装和使用方法](https://blog.csdn.net/wxl1555/article/details/71172285)
```
//先卸载node-sass
npm uninstall node-sass

//再安装node-sass
cnpm install node-sass -D
```




我的github资源地址：[nodejs -- Node Sass does not yet support your current environment解决办法]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com