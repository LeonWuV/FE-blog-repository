
欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言

大概的情景是这样的，jquery版本为1.10.1版本；浏览器为ie11；报错info为--Object doesn't support property or method 'attachEvent'

### 分析原因
其主要原因为ie的监听事件问题，ie11以下为attachEvent，而ie11为addEventListener。

但是，jquery为什么没有兼容到这种情况呢，所以我能想到的合理剧情是这样的，jquery1.10.1的出生日期比ie11早；

然后我就上git查看了下jquery的release版本时间，和百度了一下ie11的发行时间，查询结果如下：

[Internet Explorer 11 百度百科](https://baike.baidu.com/item/Internet%20Explorer%2011/8863973?fr=aladdin)；

[git 上关于jquery1.10.1的release版本信息](https://github.com/jquery/jquery/releases/tag/1.10.1)

为方便大家，我截图如下

##### ie11版本日期

![ie11版本日期](http://olv6wm3nj.bkt.clouddn.com/18-4-18/38919517.jpg)

##### jquery1.10.1版本日期

![jquery1.10.1版本日期](http://olv6wm3nj.bkt.clouddn.com/18-4-18/52674745.jpg)

### 解决方案

看了上面的分析，我们很容易就能想到换一个高一点的jquery版本就好了，只要出生日期比ie11晚就没问题

我这里换的是1.12.1的版本，结果问题自然就解决了


---



我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com
