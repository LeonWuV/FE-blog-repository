欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
本文前提是在win系统下，macos系统请绕过；
### 先看tree
tree命令是cmd自带的功能，用于生成文件目录结构，请看下面例子，我这里使用的是cmder替代cmd
![tree命令](http://olv6wm3nj.bkt.clouddn.com/18-4-11/68226554.jpg)
### 再看treer

![tree命令 写入文件](http://olv6wm3nj.bkt.clouddn.com/18-4-11/11955331.jpg)

### treer的具体安装和用法
#### 1、安装treer

```
//安装
npm install treer -g

// 查看是否安装成功，弹出版本号则安装成功
treer --version
```
下来我们就可以直接使用treer了，具体生成结果看上图
#### 2、指定目录
默认的目录为当前的路径，可以通过-d传入指定的路径，d为directory（目录）的简写，

```
treer -d <指定路径>
```

![指定目录](http://olv6wm3nj.bkt.clouddn.com/18-4-11/57405460.jpg)

#### 3、导出结果
可将结果导出到文件中，e为export（导出）的简写

```
// 如果找不到此文件，会自动新建一个文件
treer -e <导出路径/文件名>
```
![导出到文件](http://olv6wm3nj.bkt.clouddn.com/18-4-11/1660235.jpg)
#### 4、忽略指定目录文件
有时候我们需要忽略一些文件名，比如我们的node_modules文件夹，i为ignore（忽视）的简写

```
treer -i <"文件名，支持正则表达式/regex/哦">
```

[参考文章--treer:命令行生成目录结构的实用小工具](https://segmentfault.com/a/1190000009163772)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com