欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 什么是NodeJS
JS是脚本语言，脚本语言都需要一个解析器才能运行。对于写在HTML页面里的JS，浏览器充当了解析器的角色。而对于需要独立运行的JS，NodeJS就是一个解析器。

每一种解析器都是一个运行环境，不但允许JS定义各种数据结构，进行各种计算，还允许JS使用运行环境提供的内置对象和方法做一些事情。例如运行在浏览器中的JS的用途是操作DOM，浏览器就提供了document之类的内置对象。而运行在NodeJS中的JS的用途是操作磁盘文件或搭建HTTP服务器，NodeJS就相应提供了fs、http等内置对象。
### 有啥用处，能干什么
尽管存在一听说可以直接运行JS文件就觉得很酷的同学，但大多数同学在接触新东西时首先关心的是有啥用处，以及能带来啥价值。

NodeJS的作者说，他创造NodeJS的目的是为了实现高性能Web服务器，他首先看重的是事件机制和异步IO模型的优越性，而不是JS。但是他需要选择一种编程语言实现他的想法，这种编程语言不能自带IO功能，并且需要能良好支持事件机制。JS没有自带IO功能，天生就用于处理浏览器中的DOM事件，并且拥有一大群程序员，因此就成为了天然的选择。

如他所愿，NodeJS在服务端活跃起来，出现了大批基于NodeJS的Web服务。而另一方面，NodeJS让前端众如获神器，终于可以让自己的能力覆盖范围跳出浏览器窗口，更大批的前端工具如雨后春笋。

因此，对于前端而言，虽然不是人人都要拿NodeJS写一个服务器程序，但简单可至使用命令交互模式调试JS代码片段，复杂可至编写工具提升工作效率。

### 如何安装
直接在官网 [https://nodejs.org/en/download/](https://nodejs.org/en/download/)选择和自己系统匹配的安装程序傻瓜式安装就行；

##### 验证是否安装成功

win系统下，打开终端，也就是cmd，键入如下命令，如果打印出版本号，则说明安装成功了；

```
node -v

npm -v
```
![image](http://olv6wm3nj.bkt.clouddn.com/18-9-13/1814247.jpg)

安装node程序时会附带安装npm包管理器，所以也可以顺便看下npm的版本号；
### 如何运行js代码
打开终端，键入node进入命令交互模式，可以输入一条代码语句后立即执行并显示结果，例如：
```
node

> console.log('Hello World!');

Hello World!
```
如果要运行一大段代码的话，可以先写一个JS文件再运行。例如有以下hello.js。
```
function hello() {

    console.log('Hello World!');
}

hello();
```
写好后在终端下键入node hello.js运行，结果如下：

```
node hello.js

Hello World!
```
### 模块化
编写稍大一点的程序时一般都会将代码模块化。在NodeJS中，一般将代码合理拆分到不同的JS文件中，每一个文件就是一个模块

在编写每个模块时，都有require、exports、module三个预先定义好的变量可供使用。

也就是commonjs的规范；
##### require
require函数用于在当前模块中加载和使用别的模块，传入一个模块名，返回一个模块导出对象。模块名可使用相对路径（以./开头），或者是绝对路径（以/或C:之类的盘符开头）。另外，模块名中的.js扩展名可以省略。以下是一个例子。
```
var foo1 = require('./foo');
var foo2 = require('./foo.js');
var foo3 = require('/home/user/foo');
var foo4 = require('/home/user/foo.js');
 
// foo1至foo4中保存的是同一个模块的导出对象。
```

另外，可以使用以下方式加载和使用一个JSON文件。
```
var data = require('./data.json');
```
##### exports
exports对象是当前模块的导出对象，用于导出模块公有方法和属性。别的模块通过require函数使用当前模块时得到的就是当前模块的exports对象。以下例子中导出了一个公有方法。

```
exports.hello = function () {
    console.log('Hello World!');
};
```
##### module
通过module对象可以访问到当前模块的一些相关信息，但最多的用途是替换当前模块的导出对象。例如模块导出对象默认是一个普通对象，如果想改成一个函数的话，可以使用以下方式。


```
module.exports = function () {
    console.log('Hello World!');
};
```
以上代码中，模块默认导出对象被替换为一个函数。

##### 模块初始化
一个模块中的JS代码仅在模块第一次被使用时执行一次，并在执行过程中初始化模块的导出对象。之后，缓存起来的导出对象被重复利用。

理解上面这句话很重要；
##### 主模块
通过命令行参数传递给NodeJS以启动程序的模块被称为主模块。主模块负责调度组成整个程序的其它模块完成工作。例如通过以下命令启动程序时，main.js就是主模块。

```
node main.js
```
##### 完整示例
例如有以下目录。
```
- /home/user/hello/
    - util/
        counter.js
    main.js
```
其中counter.js内容如下：
```

var i = 0;
 
function count() {
    return ++i;
}
 
exports.count = count;
```
该模块内部定义了一个私有变量i，并在exports对象导出了一个公有方法count。

主模块main.js内容如下：


```
var counter1 = require('./util/counter');
var counter2 = require('./util/counter');
 
console.log(counter1.count());
console.log(counter2.count());
console.log(counter2.count());
```
运行该程序的结果如下：
```
node main.js
1
2
3
```
可以看到，counter.js并没有因为被require了两次而初始化两次。
### 二进制模块
虽然一般我们使用JS编写模块，但NodeJS也支持使用C/C++编写二进制模块。编译好的二进制模块除了文件扩展名是.node外，和JS模块的使用方式相同。虽然二进制模块能使用操作系统提供的所有功能，拥有无限的潜能，但对于前端同学而言编写过于困难，并且难以跨平台使用，因此不在本教程的覆盖范围内。


我的github资源地址：[nodejs入门（一）]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com