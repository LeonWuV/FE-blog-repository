欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
虽然我们很多人每天都在写项目，require或者import写的爽得很，但还是有很大一部分人不清楚它背后的运行原理和所谓的规则机制。

### 开始
我们基于webpack开发，就拿基本的vue项目来举例子吧

假如我们项目中要用到vue或者express框架，我们的代码就这样写

```
import Vue from 'vue'

//或者
var Vue = require('vue')
```

然后我们就能在下面轻松的用Vue这个变量，感觉很愉悦，但是你想过我们是怎么拿到Vue这个东西的吗？我们写的import或者require这行代码道理干了啥？

首先，import是es2015的模块引入规范，而require是commonjs的模块引入规范；

webpack支持es2015，commonjs，AMD等规范；

### 工作机制

> 前提是你在做web开发，试图用webpack或者rollup打包你的项目；


首先会从本地的node_modules文件夹中找到vue文件夹，看是否存在package.json文件；

如果找到了package.json，就会先找module字段，然后读取对应的路径下的文件，查找到此结束；

如果没找到module字段，就会找main字段，然后读取对应的路径下的文件，查找到此结束；

如果没有main字段，就会在vue文件夹下找index.js文件，然后读取文件，查找到此结束；

如果以上都没找到就会返回异常，扔出not find异常

如果不存在package.json就会找index.js文件，然后读取文件，查找到此结束；如果还没有就会抛出异常；


### 简单说一下module字段

说到module字段就不得不说一个和webpack很像的模块打包工具---rollup，

rollup是一个轻量级的打包工具，一般被用来打包模块或者库，可以根据需要将模块打包为es，commonjs，AMD，CMD，UMD，IIFE等规范的模块；

而webpack一般被用来打包应用程序；

rollup提出了module这个字段，其原因是一般主流的模块或者库都是commonjs规范的模块，而es2015的模块规范才是js的未来，才应该是主流；

所以，一般的package.json中的module对应的模块为es模块，而main对应的为commonjs模块，webpack和rollup都会默认优先读取module字段；




github资源地址：[webpack--require和import机制.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/webpack/webpack%20--%20require%E5%92%8Cimport%E6%9C%BA%E5%88%B6.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com