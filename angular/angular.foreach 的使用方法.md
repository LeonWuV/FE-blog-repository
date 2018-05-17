angular有自己的生命周期。同时angular页有很多自己封装的方法，当我们遍历数组时，最好还是用angular自带的循环方法。“angular.foreach”
格式为:

```
var objs =[{a:1},{a:2}];  
angular.forEach(objs, function(item,index,array){  
    // item等价于array[index];
    console.log(item.a+'='+array[index].a);  
});

```
我把参数解释一下：
1. objs：需要遍历的集合
2. item:遍历时当前的数据
3. index:遍历时当前索引
4. array:需要遍历的集合，每次遍历时都会把objs原样的传一次。

这里要注意的是：function（）里面的参数第一个是数组的当前元素即array[index]，第二个是下标（index）；

后面的两个参数是可选的:

```
var objs =[{a:1},{a:2}];  
angular.forEach(objs, function(item){  
    console.log(item.a);  
}); 
```
其实就这么简单

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**