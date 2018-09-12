欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
ES6为Array增加了from函数用来将其他对象转换成数组。

当然，其他对象也是有要求，也不是所有的，可以将两种对象转换成数组。

    1.部署了Iterator（迭代器）接口的对象，比如：Set，Map，Array。

    2.类数组对象，什么叫类数组对象，就是一个对象必须有length属性，没有length，转出来的就是空数组。
#### 具体用法
Array.from可以接受三个参数

我们看定义：Array.from(arrayLike [, mapFn [, thisArg]])

    arrayLike：被转换的的对象。

    mapFn：map函数。

    thisArg：map函数中this指向的对象。

##### 第一个参数
在这里很好理解，就是要被转换的对象

##### 第二个参数，map函数
    
用来对转换中的每一个元素进行加工，并将加工后的结果作为结果数组的元素值。
    
```
console.log(Array.from([1, 2, 3, 4, 5], (n) => n + 1))

// 结果[2,3,4,5,6] map函数的实际的做用是给每个元素都加了1
```
##### 第三个参数，map函数中this指向的对象
该参数是非常有用的，我们可以将被处理的数据和处理对象分离，将各种不同的处理数据的方法封装到不同的的对象中去，处理方法采用相同的名字。

在调用Array.from对数据对象进行转换时，可以将不同的处理对象按实际情况进行注入，以得到不同的结果，适合解耦。

这种做法是模板设计模式的应用，有点类似于依赖注入。


```
const obj = {
    
    add: function (n) {
        return n + 1;
    }
}

console.log( Array.from(
  [1, 2, 3, 4, 5], 
  function (x){
    return this.add(x)
  }, 
  obj))
  
  //结果 [2,3,4,5,6]
```
#### 转换set对象

```
    const setArr = new Set();
	setArr.add(1).add(2).add("www");
	console.log(Array.from(setArr));
	// 结果 [1, 2, "www"]
	
	const setArr1 = new Set([1,1,12,2,3,4,5,5,6,6]);
	console.log(Array.from(setArr1));
	// 或者使用展开表达式 console.log([...setArr1]);
	// 结果 [1, 12, 2, 3, 4, 5, 6] 
	// 同时不难发现set具有去重的功能
```
#### 转换map对象

```
    const mapArr = new Map();
	mapArr.set('m1', 1);
	mapArr.set('m2', 2);
	mapArr.set('m3', 3);
	console.log(Array.from(mapArr));
	// 结果 [['m1', 1],['m2', 2],['m3', 3]]
	console.log(Array.from(mapArr)[1]);
	// 结果 ["m2", 2]
```
#### 转换类数组对象
一个类数组对象必须要有length属性，他们的元素属性名必须是数值或者可以转换成数值的字符。

##### 注意：
1. 属性名代表了数组的索引号，如果没有这个索引号，转出来的数组中对应的元素就为length长度个undefined。
2. 如果没有length属性，转换出来的数组也是空的；

##### 带length
```
//注意看区别
    console.log(Array.from({
      	0: 'dd',
     	1: 'gg',
      	2: 'w3',
      	length:3
    }))
    // 结果 ["dd", "gg", "w3"]
    
    console.log(Array.from({
	  	0: 'dd',
	 	1: 'gg',
	  	4: 'w3',
	  	length:3
	}))
	// 结果 ["dd", "gg", undefined]
	
	console.log(Array.from({
	  	"0": 'dd',
	 	1: 'gg',
	  	"3": 'w3',
	  	length:6
	}))
	// 结果 ["dd", "gg", undefined, "w3", undefined, undefined]
	
//总结，生成数组的长度由length属性确定，如果相应索引位置上没有值，则为undefined
```

##### 不带length
```
    console.log( Array.from({
      	0: 3,
      	1: 12
    }))
    // 结果 []
```

##### 对象的属性名不能转换成索引号时

```
    console.log(Array.from({
	  	"s": 'dd',
	 	"ss": 'gg',
	  	"n": 'w3',
	  	length:3
	}))
    // 结果 [undefined, undefined, undefined]
```



我的github资源地址：[es6 -- Array.from()函数的用法]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)


如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com