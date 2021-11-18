### 前言

vue项目中过滤器是很常见的功能，我们应该如何合理的设计它的使用方式呢？

先看下官方文档： [vue过滤器文档](https://cn.vuejs.org/v2/guide/filters.html)

项目中对过滤器的使用不是很统一，有局部使用的，全局使用的，或者是直接引用过滤器文件的每个都注册一下，这几种使用方式都不是很友好。

我们如何优化一下呢？且向下看。



### 设计思路

1. 单独文件夹维护过滤器工具；

2. 在main.js中注入为全局过滤器;

3. 在具体需要的地方使用;



### 具体代码

新建filters文件夹，每一个过滤器为一个单独的文件维护，最后统一收口到index文件中。

![img](https://apijoyspace.jd.com/v1/files/QaVRUMQlC9tf6o3ecEB1/link)



比如一个很常见的时间格式过滤器

![img](https://apijoyspace.jd.com/v1/files/lNFxgRjLtBEjm0g6bQGQ/link)

在main.js中注入

![img](https://apijoyspace.jd.com/v1/files/DpR3BGZmF014HLoixKnB/link)



在页面中使用

![img](https://apijoyspace.jd.com/v1/files/wHG6HGvKtZT6y7H40hbu/link)

这样我们就完成了对过滤器使用方式的设计，是不是感觉这样很清爽呢。





欢迎大家关注博主的公众号：<strong>猿人说事</strong>


---

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，我们共同学习进步。

邮箱：wuxiaolong1024@163.com