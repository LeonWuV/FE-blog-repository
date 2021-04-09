vue项目中出现如下报错

>  Vue报错 --the "scope" attribute for scoped slots have been deprecated and replaced by "slot-scope"

### 原因

vue自2.5版本以来，作用域槽的“scope”属性已被弃用，并更改为“slot-scope”。

### 解决方案

```html
<!-- 将这个 -->
<template scope="scope">
</template>

<!-- 改为如下即可 -->
<template slot-scope="scope">
</template>

```

欢迎大家关注博主的公众号：<strong>猿人说事</strong>

<p align="center">
  <img src="http://storage.360buyimg.com/cdn-upload/yuanRenQR83057a63644441fda8a095ae68c574c5.jpg" alt="猿人说事-logo" width="150px" height="150px"/>
  <br>
</p>

---

<strong>github资源地址</strong>：[Vue报错 -- the "scope" attribute for scoped slots have been deprecated and replaced by "slot-scope"]()

<strong>我的CSDN博客地址</strong>：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，我们共同学习进步。

邮箱：wuxiaolong802@163.com


