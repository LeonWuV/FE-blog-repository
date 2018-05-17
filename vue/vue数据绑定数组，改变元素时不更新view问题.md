#### 欢迎访问我的个人博客：[http://xiaolongwu.cn](http://xiaolongwu.cn)

#### 前言
关于这个问题，官网上说的很清楚[官方文档](https://cn.vuejs.org/v2/guide/list.html#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
![1](http://olv6wm3nj.bkt.clouddn.com/18-3-19/38442253.jpg)
![2](http://olv6wm3nj.bkt.clouddn.com/18-3-19/52644173.jpg)
#### 写个例子
##### HTML
```
<body>
    <div class="box">
        <div v-for="aa in aas">{{aa}}</div>
        <button @click="change">变数据 </button>
    </div>
</body>
```
##### js

```
var vm = new Vue({
            el:".box",
            data:{
                aas:["ss","ddd","fff","bbb"]
            },
            methods:{
                change(){
                // 点击按钮时，改变aas的最后一个元素，
                // 数据变了 但是view没有更新
                    this.aas[3] = 444;
                }
            }
        })
```
##### 为什么
因为vue实现双向数据绑定的机制是数据劫持，也就是在所有对象上有个Object.defineProperty()方法，通过监听set，get方法去实现，而数组没有这两个方法，所以就不会更新view；解决方案就是，需要我们主动通知vue；
##### 解决方案1
```
 methods:{
    change(){
        this.aas[3] = 444;
        // 在vm实例上通知
        vm.$set(this.aas,3,this.aas[3])
    }
}
```
##### 解决方案2
```
 methods:{
    change(){
        this.aas[3] = 444;
        // 在全局对象上通知
        Vue.set(this.aas,3,this.aas[3])
    }
}
```
##### 解决方案3
```
 methods:{
    change(){
        // vue本身可以监听到数组的一些方法,例如:
        // push(),pop(),shift(),unshift(),splice(),sort(),reverse()
        this.aas.splice(3,1,"444");
    }
}
```

**我的个人博客：[http://xiaolongwu.cn](http://xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**


**邮箱：wuxiaolong802@163.com**