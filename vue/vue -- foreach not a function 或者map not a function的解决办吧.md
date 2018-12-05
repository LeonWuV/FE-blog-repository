欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
老套路，先说出现这种问题的原因：

    在做vue项目时，如果我们在组件中需要一个变量，哪怕这个变量最开始是没值的，我们也必须先在data中注册这个变量；
    
    只有这样，我们的这个变量才能是响应式的，不然就失去了响应式的功能；
    
    问题就在这里，好多人的习惯就是写变量的值等于''(空)或者null，
map和foreach方法只能对数组或者类数组进行遍历，如果不是数组就会报错，很明显我们的初始值不是一个数组；
#### 解决办法

    其实很简单，在vue组件中注册变量的初始化值时不要随意的写一个空或者null，让他等于[](空数组)就可以了；

例子：
```
data() {
    return {
    // 如果这个值在后面是当做一个数组使用，并且需要去遍历的时候需要这样写
      value: [] 
    }
  }
```

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[vue -- foreach not a function 或者map not a function的解决办吧]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.co