---
title: You are using the runtime-only build of Vue where the template compiler is not a
date: 2018-10-22 19:34:10
tags: vue
---

在升级脚手架到vue-cli3.0版本的时候出现了这个报错：

**[Vue warn]: You are using the runtime-only build of Vue where the template compiler is not available. Either pre-compile the templates into render functions, or use the compiler-included build.**

我在这里大概说一下出现这个报错的原因在哪里和解决办法

#### 原因
 vue有两种形式的代码   compiler（模板）模式和runtime模式（运行时），vue模块的package.json的main字段默认为runtime模式， 指向了"dist/vue.runtime.common.js"位置。
 
 这是vue升级到2.0之后就有的特点。
 
 而我的app.vue文件中，初始化vue却是这么写的，这种形式为compiler模式的，所以就会出现上面的错误信息
```
// compiler
new Vue({
  el: '#app',
  router: router,
  store: store,
  template: '<App/>',
  components: { App }
})

```
#### 解决办法
将app.vue中的代码修改如下就可以

```
//runtime

new Vue({
  router,
  store,
  render: h => h(App)
}).$mount("#app")
```

到这里我们的问题还没完，那为什么之前是没问题的，之前vue版本也是2.x的呀？

这也是我要说的第二种解决办法

因为之前我们的webpack配置文件里有个别名配置，具体如下
```
resolve: {
    alias: {
        'vue$': 'vue/dist/vue.esm.js' //内部为正则表达式  vue结尾的
    }
}
```

也就是说，import Vue from 'vue' 这行代码被解析为  import Vue from 'vue/dist/vue.esm.js'，直接指定了文件的位置，没有使用main字段默认的文件位置

所以第二种解决方法就是，在vue.config.js文件里加上webpack的如下配置即可，

```
configureWebpack: {
    resolve: {
      alias: {
        'vue$': 'vue/dist/vue.esm.js' 
      }
    }
```

既然到了这里我想很多人也会想到第三中解决方法，那就是在引用vue时，直接写成如下即可
```
import Vue from 'vue/dist/vue.esm.js'
```

#### 总结
遇到问题之后不是说解决了问题就完事了，更重要的是要思考 -- 为什么？，原因是啥？要理解而不是死记，只有这样你才能得到很大的提升！



我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com



