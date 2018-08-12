欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
这里只是大概的简单的使用总结，要想深入的理解还需自己一点一点的在实际的工作中积累。
### webpack是什么
webpack是一个前端构建的打包工具（并不是什么库或框架）， 它能把各种资源，例如JS（含JSX）、coffee、css（含less/sass）、图片等都作为模块来处理和使用。
### 基础知识点
webpack 是一个现代 JavaScript 应用程序的模块打包器(module bundler)。当 webpack 处理应用程序时，它会递归地构建一个依赖关系图(dependency graph)，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 bundle。

#### webpack的四个核心概念
1. entry(入口)：entry point,入口起点（可以有多个），webpack会从该起点出发，找出哪些文件时入口文件所依赖的，从而构建内部依赖关系图，并处理后输出到称之为bundles的文件中。

2. output(输出)：指定经entry point处理后的bundles文件的输出路径（path）和名字（filename）

3. loader(加载器):用来处理非JS文件，可以将所有文件转换成webpack可以处理的模块，然后交给webpack进行打包等处理；webpack loader 本质上讲是将所有类型的文件转化为应用程序的依赖图可以直接引用的模块，其有两个目标：

    1. 使用test属性，识别出对应于 loader 的可转换文件

    2. 使用use属性将这些文件进行转换，使其被添加到依赖图中，并且最终会添加到 bundle 中，如果要在 webpack 配置中定义 loader ，要在 module.rules 中定义。
4. plugins(插件)：从打包优化和压缩，一直到重新定义环境中的变量。插件接口功能极其强大，可以处理各种各样的任务

    使用一个插件只需要 require() 它，然后把它添加到 plugins 数组中就行。你也可以在一个配置文件中因为不同目的而多次使用同一个插件，这时需要通过使用 new 操作符来创建它的一个实例。当然你也可以选用webpack内置的很多插件。

    






我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[https://github.com/webpack -- 简单的使用总结.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/webpack/webpack%20--%20%E7%AE%80%E5%8D%95%E7%9A%84%E4%BD%BF%E7%94%A8%E6%80%BB%E7%BB%93.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com