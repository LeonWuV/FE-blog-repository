欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
先说一下什么是事件总线，其实就是订阅发布者模式；

比如有一个bus对象，这个对象上有两个方法，一个是on（监听，也就是订阅），一个是emit（触发，也就是发布），我们通过on方法去监听某个事件，再用emit去触发这个事件，同时调用on中的回调函数，这样就完成了一次事件触发；

这是一种设计模式，和语言没有关系；

如果不太了解什么是订阅发布者模式，请移步看这篇文章[JavaScript设计模式--观察者模式（发布者-订阅者模式）](https://blog.csdn.net/wxl1555/article/details/84632408)

在实际开发中，往往最麻烦的就是各种组件之间的传值问题；如果利用事件总线就会让这件事情变得很简单；

### vue自带事件总线的短板
我们都知道在vue被实例化之后，他就具备了充当事件总线对象的能力，在他上面挂了两个方法，是$emit和$on；

而vue文档说的很明白，$emit会触发当前实例上的事件，附加参数都会传给监听器回调；

由于在实际工作中，我们都是以组件的形式开发，每个组件就是一个实例；

所以利用vue自带的总线能力有很大的局限性，最多只能从子组件触发到父组件中，而不能在非父子组件之间传值；

所以这时，我们就需要有一个全局的事件总线对象，让我们挂载监听事件和触发事件；

##### 举个例子，子组件向父组件传值；父组件向子组件传值很简单，我们这里不说
```
// 子组件中
<template>
  <div>
    <span>{{childValue}}</span>
    <input type="button" value="点击触发" @click="send">
  </div>
</template>
<script>
  export default {
    data () {
      return {
        child: '我是子组件的数据'
      }
    },
    methods: {
      send () {
      // 如果传多个值就用逗号隔开 a, b, c
        this.$emit('fromChild', this.child)
      }
    }
  }
</script>
```

```
// 父组件
<template>
  <div>
    <span>{{name}}</span>
    // 在父组件中监听 fromChild事件
    <child @fromChild="onFromChild"></child>
  </div>
</template>
<script>
  import child from './child'
  export default {
    components: {
      child
    },
    data () {
      return {
        name: ''
      }
    },
    methods: {
      onFromChild: function (data) {
        // data就是子组件传过来的值
        // 如果传过来多个值就用逗号隔开去接收 data1, data2, data3
        this.name = data
      }
    }
  }
</script>
```

### 实现全局事件总线对象的几种方式
#### 方式一，也是我自己使用的方式（推荐使用，简单）
大概思路是 ：在main.js，也就是入口文件中，我们在vue的原型上添加一个bus对象；

具体实现方式如下：

##### 下面的组件A和组件B可以是项目中任意两个组件
```
//在mian.js中
Vue.prototype.bus = new Vue()  //这样我们就实现了全局的事件总线对象

//组件A中，监听事件
this.bus.$on('updata', function(data) {
    console.log(data)  //data就是触发updata事件带过来的数据
})

//组件B中，触发事件
this.bus.$on('updata', data)  //data就是触发updata事件要带走的数据

```
#### 方式二，稍微有点麻烦，但也很容易理解
大概的实现思路： 新建一个bus.js文件， 在这个文件里实例化一下vue；然后在组件A和组件B中分别引入这个bus.js文件，将事件监听和事件触发都挂到bus.js这个实例上，这样就可以实现全局的监听与触发了

##### 写个例子

##### bus.js文件
```
// bus.js文件
import Vue from 'vue'
export default new Vue()
```

##### 组件A

```
// 组件A ，监听事件send
<template>
  <div>
    <span>{{name}}</span>
  </div>
</template>
<script>
  import Bus from './bus.js'
  export default {
    data () {
      return {
        name: ''
      }
    },
    created() {
      let _this = this
      // 用$on监听事件并接受数据
      Bus.$on('send', (data) => {
        _this.name = data
        console.log(data)
      })
    },
    methods: {}
  }
</script>
```
##### 组件B

```
// 组件B， 触发事件send
<template>
  <div>
    <input type="button" value="点击触发" @click="onClick">
  </div>
</template>
<script>
  import Bus from './bus.js'
  export default {
    data () {
      return {
        elValue: '我是B组件数据'
      }
    },
    methods: {
        // 发送数据
      onClick() {
        Bus.$emit('send', this.elValue)
      }
    }
  }
</script>

```
这样我们就完成了一个简单非父子组件之间的传值


我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[vue -- 非父子组件传值，事件总线（eventbus）的使用方式](https://github.com/LeonWuV/FE-blog-repository/blob/master/vue/vue%20--%20%E9%9D%9E%E7%88%B6%E5%AD%90%E7%BB%84%E4%BB%B6%E4%BC%A0%E5%80%BC%EF%BC%8C%E4%BA%8B%E4%BB%B6%E6%80%BB%E7%BA%BF%EF%BC%88eventbus%EF%BC%89%E7%9A%84%E4%BD%BF%E7%94%A8%E6%96%B9%E5%BC%8F.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com