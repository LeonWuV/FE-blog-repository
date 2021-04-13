## 前言

通过这篇文章，您将清楚为什么需要配置多个ssh秘钥，如何生成多个秘钥，如何配置并让多个秘钥生效，如何测试秘钥是否生效等。



## 配置多个ssh秘钥的场景

在公司，我们提交代码可能是coding，或者可能是gitlab，或者是其他。同时我们还需要维护自己的github或者gitee账号。

公司的gitlab邮箱账号肯定和自己的github邮箱账号不一样，如果我们都选用ssh的协议来提交代码，那么gitlab邮箱生成的秘钥不能在github上使用。

这时，就需要生成多个秘钥，分别配置gitlib、github等多个代码托管网站。

## 如何生成多个秘钥



生成默认秘钥使用下面这段命令即可，系统会弹出让输入密码，输入密码即可

```bash
ssh-keygen -t rsa -C "邮箱地址"
```



生成自定义秘钥命令：

```bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa.别名 -C "邮箱地址"
```



我们分别生成gitlab和github的秘钥：

```bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa.github -C "邮箱地址"

ssh-keygen -t rsa -f ~/.ssh/id_rsa.gitlab -C "邮箱地址"
```



然后使用如下命令，查看公钥文件，将内容全部复制：

```bash
cat id_rsa.github.pub
```

将公钥填写到相应的网站，一搬都是在网站的设置中,.有个ssh keys的配置，我们将公钥填写进去即可。

这个填写过程我在这里就忽略了。

重复上面的步骤，填写另一个公钥



到这里还没有完成，我们需要将秘钥注册到**ssh-agent**中，因为ssh默认去找的id_rsa秘钥，不会识别我们自定义生成的秘钥。

注册秘钥：

```bash
ssh-add -K ~/.ssh/id_rsa.github
```



查看添加结果：

```
ssh-add -l
```



下来我们还需要在.ssh文件夹下创建一个config的文件

```bash
touch config

# vim编辑config文件
vim config
```



内容如下：

```bash

 	Host git@gitlab.xxx.com  #平台访问地址
  HostName gitlab #随便起
  User xxx #随便起
  IdentityFile ~/.ssh/id_rsa.gitlab  #秘钥的地址

  Host git@github.com
  HostName github
  User xxx
  IdentityFile ~/.ssh/id_rsa.github

```



测试联通性：

```bash
#这里跟的是我们在config配置中Host字段对应的名字
ssh -T git@github.com
```



如果返回：

> Hi xxxxx! You've successfully authenticated, but GitHub does not provide shell access.
>
> 则表示链接成功

到这里我们就配置完成了。




欢迎大家关注博主的公众号：<strong>猿人说事</strong>

<p align="center">
  <img src="http://storage.360buyimg.com/cdn-upload/yuanRenQR83057a63644441fda8a095ae68c574c5.jpg" alt="猿人说事-logo" width="150px" height="150px"/>
  <br>
</p>

github资源地址：[Mac如何生成并配置多个ssh秘钥]()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，我们共同学习进步。

邮箱：wuxiaolong802@163.com











​