我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

接上篇文章：
[js基础进阶--编码实用技巧(一)]()

### 5、合理利用||运算符

使用||可以作为参数之外的默认值，当第一个参数返回值为false时，那么第二个值就为默认值。

一般在面向对象思想中这么使用。
```
function User(name, age) {
    this.name = name || "leonWu";
    this.age = age || 29;
}
var user1 = new User();
console.log(user1.name); // leonWu
console.log(user1.age); // 29
 
var user2 = new User("delia", 28);
console.log(user2.name + " is my wife"); // delia is my wife
console.log(user2.age); // 28
```

### 6、三木运算符
看看下面的例子，我相信你就会立马理解了

```
var x = 10,b = null;
if (x > 5) {
    b = 7;
} else {
    b = 2;
}
```
这段代码用三木运算简写为

```
b = x > 5 ? 7 : 2;
//解释一下上面的代码
// 当x > 5 时返回7并赋值给b，反之则返回2赋值给b
```

### 7、判断相等时用 === 而不是 ==
因为== 和 != 在做判断时，会在某些情况下进行隐式类型转换，但是 === 和 !== 却不会，并且它们会同时对值大小和值类型进行比较，所以=== 和！== 要比== 和！=的处理速度快。

看例子


```
[5] == 5; //true
[5] === 5; //false
"5" == 5; //true
"5" === 5;//false
""  == 0; // true
"" === 0; //false
[] == "" //true
[] === "" //false

```
### 8、随即从数组中取一个元素

```
var items = [123, 81 , 'abc' , 234 , 781 , 'leonwu', 114, , 'delia' , 110 , 120];
var randomItem = items[Math.floor(Math.random() * items.length)];

```
稍微解释一下上面的代码

1. Math.floor()这个方法为js内置的方法，向下取整，即Math.floor(2.9)结果为2，Math.floor(2.1)结果也为2。
2. Math.random()为在[0-1)之间取一个随即浮点数，包括0但不包括1；

所以上面randomItem的结果是[0-9]之间的一个随即整数。

### 9、在指定的范围中取出一个随机整数
这个方法应该是上面第8条的加强版，只要理解上面的方法，那么这个方法理解起来就不会有难度。在这里多一嘴，很多东西靠死记硬背是记不住的，但是只要你理解了，那么你想忘记就比较难了。好了，不扯淡了，我们开始

上代码

```
//先看看下面这个方法，不理解不要紧，继续向下看你就会理解它

var a = Math.floor(Math.random() * (max - min + 1)) + min; 

//下面就让我们慢慢的理解上面这个方法是怎么来的

//先写出在[0-10]之间取随机整数的方法

var b = Math.floor(Math.random() * 10) //这个返回的是[0-10),不包括10，最大到9

 b = Math.floor(Math.random() * (10 + 1)); //这样就能取到[0-10]之间的随即整数了

//然后取一个[30-40]之间的随机整数

//我们把上面的任务分解为先取一个[0-10]之间的随机整数，然后再加上30，是不是就能满足我们上面的需求了，看代码

var c = Math.floor(Math.random() * (40-30 + 1)) + 30;

//那我们要取[max-min]之间的随机整数，代码是不是就为

var a = Math.floor(Math.random() * (max - min + 1)) + min;

//我们是不是已经理解了这段代码的意义呢，是不是想忘记都会很难呢？如果没理解就再多想想。

```
相关推荐：[js基础进阶--编码实用技巧(一)]()


github资源地址：[js基础进阶--编码的实用技巧(二)]()


csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com
