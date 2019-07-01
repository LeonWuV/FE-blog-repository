欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言
由于项目迭代开发比较快，所以就需要在每个迭代版本上打tag的需求，博主之前的策略为，创建一些名字为tag-xx的分支来充当tag的角色，但是这样显然是不可取的，所以就实践了一下tag的功能并记录下来；
### 正文
假如我们的项目到某个阶段的版本封板了，要上线，在这时，通常是要打tag留个标记的；

这时我们就利用git的tag命令进行一系列操作，具体如下：

1. 我们需要在发版的master分支打tag，先添加一个tag

```
git tag -a 0.1 -m "version 0.1″

// git tag 是命令
// -a 0.1是增加 名为0.1的标签
// -m 后面是标签的注释
```

2. 然后推送tag到远程

```
git push origin --tags
// --tags参数表示提交所有tag至服务器端
// 注意：普通的git push origin master操作不会推送标签到服务器端
```

3. 查看已有tag列表

```
git tag --list
// 后面的--list可以省略
```

4. 假如我们要切换到某个tag

```
git checkout [tagName/branchName]  
//  这里与切换分支的道理一样，也可以将tag和分支理解为一个东西，这个会好理解一点
```

5. 删除本地tag

```
git tag -d <tagName>
// 与删除分支的命令相似
// 我们切换到这个tag之后如果需要修改东西，
// 就使用新建并且换分支的命令，切出新的分支修改代码
```

6.  删除远端服务器的tag

```
git push origin :refs/tags/0.1

// 后面跟tag的名字，例如0.1
```


我的github资源地址：[git--git tag相关命令和实践记录](https://github.com/LeonWuV/FE-blog-repository/blob/master/git/git--git%20tag%E7%9B%B8%E5%85%B3%E5%91%BD%E4%BB%A4%E5%92%8C%E5%AE%9E%E8%B7%B5%E8%AE%B0%E5%BD%95.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com