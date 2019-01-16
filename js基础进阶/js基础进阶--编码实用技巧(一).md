我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
在平时的开发中，编码技巧很重要，会让你少写很多代码，起到事倍功半的效果。

下面总结几种简单的技巧，大家共同学习一下

#### 1、 利用+、-、/1,*1将字符串转换为整数型
这个方法试用于将字符串类型的数字转换为整数型，如果带字母就会返回NaN。

```
var a = "1234", b = "leonWuv";
//我们想把a转换为1234的整数型，一般方法
console.log(typeof Number(a))  //number
//简单写法
console.log(+a + 1,typeof +a);  //1235 number
console.log(a - 0 + 1,typeof (a-0)); //1235 number
console.log(a*1 + 1,typeof (a*1));  //1235 number
console.log(a/1 + 1,typeof (a/1));  //1235 number
console.log(b/1 + 1,typeof (b/1));  //NaN number
```
这个也是用于 Date();它将返回时间戳

```
//以下方法都返回时间戳
console.log(+ new Date()); //1512378253218  2017年12月04日17时左右;
console.log(Date.parse(new Date())); //1512378253000  注意后三位向下取整为000;
console.log(new Date("2017/1/1").getTime()); ////1483200000000
```

#### 2、利用!!强制转换布尔值
我们需要验证一个变量是否存在或者有效时，可以使用！！来简单快速的判断

这个技巧我在 [javaScript数据类型你都弄明白了吗？绝对干货](http://blog.csdn.net/wxl1555/article/details/78595729)这篇博文中的第四部分提到过

总结一下就是：只要变量的值为:0、null、" "、undefined或者NaN都将返回的是false，反之返回的是true。看下面例子


```
var a = 0,b = "12";
console.log(!!c); //false
// 分解上面的代码--Boolean(c)得false，取非为true，再取非为false。
console.log(!!d)  //true
// 分解上面的代码--Boolean(d)true，取非为false，再取非为true
```
#### 3、在遍历数组时，缓存数组的length

在处理一个数组循环时，我们好多人通常会这么写
```
for(var i = 0; i < array.length; i++) {
    console.log(array[i]);
}
```
当我们遍历一个小型数组时，这样写是可以的，但是当我们处理一个大型数组时，这样写就会每次循环都计算数组的长度，会有延误，这时我们可以这样写

```
var length = array.length;
for(var i = 0; i < length; i++) {
    console.log(array[i]);
}
```
当然我们也可以这样写，这两种方式都是可以的
```
for(var i = 0, length = array.length; i < length; i++) {
    console.log(array[i]);
}
```

#### 4、合理利用&&运算符
看看这段代码

```
if(a){
	console.log("hello leonWu");
	//解释一下这段代码，如果Boolean(a)为true，就打印出hello leonWu
}
```
我们稍微修改一下上面的代码

```
a && console.log("hello leonWu"); //结果是一样的，但是这样是不是简单清晰多了，代码量也少了
```

相关链接：[js基础进阶--编码的实用技巧(二)](https://blog.csdn.net/wxl1555/article/details/78736591)


github资源地址：[js基础进阶--编码实用技巧(一)](https://github.com/LeonWuV/leonwuv.github.io/blob/hexo/source/_posts/js%E7%BC%96%E7%A0%81%E7%9A%84%E5%AE%9E%E7%94%A8%E6%8A%80%E5%B7%A71.md)


csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com