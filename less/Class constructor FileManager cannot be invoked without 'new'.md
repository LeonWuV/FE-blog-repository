欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### webpack打包时出现以下问题
```
ERROR in ./src/pages/score/components/current/no-join/index.less
Module build failed (from ./node_modules/_mini-css-extract-plugin@0.5.0@mini-css-extract-plugin/dist/loader.js):
ModuleBuildError: Module build failed (from ./node_modules/_less-loader@4.1.0@less-loader/dist/cjs.js):


Class constructor FileManager cannot be invoked without 'new'
      in undefined (line undefined, column undefined)
    at runLoaders (/home/admin/build/node_modules/_webpack@4.39.2@webpack/lib/NormalModule.js:313:20)
    at /home/admin/build/node_modules/_loader-runner@2.4.0@loader-runner/lib/LoaderRunner.js:367:11
    at /home/admin/build/node_modules/_loader-runner@2.4.0@loader-runner/lib/LoaderRunner.js:233:18
    at context.callback (/home/admin/build/node_modules/_loader-runner@2.4.0@loader-runner/lib/LoaderRunner.js:111:13)
```
#### 这个问题是由于less升级导致的bug；
具体的解决方案： [https://github.com/less/less.js/issues/3414](https://github.com/less/less.js/issues/3414)

#### 解决方案一
也就是将less锁定版本在3.10以下，及3.9.0。

#### 解决方案二
或者将less-loader版本升级到5.0.0即可。

---


我的github资源地址：[Class constructor FileManager cannot be invoked without 'new']()

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com