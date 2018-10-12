欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

#### 前言
首先，我们碰到的这个问题只是一类问题的一个代表，总结起来就是关于eslint的问题；

类似的还有括号后面多个空格呀，不能用双引号呀等等的问题；

我们项目中既然选择了eslint，那么就是想做代码级的规范，如果解决问题的方案是在webpack的配置文件里注释掉eslint检查的相关配置，或者是在eslint的配置文件里将2（报错）级改为1（警告）或者0（忽略）级。

请问，如果这样你项目里的eslint有何意义？

具体的可以参考下面这几篇文章


1. [直接将eslint的配置文件改为0级（忽略）的文章](https://blog.csdn.net/openglnewbee/article/details/79852645)
2. [直接关闭或者注释掉webpack配置中eslint检查的项目配置文章](https://blog.csdn.net/u010429286/article/details/80108593)

#### 解决方案
首先我们要选一种规则，流行的有eslint-config-google，eslint-config-airbnb，eslint-config-standard，关于用法可以自行查找；

我的解决方案为，将eslint规则扩展到prettier，prettier有两种用法：

一种为plugin插件形式的，包名为eslint-plugin-prettier，当然我们需要先安装这个包；将eslint的配置文件中的plugin做如下修改即可

```
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```

第二种为扩展形式的，包名为eslint-config-prettier，同样eslint的配置文件做如下修改即可
```
{
  "extends": ["prettier"]
}
```

那么如果报错我们改怎么办呢，肯定不是手动去改；

我们做了这么多就是为了实现自动化，让脚本去做这些事情；

至于如何自动化请看这篇文章 [Prettier的三种使用场景和使用方法](https://github.com/LeonWuV/FE-blog-repository/blob/master/%E7%A0%81%E5%86%9C%E5%B7%A5%E5%85%B7/Prettier%E7%9A%84%E4%B8%89%E7%A7%8D%E4%BD%BF%E7%94%A8%E5%9C%BA%E6%99%AF%E5%92%8C%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95.md)


##### 友情链接
[eslint的配置规则总结链接](https://www.jianshu.com/p/29ca5a6a34fd)

[eslint官方文档链接](https://cn.eslint.org/)

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com



