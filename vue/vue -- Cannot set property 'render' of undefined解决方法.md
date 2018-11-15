欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
在用vue-cli3做组件测试时，出现个问题，记录一下

报错如下 Cannot set property 'render' of undefined

#### 解决方案
后来发现是因为 组件里写了script标签，没写 export default {}

加上这句话之后就好使了


---


我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[vue -- Cannot set property 'render' of undefined解决方法]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com