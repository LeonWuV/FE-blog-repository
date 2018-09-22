欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### npm的常见命令
1. 下载安装某个模块 npm install <Module Name> -D（添加到开发环境）/-S（添加到生产环境）
2. 使用以下命令来卸载模块 npm uninstall <package>    

3. 查看所有全局安装的模块   npm list -g

4. 查看依赖的某个模块的当前版本号   npm list <package>  -g    //不带-g为此项目内查找
5.  升级依赖包版本 npm update <package> 

6. 搜索模块 npm search <package>

7. 浏览器端打开项目地址 npm repo <package>   //是git地址

8. 在浏览器端查看项目  npm home <package> //是git地址

9. 查看全局安装地址 npm root -g 
10. npm outdated 查看当前过期依赖，其中current显示当前安装版本，latest显示依赖包的最新版本，wanted显示我们可以升级到可以不破坏当前代码的版本
11. npm view <jquery> versions  查看npm服务器上某个包的所有版本,只显示版本号      
13.  npm view <jquery> version   查看npm服务器上某个包的最新版本,只显示版本号       
12. npm info <jquery>  查看npm服务器上某个包的所有版本     类似于（npm view <jquery>）
14. npm的start命令是一个特殊的脚本名称，其特殊性表现在，在命令行中使用npm start就可以执行其在脚本里对应的命令，如果对应的此脚本名称不是start，想要在命令行中运行时，需要这样用npm run {script name} 如npm run build
15. npm config ls 或者npm config list  查看npm的配置文件
16. npm config ls -l 获取更多的npm的配置文件
17. npm config get registry  查看npm下载包的源
18. npm config set registry  <url>  设置npm下载包的源
19. npm i -g npm@5.6.0 安装指定版本的npm
20. npm i -g npm@latest  安装最新版本的npm
21. npm cache clean --force 删除缓存目录下的所有数据。为了保证缓存数据的有效性和完整性，需要加上 --force 参数
22. npm cache verify 验证缓存数据的完整性和有效性，清楚垃圾数据


#### 不定期更新......
---

我的github资源地址：[npm常见命令](https://github.com/LeonWuV/FE-blog-repository/blob/master/nodejs/npm%E5%B8%B8%E8%A7%81%E5%91%BD%E4%BB%A4.md)

我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com