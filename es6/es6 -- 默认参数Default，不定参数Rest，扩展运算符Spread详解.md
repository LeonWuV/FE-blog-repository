欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
记录一下在实际开发中，很有用的三个es6的新方法
#### 用法详解
##### 默认参数
```
function f(x, y=13) {
  // 如果没有传入y或传入了undefined，y的默认值为13
  return x + y;
}
f(5) // 18
```

##### 不定参数Rest
不定参数rest，让我们不再需要arguments，从而避免很多麻烦
```
function f(x, ...r) {
  // y是一个数组
  console.log(r);  //["h", true]
  return x * r.length;
}
f(4, "h", true) // 8
```
##### 扩展运算符
1、展开运算符，展开函数的参数。

```
function f(x, y, z) {
  return x + y + z;
}
// 将数组中的每个元素展开为函数参数
f(...[3,5,7]) //  15

```

2、扩展运算符取代apply方法的一个实际的例子，应用Math.max方法，简化求出一个数组最大元素的写法。

```
// ES5 的写法
Math.max.apply(null, [14, 3, 77])
 
// ES6 的写法
Math.max(...[14, 3, 77])
 
// 等同于
Math.max(14, 3, 77);
```

3、通过push函数，将一个数组添加到另一个数组的尾部

```

// ES5的 写法
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
Array.prototype.push.apply(arr1, arr2);
 
// ES6 的写法
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1.push(...arr2);

```

4、扩展运算符将字符串转为真正的数组

```
[...'leon']

// [ "l", "e", "o", "n"]
```

5、合并数组更加简单

```
// ES5
[11, 2].concat([4,5])

// ES6
[11, 2, ...[4,5]]
 
 
 //多个的写法
var arr1 = ['a', 'b'];
var arr2 = ['c'];
var arr3 = ['d', 'e'];
 
// ES5的合并数组
arr1.concat(arr2, arr3);
// [ 'a', 'b', 'c', 'd', 'e' ]
 
// ES6的合并数组
[...arr1, ...arr2, ...arr3]
// [ 'a', 'b', 'c', 'd', 'e' ]
```


我的github资源地址：[es6 -- 展开表达式详解]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com