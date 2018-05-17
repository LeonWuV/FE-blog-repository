
#### 数据类型的分类
JavaScript的数据类型分为两大类，基本数据类型和复杂数据类型。

基本数据类型：Null、Undefined、Number，String，Boolean。

复杂数据类型：Object。

### 一、Object
《JavaScript语言精辟》这本书里面是这么定义的：数组是对象，函数是对象，正则表达式也是对象，当然，对象也是对象。

JavaScript包括一个原型链特性，允许对象继承另一个对象的属性，正确的使用它能减少对象初始化的时间和内存消耗。
### 二、undefined
这个数据类型只有一个值，就是undefined，它是在var了一个变量之后没有对其初始化的结果。

```
var  a;

console.log(a) //undefined
```
### 三、null

这个数据类型也只有一个值，就是null，他表示的是一个空指针对象，这也是typeof类型检测null为什么返回object的原因。

如果我们申明一个变量是为了在以后保存某个值，那么现在我们就把null赋值给它，而不是其他的值。然后我们就可以判断它的值进行一系列的操作。

```
//例如
var a = null;

if(a != null){
    //为undefined时也不能进来
    //进行一系列操作

}

```
还有一点就是，undefined值是派生自null值，所以ECMA规定他们相等测试返回值是true。

```
console.log(undefined == null); // true

```
### 四、Boolean
这个数据类型只有两个值true、false，他们的值分别等价于1和0，但是值类型不相等。

```
console.log(true == 1,true === 0,false == 0,false === 0);  //true false true false
```

其实在JavaScript中，每种数据类型的值都可以转换为和Boolean类型相等的值，我们可以调用类型转换函数Boolean();


```
var aa = 0,bb = "leonWu",cc = [1,2,3],cc1 = [], dd = undefined,ee = null;

console.log(Boolean(aa)); //false
console.log(Boolean(bb)); //true
console.log(Boolean(cc)); //true
console.log(Boolean(cc1)); //true
console.log(Boolean(dd)); //false
console.log(Boolean(ee)); //false
```
由上面的例子我们可以看出，调用的Boolean()函数返回值是boolean数据类型的值，至于返回的是true还是false，取决于被转换值的数据类型及其实际值。

它的转换规则详见下表

数据类型 | 转换为true的值 | 转换为false的值
---|---|---
boolean | true | false
String | 任何非空字符串 | " "(空字符串)
Number| 任何非0整数（包括无穷大） | 0和NaN
Object | 任何对象 | null
Undefined | 不适用 |undefined

当然，在有的时候，Boolean()函数会被隐式调用，看下面代码


```
var a1 = "leonWu",a2 = 0;

//1、可以打印出 "进来了"
if(a1){
    console.log("进来了") 
}

//2、不能打印出 "进来了"
if(a2){
    console.log("进来了") //
}

console.log(!a1,!a2) // 3、false true
```

上面的代码就是在if判断和取非的时候隐式调用了Boolean()函数，第一个相当于Boolean(a1)返回true，第二个相当于Boolean(a2)返回false,第三个相当于 !Boolean(a1)、!Boolean(a2)返回false、true。

在实际编码中 !a2的写法肯定比 !Boolean(a2)的写法简单的多，但是Boolean(a2)的返回值本来是false，我们为了简单，写成了 !a2返回值却是true，和我们想要的结果不一致，容易弄混，所以我们就可以写成 !!a2,这样就可以返回我们想要的值了。


看下面代码
```
var b1 = "",b2 = "ddd";

console.log(!!b1) // false
console.log(!!b2) // true
```


**本文内容稍有点长，请你耐心往下看**

### 五、String

我对这个数据类型的理解是由零或多个16位Unicode字符组成的字符序列，即字符串。字符串可以由单引号(')或双引号(")表示。

他也有个强制转换为字符串的String()方法,可以把任何数据类型转换为字符串。

```
var bb1 = 123, bb2 = null;

console.log(String(bb1)); // "123"

console.log(String(bb2)); // "null"
```

还有一个方法.toString()方法，但是只有数值，字符串，对象，布尔值有这个方法，null和undefined没有这个方法。

```
var bb1 = 123, bb2 = null, bb3 = undefined;

console.log(bb1.toString()); // "123"

console.log(bb2.toString()); // 报错

console.log(bb3.toString()); // 报错
```

### 六、Number

这个数据类型包括整数型、浮点型、NaN(not  a number),NaN是个特殊的数值，它表示本来要返回一个数值类型的值，但是没有返回，中途出错了，这样可以避免抛出错误。

比如下面几个例子


```
var a = "leonWu",b = 12,c = null,d = "lwonWu123";
    c = a * b;
    console.log(c) // NaN
    console.log(parseInt(d)); // NaN
    console.log(Number(d)); //NaN
    
```

和NaN有关的运算符操作，结果也是NaN，NaN和任何数都不相等，页包括它自己。


```
console.log(typeof NaN); //number

console.log(NaN == NaN); //false

```

再看下面几个例子


```
var a = "123leonWu", b = "leonWu123",c = "12.34";

console.log(parseInt(a)); //123
console.log(parseFloat(a)); //123
console.log(Number(a));  //NaN

console.log(parseInt(b)); //NaN
console.log(parseFloat(b));  //NaN
console.log(Number(b)); //NaN

console.log(parseInt(c)); //12
console.log(parseFloat(c)); //12.34
console.log(Number(c)); //12.34
```

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**


