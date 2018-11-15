欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
在vue项目中组件之间的通讯是很常见的问题，同时也是很重要的问题，我们大致可以将其分为三种情况：

1. 父传子：在父组件中绑定值，在子组件中用props接收
2. 子传父：在父组件中监听一个事件，在子组件中利用$emit触发这个事件并带上数据作为第二个参数，这时父组件中监听事件的回调函数就会被调用，回调函数的参数就是子组件带上来的数据，这样就可以在父组件中使用子组件的数据了，
3. 兄弟之间的传递：我们可以使用事件总线（eventBus）来轻松的解决，其实就是发布订阅者模式

今天我们要看的是父组件如何直接调取子组件的数据和方法，而不是通过子组件传上来的

在这里我们要理解父组件直接拿事件是在父组件上，子组件传上来数据，事件是在子组件上，是完全不同的两种情况

#### 代码展示
子组件 children.vue,我们在子组件中定义了数据sonData和方法sonMethod

```
// children.vue

<template>
  <div>我是 children</div>
</template>

<script>
export default {
  data: () => ({
    sonData: '我是子组件的数据！'
  }),
  methods: {
    sonMethod() {
      console.log('我是子组件的方法！')
    }
  },
  computed: {
    
  },
  created() {

  }
}
</script>
```
父组件 文件

```
// 父组件

<template>
  <div>
    <children ref='ch'>
    </children>
    <h1 @click="onclick">父组件</h1>
  </div>
</template>

<script>
import children from './coms/children'
export default {
  data() {
    return {}
  },
  components: {
    children
  },
  methods: {
    onclick() {
    // 或者 let chil = this.$refs['ch']
      let chil = this.$refs.ch

    // 父组件可以通过$refs拿到子组件的对象
    // 然后直接调用子组件的 methods里的方法和data里的数据
      console.log(chil) //子组件对象
      console.log(chil.sonData) // 我是子组件的数据
      console.log(chil.sonMethod()) // 我是子组件的方法
    }
  }
}
</script>
```
#### 注意事项
因为 ref 本身是作为渲染结果被创建的，在初始渲染的时候你不能访问它们 - 它们还不存在！，所以它不是响应式的，不能用在模板或者计算属性中。

---


我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[vue -- Cannot set property 'render' of undefined解决方法]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com