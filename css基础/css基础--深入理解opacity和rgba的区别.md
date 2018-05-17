##### 欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
首先这两个都与透明度有关，那么他们之间有什么具体的区别呢？在实际工作中我们需要注意什么呢？请您接着往下看
### 语法
#### 1. rgba
首先它是一个属性值，语法为rgba（r,g,b,a）
- r为红色值， 正整数 | 百分数 
- g为绿色值，正整数 | 百分数
- b为蓝色值，正整数 | 百分数
- a为alpha（透明度），值为0 ~ 1之间的小数， 0.0 （完全透明）到 1.0（完全不透明）
- 上面的正整数为十进制0 ~ 255之间的任意值，百分数为0% ~ 100%之间的任意值

```
// 例子：
.box1{
    // 不限于背景颜色，可以是文字颜色，阴影等
     background: rgba(0,0,255,0.4);
}
```
#### 2. opacity
opacity是一个属性，而非一个属性值，语法为 ：

```
opacity: value|inherit;
```
value:不透明度，从 0.0 （完全透明）到 1.0（完全不透明）

```
//例子
.box2{
     background: rgb(0,0,255);
     opacity:0.4;
}
```


### 不同之处
- 有opacity属性的所有后代元素都会继承 opacity 属性，而RGBA后代元素不会继承不透明属性
- 看看下面效果:

```
//部分代码
.box1{
     background: rgba(0,0,255,0.4);
}
.box2{
     background: rgb(0,0,255);
     opacity:0.4;
}
```

![opacity和rgba的区别效果图](http://olv6wm3nj.bkt.clouddn.com/18-3-30/85615926.jpg)

我们从效果图中不难看出，
- rgba只是背景颜色有透明效果
- 而有opacity属性元素的后代都会继承这个透明属性，包括但不限于文字图片等

---

**我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**