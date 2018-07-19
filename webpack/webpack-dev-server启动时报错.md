欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 显示如下报错

```
D:\myProjectDemos\webpackDemo\node_modules\ajv-keywords\keywords\instanceof.js:52
    throw new Error('invalid "instanceof" keyword value ' + c);
    ^

Error: invalid "instanceof" keyword value Promise
    at getConstructor (D:\myProjectDemos\webpackDemo\node_modules\ajv-keywords\keywords\instanceof.js:52:11)
    at Ajv.compile (D:\myProjectDemos\webpackDemo\node_modules\ajv-keywords\keywords\instanceof.js:21:27)
    at Object.useCustomRule (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\compile\index.js:275:26)
    at Object.generate_custom [as code] (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\dotjs\custom.js:32:24)
    at Object.generate_validate [as validate] (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\dotjs\validate.js:347:35)
    at Object.generate_anyOf [as code] (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\dotjs\anyOf.js:34:27)
    at generate_validate (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\dotjs\validate.js:347:35)
    at localCompile (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\compile\index.js:87:22)
    at Ajv.compile (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\compile\index.js:56:13)
    at Ajv._compile (D:\myProjectDemos\webpackDemo\node_modules\ajv\lib\ajv.js:358:27)
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! ll@1.0.0 dev: `webpack-dev-server`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the ll@1.0.0 dev script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\q\AppData\Roaming\npm-cache\_logs\2018-07-06T09_19_18_374Z-debug.log

```
#### 解决方案

1. 我的webpack是3.6版本的，
2. 我查了一下我webpack-dev-server版本是3.1.4的版本，
3. 这两个版本不兼容，把webpack-dev-server降到2.x版本就好使了



我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[https://github.com/webpack-dev-server启动时报错.md](https://github.com/LeonWuV/FE-blog-repository/blob/master/webpack/webpack-dev-server%E5%90%AF%E5%8A%A8%E6%97%B6%E6%8A%A5%E9%94%99.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com