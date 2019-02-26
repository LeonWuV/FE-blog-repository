欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
老规矩，我们还是先说为什么。

问题描述：为什么在vue组件中，我们的data属性必须是一个函数,new Vue()中的data除外，因为new Vue中只有一个data属性。

原因：因为我们能抽离出来的组件，肯定是具有复用性的，它在项目中会存在多个实例。如果data属性值是一个对象时，那么它所有的实例都会共享这些数据，这是很麻烦的事情，你不能确保你的所有实例中的属性值都不会重复。

我们的期望是，组件的每个实例都能独立的维护自己的数据。
### 解决方案
我们都知道，在JavaScript中，函数具有独立作用域快的特点，外部是无法访问其内部的变量。

试想一下，如果我们组件中的data返回一个函数，他的每个实例就会有自己的作用域空间，也就是独立的数据，每个实例之间不会相互影响。

所以，组件中的data属性必须是一个函数。


github资源地址：[vue--为什么data属性必须是一个函数](https://github.com/LeonWuV/FE-blog-repository/blob/master/vue/vue--%E4%B8%BA%E4%BB%80%E4%B9%88data%E5%B1%9E%E6%80%A7%E5%BF%85%E9%A1%BB%E6%98%AF%E4%B8%80%E4%B8%AA%E5%87%BD%E6%95%B0.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com