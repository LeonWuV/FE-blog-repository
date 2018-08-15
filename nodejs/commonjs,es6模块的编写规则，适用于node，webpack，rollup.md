欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 一、commonjs的编写规则
首先说明一下，commonjs模块规范被广泛使用在nodejs中，webpack也支持，rollup如果要支持则需要安装两个插件，rollup-plugin-node-resolve和rollup-plugin-commonjs

也可以参考下这篇博文：[require和import机制](https://blog.csdn.net/wxl1555/article/details/81613327)

commonjs模块要向外暴露 module.exports={}，也就是暴露一个对象，默认值为一个空对象;

写法如下：
```
// say.js
//一定要包裹在对象中 还要是顶级作用域
module.exports = {
    sayHi:function(){
        console.log("你好啊");
    }
};

//main.js 引用后就可以使用了
const say = require("./say.js");
say.sayHi();
```


顺便说一下exports，他其实是module.exports的一个引用，即exports = module.exports，也可以理解为是module.exports的浅复制对象；

我们可能也经常见到如下代码：
```
// b.js
exports.hi = function () {
    console.log('hi 1111');
}

//main1.js
const b = require("./b.js");
b.hi();
// 其实，exports.hi就等于是给module.exports对象上添加新的属性方法
```



#### 二、ES6模块的编写规则
webpack和rollup完美支持es6模块，nodejs在9+版本之后支持es6模块了
##### 1. 整体抛出

被引用的组件要暴露 export default {}

引用时 用import Cal from "组件的路径";

然后就可以用 Cal点出来组件中属性或者方法


```
//代码
//cal.js的内容
export default {
    add:function (n1,n2){
        return n1+n2;
    },
    num:34
};

//main.js 引用后就可以使用了
import Cal from "./cal.js";
console.log(Cal.add(4,5));
console.log(Cal.num);
```

##### 2. 单个抛出


```
//cal.js的内容
//声明直接导出
export const num =123;

//先声明后导出
const Cal ={
    sub:function(n1,n2){
        console.log(n1-n2);
    }
};
export { Cal };

//main.js 引用后就可以使用了 也要是顶级作用域 注意 命名很重要 要一致
import { Cal,num} from "./cal.js";
Cal.sub(12,1);
console.log(num);
```
#### 三、export default 和 export 区别
1. export与export default均可用于导出常量、函数、文件、模块等

2. 你可以在其它文件或模块中通过import+(常量 | 函数 |文件|模块)名的方式，将其导入，以便能够对其进行使用
3. 在一个文件或模块中，export、import可以有多个，export default仅有一个
4. 通过export方式导出，在导入时要加{ }，export default则不需要

```
//1.export
//demo1.js
export const str = 'hello world'
export function f(a){ return a+1}
对应的导入方式：

//demo2.js
import { str, f } from 'demo1' //也可以分开写两次，导入的时候带花括号

//2.export default
//demo1.js
export default const str = 'hello world'
对应的导入方式：

//demo2.js
import str from 'demo1' //导入的时候没有花括号
```
使用export default命令，为模块指定默认输出，这样就不需要知道所要加载模块的变量名


我的github资源地址：[commonjs,es6模块的编写规则，适用于node，webpack，rollup.md]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com