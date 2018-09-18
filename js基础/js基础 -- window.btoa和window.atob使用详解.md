欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

#### 定义
atob()
>解码一个Base64字符串。

btoa()

>从一个字符串或者二进制数据编码一个Base64字符串。

#### 用法
只有字符串才能被转换

###### 默认转换 ASCII字母和数字，不支持中文
```
// 转base64
var aa = btoa("dddddddd");
// 转码结果 "ZGRkZGRkZGQ="

// 解码结果
var bb  = atob(aa);
// 解码结果 "dddddddd"

// 注意，如果想转换中文会直接报错，具体方法见下文
// 中文转换base64
var cc = btoa("哈哈")；
// 直接报错 VM275:1 Uncaught SyntaxError: Invalid or unexpected token
```
###### 转换中文的方法

```
// 先将中文转换为URL组件格式，再转为base64形式的
var dd = btoa(encodeURIComponent("哈哈"));
// 结果 "JUU1JTkzJTg4JUU1JTkzJTg4"

// 注意解析时就需要先解码为URL组件格式，再转换为中文，就是先进后出的原则
var ff = decodeURIComponent(atob(dd));
// 结果 "哈哈"
```

我的github资源地址：[js基础 -- window.btoa和window.atob使用详解]()

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com