欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
关于cmder优点和如何下载，还有它的min版和完全版有啥区别，我在这里就不说了，网上文章一大堆，请自行搜索，我在这里只说首次安装存在问题最多的地方

每次用cmder手动一层一层的进入目标文件夹，是一件很麻烦的事儿。所以，将cmder添加到系统右键菜单是个很好地解决方法。就像使用git bash那样的方便；
### 如何添加
1. 也是2的前置任务，把 Cmder加到环境变量


把cmder.exe存放的目录添加到系统环境变量中；
加完之后,验证是否添加成功，Win+r（也就是键盘左边alt旁边，
上面有四个小方格的键+r）下输入cmder,回车即可打开cmder。
2. 添加cmder到系统右键菜单


如果1验证成功，则以管理员权限打开cmd，输入：
```
Cmder.exe  /REGISTER ALL
```

验证是否成功：在任意文件夹点击鼠标右键如果显示为下图则表示成功，否则失败：

![系统右键菜单成功显示结果](http://olv6wm3nj.bkt.clouddn.com/18-4-10/39101390.jpg)
  
### 出现如下报错的原因
![安装的错误提示图](http://olv6wm3nj.bkt.clouddn.com/18-4-10/75814302.jpg)

If you get a message "Access Denied" ensure you are executing the command in anAdministrator prompt.

出现这个错误的原因就是你没有用管理员身份打开命令行工具；
### 解决方案
切记必须要要用管理员身份打开cmd，然后输入上面2中的命令即可


![image](http://olv6wm3nj.bkt.clouddn.com/18-4-10/14931061.jpg)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com