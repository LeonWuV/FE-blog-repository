欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
最近工作有点忙，好几天都没更新技术博客了。

周末起床打开有道云笔记，发现自己的博客todolist里躺了一堆只有名字的文件。

话不多说，我们开干，加油！

### 干货满满
今天，我们一起学习一下js中的数据类型检测相关的知识，也顺便做个总结。
#### 1、数据类型介绍
我们都知道，在js中分为基本数据类型和复杂数据类型。

基本数据类型又包括 Sting Number Boolean Null Undefined ，还有一个es6新增的Symbol，我们这先不说。

复杂数据类型只有一种，那就是Object。

我们平时见到的数组Array、正则RegExp、时间对象Date、函数Function等都属于Object。
#### 2、如何判断基本数据类型
这点想必大家都知道，但是我还是要在这里啰嗦一下。

判断基本数据类型我们可以选择typeof来判断。

这里需要注意就是返回值，他的返回值为小写字母开头的字符串。

```
//字符串
typeof 'leon'  // 'sting'

//整数
typeof 22  // 'number'

//undefined
typeof undefined  // 'undefined'

//Boolean
typeof true  // 'boolean'

//Null
typeof null  // 'object' 这为什么是object ？
// 因为null表示的是一个空指针，指针表示的是引用型数据，所以返回object

//Object
typeof [1,2.3]      //'object' 
typeof {a: 'ww'}    //'object' 
typeof new Date()   //'object' 

//function
typeof function(){}     //"function"
```
### 3、instanceof 
instanceof是用来检测引用类型，检测是那种类型的实例。

他的返回值为Boolean值，真为true，否则为false。

不能检测null，会报错。

```
// 这种检测方式一般不常用
[1, 2] instanceof Array  //true

({a: 1}) instanceof Object  //true

(function(){}) instanceof Function  //true

```
#### 4、Constructor
返回结果为构造器，也可以检测自定义类型；

但是不适用于null和undefined。
```
'leon'.constructor == String // true
(1234).constructor == Number // true
(true).constructor == Boolean // true
[1, 2].constructor == Array // true
({name:'leon'}).constructor == Object // true
(function(){}).constructor == Function // true
```

检测自定义类型
```
function Leon(){}
var leon = new Leon();
leon.constructor == Leon;  // true 
```
#### 5、Object.prototype.toString.call(obj)
这种方式是最权威的，也是很多框架插件中用到的方法，推荐使用；

```
Object.prototype.toString.call('leon'); //"[object String]"
Object.prototype.toString.call(1234);  //"[object Number]"
Object.prototype.toString.call(true); //"[object Boolean]"
Object.prototype.toString.call([1,2,3]); //"[object Array]"
Object.prototype.toString.call({name:'leon'}); //"[object Object]"
Object.prototype.toString.call(function(){}); //"[object Function]"
Object.prototype.toString.call(null); //"[object Null]"
Object.prototype.toString.call(undefined); //"[object Undefined]"
```

实际使用时，可以这么写

```
var test = Object.prototype.toString.call('leon');
if(test == "[object String]") {
    console.log('这是个字符串')
}

//当然我们也可以选择用正则去判断第二个单词，从而得到数据的类型
```


---
github文章资源地址：[js基础--数据类型检测的相关知识](https://github.com/LeonWuV/FE-blog-repository/blob/master/js%E5%9F%BA%E7%A1%80/js%E5%9F%BA%E7%A1%80--%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B%E6%A3%80%E6%B5%8B%E7%9A%84%E7%9B%B8%E5%85%B3%E7%9F%A5%E8%AF%86.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com