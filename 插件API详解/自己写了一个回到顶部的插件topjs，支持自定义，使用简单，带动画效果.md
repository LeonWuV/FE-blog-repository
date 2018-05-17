#### 欢迎访问我的个人博客：[http://xiaolongwu.cn](http://xiaolongwu.cn)

#### 项目地址
[传送门：https://github.com/LeonWuV/topjs](https://github.com/LeonWuV/topjs)

[线上效果：http://xiaolongwu.cn/topjsDemo/demo.html](http://xiaolongwu.cn/topjsDemo/demo.html)

感兴趣的可以去看看，欢迎大家提issues
#### 前言
top.js是一个体积小、支持自定义、灵活、使用简单、纯原生实现的带动画效果回到顶部的插件；
#### 看看效果
![topjs效果图](https://raw.githubusercontent.com/LeonWuV/topjs/master/img/topjs_2.gif)
#### 使用指南
1. 将top.js引用到项目中；

```
//像这样
<script src="../dist/top.js"></script>
```
2. 实例化topjs

```
new Top()

//到这里  回到顶部的功能就已经实现了
// 不过所有的属性都是默认的，如果需要自定义，请继续向下看
```
3. 自定义的方法

```
// 实例化时接收一个参数，这个参数为一个对象，
// 传入你想要的值就可以

new Top({s:180,th:500,....}); //回到顶部速度为180，scrollTop为500时，按钮显示

```

4. 参数详情

字段名称 | 定义 | 默认值
---|--- | ---
w | 按钮的宽度 | 40px
h | 按钮的高度 | 40px
bt | 按钮固定定位的bottom值 | 40px
rg | 按钮固定定位的right值  | 30px
dImg | 按钮默认背景图 | http://olv6wm3nj.bkt.clouddn.com/18-3-22/16215533.jpg 
hImg | 按钮hover时默认背景图 | http://olv6wm3nj.bkt.clouddn.com/18-3-22/74337023.jpg 
s | 页面回到顶部的速度 | 约等于 70px/15毫秒 
th | 当页面的scrollTop为多少时，按钮显示 | 300px



5. 自定义背景图需要注意的地方

    两种方式：
    -   第一种 直接写一个公网的绝对地址
    -   第二种 可以写相对路径，由于topjs引入到了html文件中，所以必须以html文件为基准
    
```
// 例如，和html文件同级有一个img文件夹，即为
new Top({dImg:"img/xxx.png",....});

// 例如，和html文件父级同级有一个img文件，即为
new Top({dImg:"../img/xxx.png",....});
```

**我的个人博客：[http://xiaolongwu.cn](http://xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**


**邮箱：wuxiaolong802@163.com**

