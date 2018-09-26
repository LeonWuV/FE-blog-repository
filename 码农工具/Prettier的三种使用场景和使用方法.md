欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

Prettier是最近很火的一个代码美化工具，其中文意思是“漂亮的、机灵的”，它能够解析代码，使用你自己设定的规则来重新打印出格式规范的代码。

他的整个圈子很强大，有基于各种编辑器的插件（vs code，atom），有脚本类的，有插件类的（eslint的插件eslint-plugin-prettier）。

更多有关prettier的信息，请点击 [这里](https://github.com/prettier)
#### Prettier具有以下几个有优点：
1. 可配置化
2. 支持多种语言
3. 集成多数的编辑器
4. 简洁的配置项

#### 官方给的例子
使用Prettier在code review时不需要再讨论代码样式，节省了时间与精力。下面使用官方的例子来简单的了解下它的工作方式。

**格式化前**
```
foo(reallyLongArg(), omgSoManyParameters(), IShouldRefactorThis(), isThereSeriouslyAnotherOne());
```

**格式化后**

```
foo(
  reallyLongArg(),
  omgSoManyParameters(),
  IShouldRefactorThis(),
  isThereSeriouslyAnotherOne()
);
```

#### 几种使用方式

#####  一、编辑器插件类

在这里以vs code为例，也是最简单的使用方式，我在这里强烈推荐，我自己也是这么用的。

这种方式的优点就是开发时随意写，写完后一键格式化。按下快捷键，Prettier就会帮我们重写想要格式化的文件，不需要像eslint那样报错后我们需要一行一行去修改。

安装vs code的插件Prettier - Code formatter，这里不再赘述如何安装vs code的插件。

使用方法：
> 格式化某个文件时，在打开文件的当前页按shift + alt + f

> 格式话某段代码时，先选中这段代码，在按 shift + alt + f

##### 二、脚本类
**安装**

使用yarn
```
yarn add prettier --dev --exact
// and globally
yarn global add prettier
```
使用npm

```
npm install --save-dev --save-exact prettier
// and globally
npm install --g prettier
```
这里需要全局安装一下prettier，不然prettier命令会无效。


```
//测试是否安装成功
prettier -v
// 会打印出版本号
```
**使用**

1.使用prettier默认配置规则格式化文件方式

```
prettier --write <文件路劲+文件名>

//例如，格式化当前路劲下的aaa.js文件
prettier --write  ./aaa.js
```
2.自定义配置文件使用方式

自定义文件的格式可以有多种
- .prettierrc 文件，支持yaml和json格式；或者加上扩展名也可以，可选的扩展名有 .yaml/.yml/.json
- .prettierrc.toml 文件
- prettier.config.js or .prettierrc.js 返回一个对象
- 或者在package.json文件中加上prettier对象

关于这部分的[官方文档](https://prettier.io/docs/en/configuration.html)

以上这几个文件名是prettier默认会去查找的文件，执行方式为

```
//默认配置文件都是在根目录下，只要使用了以上几种命名都可使用下面的命令
prettier --config --write <文件路劲+文件名>
// 例如
prettier --config --write ./aaa.js

//如果配置文件没在根目录下，则需要加上配置文件的路劲
prettier --config <配置文件路径+文件名> --write <文件路劲+文件名>

//其实他的规则很符合一般脚本规则，比如webpack，eslint，babel等
```


json 配置文件写法
```
{
    "semi": false,
    "singleQuote": true
}
```
toml 文件写法
```
#  .prettierrc.toml
semi = false
singleQuote = true
```
yaml文件写法

```
# .prettierrc
semi: false
singleQuote: true
```
js写法
```
// prettier.config.js or .prettierrc.js 返回对象
module.exports = {
  semi: false,
  singleQuote: true
};
```
##### 插件类
**这里以eslint为例**

当做eslint的插件来使用
```
//安装
yarn add --dev prettier eslint-plugin-prettier
```
在eslint的配置文件中添加配置

在.eslintrc 或者 .eslintrc.json 或者 .eslintrc.js文件中

```
{
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  }
}
```




我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

github资源地址：[关于代码格式化工具Prettier的多种使用方法总结](https://github.com/LeonWuV/FE-blog-repository/blob/master/%E7%A0%81%E5%86%9C%E5%B7%A5%E5%85%B7/Prettier%E7%9A%84%E4%B8%89%E7%A7%8D%E4%BD%BF%E7%94%A8%E5%9C%BA%E6%99%AF%E5%92%8C%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com