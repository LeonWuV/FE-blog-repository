#### 写在前面的话
这个问题在之前做项目时碰到过一次，当时按照网上的做法，去掉JSON.parse()这一层转换后就没有这个报错了，数据也能正常使用，就没多想，也没深究是什么原因。可是这次又碰到了，所以这次我必须要弄明白原因。
#### 先看看它的作用
JSON.parse()用于从一个字符串中解析出json对象,如

```
var str = '{"name":"LeonWu","age":"18"}'

JSON.parse(str);

//结果为一个Object
// age: "18";
// name: "LeonWu";
```
JSON.stringify()用于从一个对象解析出字符串，如

```
var a = {a:1,b:2,c:"LeonWu"};
 
 JSON.stringify(a);
 
 //结果为 "{"a":1,"b":2,"c":"LeonWu"}"
 
```
#### 背后的原因
1. 报错的原因：
  
因为你要转换的数据本来就是object，这个方法是把一个字符串解析出json对象，你再转换就会报错;

2. 为什么会有这样的错误：

因为把Object作为参数传到JSON.parse()里时，它会默转为string，转换为"[object Object]"，JSON.parse将第一个字符'['理解为数组的开始，第二字符'o'不知道怎么处理;所以就抛出了上面的错误信息 Unexpected token o in JSON at position 1。


---


**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**