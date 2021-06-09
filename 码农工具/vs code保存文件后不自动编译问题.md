### 问题

​	某一次编码中，写好代码，按下Ctrl + S，结果vs code控制台没有任何反应，也就是代码没有被自动编译。

​	之前，当写完代码，保存之后，控制台就会显示Compiling...，表示正在编译中，过一会儿会显示compiled successfully in xxxs，表示用了多少秒重新编译成功了。

### 定位问题

​	重新打开一个别的项目，改动文件，保存后会自动编译。

​	所以排除是vs code工具的问题。

​	在本项目中，先stash当前的代码，再切换分支，改动代码，保存后会自动编译。

​	所以排除是项目配置的问题。

​	由于本次代码改动较大，增加了文件夹和文件。改动不是本次增加和改动的文件，保存后会自动编译。

​	所以，应该是本次改代码出的问题。

### 发现问题

​	最后发现，新增加的文件夹名称为小写开头，而在代码中，引用的时候，文件夹名称写成了大写。

​	**修改代码中文件夹名称为小写，问题解决。**



欢迎大家关注博主的公众号：<strong>猿人说事</strong>

<p align="center">
  <img src="http://storage.360buyimg.com/cdn-upload/yuanRenQR83057a63644441fda8a095ae68c574c5.jpg" alt="猿人说事-logo" width="150px" height="150px"/>
  <br>
</p>

---

github资源地址：[ ]( https://github.com/LeonWuV/FE-blog-repository/blob/master/)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，我们共同学习进步。

邮箱：wuxiaolong802@163.com

