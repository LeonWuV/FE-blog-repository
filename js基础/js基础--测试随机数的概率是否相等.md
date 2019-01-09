欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

### 前言
今天我们来做一个有趣的测试，那就是我们在某个范围之间取随机数时，每项被随机到的概率是否相等。

### 随机方法

我们都知道Math.random()的结果是[0, 1)之间的小数，结果包括0但是不包括1。

那么很简单就会想到Math.random() * n的结果是[0, n)之间的小数，结果包括0但是不包括n。

那么parseInt(Math.random() * n)的结果就是[0, n)之间的正整数， parseInt(Math.random() * n + 1)的结果就是[1, n+1)之间的正整数。

那么parseInt(Math.random() * (m - n) + n)的结果就是[n, m)之间的正整数。

### 开始证明

我们首先写一个方法，随机7500个在a和b之间的数。

```
function randomArr(a, b) {
    var obj = {}
    for (let i = 0; i < 7500; i++) {
      const n = parseInt(Math.random() * (b - a) + a);
      if (!obj[n]) {
        obj[n] = 1;
      } else {
        obj[n] ++;
      }
    }
    console.log(obj)
}
  
  randomArr(5, 10)
  randomArr(5, 15)
  randomArr(5, 20)
```

结果如下：

![测试结果](https://raw.githubusercontent.com/LeonWuV/ftp/master/pictures/random/1546968496.jpg)

由此，我们大致能得出结论，随机数的每项概率基本是相等的；

github资源地址：[]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com