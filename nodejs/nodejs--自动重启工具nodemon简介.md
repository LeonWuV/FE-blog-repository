欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 前言
我们在写nodejs时，是不是有这样的痛点，每次改完代码后都需要重启node服务，这个是很操蛋的事情。

### nodemon介绍
在这里，我要给大家介绍一个自动重启工具，他就是nodemon；

nodemon会监听项目路径下的文件，如果发生变化就会重启服务，那么他就完美解决了我们上面说的每次改完代码需要手动重启服务的痛点；

当然在github上也有很多相关功能的工具，比如forever、node-dev等，在这里我们主要说nodemon，如果你对其他的有兴趣，可以自行查看；

nodemon能流行起来的原因就是他使用简单，可配置性高；

### 如何使用

博主以npm包管理器为例，其他的不在赘述；
```
// 安装
npm install -g nodemon

// 启动node服务
nodemon server.js   //相当于node server.js

```
如果想手动重启node项目，在终端中输入rs即可，如下图所示。


![https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/nodemon/1545962846(1).png](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/nodemon/1545962846(1).png)


我们有时可能需要让nodemon忽略某个文件、需要debug模式等等，这些就需要在nodemon的配置文件中去配置，详细配置文档请跳转至[github仓库查看doc](https://github.com/remy/nodemon)；




我的github资源地址：[nodejs--自动重启工具nodemon简介](https://github.com/LeonWuV/FE-blog-repository/blob/master/nodejs/nodejs--%E8%87%AA%E5%8A%A8%E9%87%8D%E5%90%AF%E5%B7%A5%E5%85%B7nodemon%E7%AE%80%E4%BB%8B.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com