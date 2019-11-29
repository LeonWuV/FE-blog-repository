##### 欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 问题
有时候，我们页面的主题色是深色的，在chrome浏览器里登录成功之后，会有个记住密码功能，这个功能是chrome自带的功能，然后我们下次登录的时候，就会提示让我们选择浏览器记住的账号和密码，选完之后会有个白色的背景，与我们自己写的风格很不搭配；

当然，这个也浏览器默认的颜色，我们是可以修改的；

### 解决方案
加上如下css，即可解决这个问题

```
:-webkit-autofill,
:-webkit-autofill:hover,
:-webkit-autofill:focus,
:-webkit-autofill:active {
    // 回填文字颜色设置
    -webkit-text-fill-color: #2b739d !important;
    transition: background-color 5000s ease-in-out 0s;
}
```

---

github资源地址：[css基础--chrome浏览器已保存的密码回填时带默认白色背景问题](https://github.com/LeonWuV/FE-blog-repository/blob/master/css%E5%9F%BA%E7%A1%80/css%E5%9F%BA%E7%A1%80--chrome%E6%B5%8F%E8%A7%88%E5%99%A8%E5%B7%B2%E4%BF%9D%E5%AD%98%E7%9A%84%E5%AF%86%E7%A0%81%E5%9B%9E%E5%A1%AB%E6%97%B6%E5%B8%A6%E9%BB%98%E8%AE%A4%E7%99%BD%E8%89%B2%E8%83%8C%E6%99%AF%E9%97%AE%E9%A2%98.md)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com