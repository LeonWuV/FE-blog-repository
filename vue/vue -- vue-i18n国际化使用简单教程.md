欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 前言
vue-i18n是一个针对于vue的国际化插件，使用非常简单，具体使用方式看我细细道来。
#### 实现方式
这里我们直接讲在实际开发中如何使用以及注意事项；

##### 1. 下载包

```
npm install vue-i18n
```
##### 2. 配置
在main.js文件中加入如下配置

```
// 引入插件和语言包
import VueI18n from 'vue-i18n'
import zh from '@/i18n/langs/zh'
import en from '@/i18n/langs/en'
Vue.use(VueI18n)

//实例化vue-i18n
const i18n = new VueI18n({

  // 从本地存储中取，如果没有默认为中文，
  // 这样可以解决切换语言后，没记住选择的语言，刷新页面后还是默认的语言
  locale: localStorage.getItem('lang') || 'zh',
  
  messages: {
    'zh': zh, // 中文语言包
    'en': en // 英文语言包
  }
})

// 将i18n实例挂载到vue上
new Vue({
  el: '#app',
  i18n,
  router,
  store,
  template: '<App/>',
  components: { App }
})
```
##### 3. 创建中、英文包文件
创建两个文件，一个为zh.js代表中文，en.js代表英文，具体内容格式如下

```
//zh.js
export default {
  nav: {
    home: '首页',
    monitor: '监控',
    analyze: '分析',
    alarm: '报警',
    maintenance: '运维',
    config: '配置',
    device: '设备',
    scada: '画面'
  },
  confirm: {
    ok: '确认',
    cancel: '取消',
    content: '你确认要退出系统吗？',
    logout: '退 出'
  },
}
```

```
//en.js
export default {
  nav: {
    home: 'Home', //首页
    monitor: 'Monitor', //监控
    analyze: 'Analyze', //分析
    alarm: 'Alarm', // 报警
    maintenance: 'Maintenance', //运维
    config: 'Config', //配置
    device: 'Device', //设备
    scada: 'Scada' //画面
  },
  confirm: {
    ok: 'Logout', //退出
    cancel: 'Cancel', //取消
    content: 'Are you sure you want to quit the system?', //你确认要退出系统吗
    logout: 'Logout' //
  }
}
```
##### 4. 在组件中使用
我们先看vue-i18n的模板语法

```
//第一种
<span v-text="$t('nav.home')"></span>

//第二种
<span>{{$t('nav.home')}}</span>
```
$t()是vue-i18n的模板语法，必须这么写；'nav.home'就是中、英文包文件中的key；

所以我们把页面中的中文全部换成这种带key的表达式即可；

##### 5. 如何切换中英文
关于这点，vue-i18n给我们提供了一个全局变量locale，通过他我们可以查看当前使用的语言，也可以通过他改变当前使用的语言；

具体用法：

```
// 查看当前使用的语言
console.log(this.$i18n.locale)

// 改变当前使用的语言
this.$i18n.locale = 'en'  // 将当前使用的语言切换到英文
```
一般在项目中，我们会使用如下方式切换语言

```
// 切换语言按钮
<v-list-tile  @click="onChangeLang">
  <v-list-tile-title>中文 / EN</v-list-tile-title>
</v-list-tile>
<v-list-tile  @click="onLogOutClick">
  <v-list-tile-title >{{$t('confirm.logout')}}</v-list-tile-title>
</v-list-tile>


// 切换方法onChangeLang的处理, 这里的弹出框是element-ui的组件
onChangeLang() {
  this.$confirm(this.$t('changeLang.content'), this.$t('changeLang.tip'), {
    confirmButtonText: this.$t('changeLang.ok'),
    cancelButtonText: this.$t('confirm.cancel'),
    type: 'warning'
  })
    .then(() => {
      let lang = this.$i18n.locale
      if (lang === 'zh') {
        this.$i18n.locale = 'en'
        // 对应main.js配置文件中的localStorage的get方法
        localStorage.setItem('lang', this.lang)
      } else {
        this.$i18n.locale = 'zh'
        localStorage.setItem('lang', this.lang)
      }
    })
    .catch(() => {})
}
```
到这里我们的国际就算是做完了。

#### 可能会遇到的问题
##### 1. 记不住切换后的语言
就是我们切换语言后，刷新又是默认语言，这点我们在上面已经用本地存储localStorage解决了；

##### 2. 将this.$t() 写到了data属性里，切换语言不起作用
就像下图这样的写法，切换会没作用；

![错误1](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/i18n/wrong1.jpg)
![错误2](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/i18n/wrong2.jpg)

但是我们换个写法就好了，如下图；

![正确1](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/i18n/right1.jpg)
![image](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/i18n/right2.jpg)

官方的解决办法是，建议我们将表达式写到computed属性里，不要写到data里

###### 附上 ：[vue-i18n官方issues链接](https://github.com/kazupon/vue-i18n/issues/271) ，里面也有博主的回复；
---

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[vue -- vue-i18n国际化使用简单教程](https://github.com/LeonWuV/FE-blog-repository/blob/master/vue/vue%20--%20vue-i18n%E5%9B%BD%E9%99%85%E5%8C%96%E4%BD%BF%E7%94%A8%E7%AE%80%E5%8D%95%E6%95%99%E7%A8%8B.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.co