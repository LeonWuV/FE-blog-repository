欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
首先，proxyTable是我们在本地开发环境中调试接口用的，目的是为了解决本地跨域的问题，因为本地地址为localhost:xxxx/xxx

在线上的生产环境是没用的！！！

假设我们用的是vue-cli命令行工具生成的webpack项目模板，我们很容易能在config文件夹下面找到index.js文件。

### 本地如何配置 

假设我要请求的地址为
```
'http://p.iotwhere.com:38080/scada/json/aa.tpl'
```

我们在index.js文件中找到如下代码：我推荐了一种写法，后面我会说为什么

![proxyTable配置](http://olv6wm3nj.bkt.clouddn.com/18-7-19/46851830.jpg)

那么我请求的那段代码就是这样的
```
axios.get('/scada/json/aa.tpl').then((res) => {
    //........
})
```
稍微解释一下其中的原理：当发请求的时候，proxy就会起作用，他会在接口'/scada'前面加上 'http://p.iotwhere.com:38080',成为 'http://p.iotwhere.com:38080/scada/json/aa.tpl' 由于我们配置中的 pathRewrite字段需要将 '/scada'写为 '/scada',所以请求接口还是 'http://p.iotwhere.com:38080/scada/json/aa.tpl'

继续向下看，干货还在后面

### 假设几种其它的写法
#### 假设一
如果proxyTable配置是这样的

```
proxyTable: {
  '/scada': {
    target: 'http://p.iotwhere.com:38080', 
    changeOrigin: true,
    pathRewrite: {
        '^/scada': '/'     
    }
  }
```
那么我们的请求代码必须写成这样

```
axios.get('/scada/scada/json/aa.tpl').then((res) => {
    //........
    //是不是有点难受
})
```
#### 假设二
如果proxyTable配置是这样的，也就是重新起个名字

```
proxyTable: {
  '/api': {
    target: 'http://p.iotwhere.com:38080', 
    changeOrigin: true,
    pathRewrite: {
        '^/api': '/'     
    }
  }
```
那么我们的请求代码必须写成这样

```
axios.get('/api/scada/json/aa.tpl').then((res) => {
    //........
    //这种写法还能接受，但是有个致命的缺点
})
```

再向下看，看看我推荐的写法的真真优势

### 打包上线的问题

这里只说代码上线之后和接口在同源情况下，如果不同源则存在跨域，这里先不考虑这种情况

假如我们把打包后的代码也部署到了 'http://p.iotwhere.com:38080'上

上线后的代码为生产环境，没有了proxy

那么他是怎么解析请求的呢？比如下面这个请求

```
axios.get('/scada/json/aa.tpl').then((res) => {
    //........

})
```
由于 '/'表示的是根目录的意思，所以会解析为hostname + port + 请求的地址，即为 'http://p.iotwhere.com:38080/scada/json/aa.tpl' ，没有一点问题，接口肯定能请求到

那么如果按照上面我说的假设一或者假设二的写法呢？

是不是会解析为 'http://p.iotwhere.com:38080/scada/scada/json/aa.tpl' 和 'http://p.iotwhere.com:38080/api/scada/scada/json/aa.tpl'

所以，假设一和假设二需要在打包之前修改请求地址才能打包，增加了许多不必要的麻烦

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[https://github.com/关于proxyTable的配置在开发环境和生产环境中的原理解析.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/webpack/webpack%20--%20%E5%85%B3%E4%BA%8EproxyTable%E7%9A%84%E9%85%8D%E7%BD%AE%E5%9C%A8%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E5%92%8C%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83%E4%B8%AD%E7%9A%84%E5%8E%9F%E7%90%86%E8%A7%A3%E6%9E%90.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com