欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
在工作中我们可能会遇到这样的需求，当浏览器切换到别的标签页或着最小化时，我们需要暂停页面上正在播放的视频或者音乐，这个需求就会用到我下面要说的这个知识点：

1. document.visibilityState 
2. document.hidden
3. visibilitychange
### 具体用法
浏览器标签页隐藏或者显示时会改变document.visibilityState和document.hidden的值，我们可以通过visibilitychange这个事件去监听他们状态值的变化；

```
// 我在这里建议大家亲自试试以下代码
document.addEventListener("visibilitychange", function() {
  console.log( document.visibilityState );
  console.log(document.hidden);
});
```
上面代码中：
- document.visibilityState有两个值，分别为hidden和visible,hidden表示标签页被隐藏了，visible则反之；
- document.hidden也有两个值，分别为true和false，true表示标签页被隐藏了，false则反之；




我的github资源地址：[js基础--如何判断浏览器标签页是隐藏或者显示状态](https://github.com/LeonWuV/FE-blog-repository/blob/master/js%E5%9F%BA%E7%A1%80/js%E5%9F%BA%E7%A1%80--%E5%A6%82%E4%BD%95%E5%88%A4%E6%96%AD%E6%B5%8F%E8%A7%88%E5%99%A8%E6%A0%87%E7%AD%BE%E9%A1%B5%E6%98%AF%E9%9A%90%E8%97%8F%E6%88%96%E8%80%85%E6%98%BE%E7%A4%BA%E7%8A%B6%E6%80%81.md)

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)


如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com