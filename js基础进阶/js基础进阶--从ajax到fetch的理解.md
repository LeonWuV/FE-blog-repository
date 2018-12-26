欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

#### 基本知识
##### 1. Ajax是什么？

答：Ajax是一种可以在浏览器和服务器之间使用异步数据传输（HTTP请求）的技术。使用它可以让页面请求少量的数据，而不用刷新整个页面。而传统的页面（不使用Ajax）要刷新部分内容，必须重载整个网页页面。
##### 2. Ajax基于什么？

答：它基于的是XMLHttpRequest（XHR）。这是一个比较粗糙的API，不符合关注分离的设计原则（Separation of Concerns），配置和使用都不是那么友好。

##### 3. Ajax的库？

答：基于上面的原因，各种ajax库引用而生，然而最有名的就是jQuery的API中的 $.ajax() 。 $.ajax() 它的一个优势异步操作，但jQuery的异步操作是基于事件的异步模型，没有promise那么友好。

##### 4. fetch产生的背景？

答：综合上面所讲的各种因素，fetch这个api应运而生，它和XMLHttpRequest都是浏览器window对象的原生api。但好用归好用，它存在着一些问题（这个问题下面详讲，并讲解相对应的解决方案），再加上兼容性问题（ie11以下压根不支持），所以很多开发者使用了axios这个第三方库。

##### 5. 支持promise的库（axios）？

答：axios 这个库现在是一个比较通用的行业解决方案，axios 流行开来的一个原因是promise，另一个原因是基于数据操作的库的流行（vue.js, angular.js, react.js等），而传统的jQuery是基于dom操作的库。但它也存在着缺陷，就是我们使用前，要保证这个库已经被引入。

其实，就我个人而言，我还是比较喜欢使用fetch的。在开发中遇到兼容性的问题，只需要同构fetch即可，而不需要额外的引入一个库。下面就重点说一下fetch。

#### fetch 的使用

```
fetch(url, options)
    .then(response => console.log(responese))
    .catch(err => console.log(err))
```
url：请求的地址

options： 请求的相关参数配置

response：请求返回的对象

then：正常返回数据

catch： 返回异常

请求参数配置 options 详情可参考[MDN fetch](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch#%E6%94%AF%E6%8C%81%E7%9A%84%E8%AF%B7%E6%B1%82%E5%8F%82%E6%95%B0)  我在这里就不再赘述

#### fetch存在的问题及解决方案
1. fetch得到数据你需要两个步骤
```
fetch('https://api.github.com/users')
    .then(res => {
        console.log(res)
        return res.text()
    })
    .then(data => {
        console.log(data)
    })
```
fetch的使用需要浏览器支持promise， fetch的返回值也是一个promise对象；

通过上面的代码，可以发现直接打印返回的 Response 对象中压根就没有数据，要想获取到所需的数据，必须经一个中间的方法 response.text() （[fetch提供了5中方法](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch#Body)），如下：
```
// 具体功能请自行查阅
arrayBuffer()
blob()
json()
text()
formData()
```

 而fetch的封装库axios解决了这个问题，使用起来就要方便的多，它返回的 Response 对象中却有数据，在 data 属性内。参考代码如下：
```
axios.get('https://api.github.com/users')
    .then(res => console.log(res));
```
2. fetch的请求默认是不带 cookie

解决这个问题，需要在 options 中配置 {credentials: 'include'}

3. 并非所有的请求错误都会 reject

也就是说 catch 方法并不能捕获所有的错误，当错误可以用一个状态码（如：404，500等）的形式表示时，fetch 返回的 Promise 不会拥有reject，只有当网络故障或请求被阻止时 catch 才有效。

解决这个问题，我们可判断 Response 对象中的 ok 是否为true，如果不是，用 Promise 手动添加一个 reject 即可。参考代码如下：
```
fetch('https://api.github.com/usrs')
    .then(res => {
        if (res.ok) {
            return res.text()
        } else {
            return Promise.reject('请求失败')
        }
    })
    .then(data => {
        console.log(data)
    })
    .catch(err => {
        console.log(err)
    })
```

当然，如果是用axios库就不需要考虑这个问题，因为axios已经为我们封装好了；

#### fetch和async、await在实际中一起使用
async和await是es7的api，在实际开发中加入一些polyfill库，比如最流行的的babel，我们就可以使用它们了；

如果你还不了解它们，请跳转至：[用async/await来处理异步](https://www.cnblogs.com/SamWeb/p/8417940.html)

在实际中我们会经常遇到异步嵌套的问题，比如：

```
fetch('https://api.github.com/usrs')
    .then(res => {
        if (res.ok) {
            return res.text()
        } else {
            return Promise.reject('请求失败')
        }
    })
    .then(data => {
        let url = data.url
        
        fetch(url)
        .then(res => {
            if (res.ok) {
                return res.text()
            } else {
                return Promise.reject('请求失败')
            }
        })
        .then(data => {
            console.log(data)
        })
    })
    .catch(err => {
        console.log(err)
    })
```

上面就是在收到相应之后再发起一个请求，这样的代码是不是看着很难受；

下面我们来用async和await改一下，感受一下用同步的方式写异步的感觉：
```
// 封装aa
async function aa() {
    try {
        let res = await fetch('https://api.github.com/usrs')
        let data = await res.text()
        let url = data.url
        let res1 = await fetch(url)
        let data1 = await res1.text()
        console.log(data)
    } catch(e) {
        console.log("error", e)
    }
}

// 调用aa
aa()

```
看看上面的代码是不是舒服多了 ，也简单多了；

github资源地址：[]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com