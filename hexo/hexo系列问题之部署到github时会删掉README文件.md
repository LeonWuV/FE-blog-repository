#### 欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 先说为什么
1. 我们执行命令hexo g之后，会把source文件里的.md格式的文件渲染为html文件并放到public下面；
2. 继续执行命令hexo d之后，会把public下面的所有文件提交到对应的XXX.github.io这个仓库；

3. 由于本地public文件夹里没有README.md这个文件，所以在提交public文件时，github会认为你把README.md文件删掉了，同时github也会删掉仓库里的README.md文件，这就是具体的原因
#### 我们解决问题
1. 我们在本地的source文件里新建一个README.md文件。

2. 修改Hexo根目录下的_config.yml文件，将skip_render参数的值设置为README.md
```
skip_render: README.md

//  为什么需要设置这一步呢？
//  因为你执行hexo g命令时，hexo会默认将source文件里的所有md文件渲染为html文件放到public中，
//  同时README.md会被渲染为README.html文件放到public文件里
//  加上这段设置，就是告诉hexo的解析器，你在渲染source文件里的md文件时，跳过README.md文件

```
**我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**


**邮箱：wuxiaolong802@163.com**
