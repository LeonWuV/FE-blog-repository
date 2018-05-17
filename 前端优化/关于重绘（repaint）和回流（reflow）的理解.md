### 欢迎访问我的个人网站  [xiaolongwu.cn](http://xiaolongwu.cn)

#### 什么是页面的重绘与回流

当页面中的部分或者全部元素改变宽度和高度、或者位置发生变化、删除或者增加某个或者某些元素时、某个元素影藏或者显示时，这时页面就需要重新加载了，这就叫做回流。

当页面的中的可见性发上变化时，比如：背景颜色吗，文字颜色等，这样就形成了重绘。

注：从上面可以看出，回流必将引起重绘，而重绘不一定会引起回流。

#### 怎么减少重绘和回流呢

一、使用cssText属性，在各浏览器中测试都通过了。一行代码即可，实在很妙。如

```
var head= document.getElementById("head");

head.style.cssText="width:200px;height:70px;display:bolck";
```
但cssText也有个缺点，会覆盖之前的样式。如

```
<div style="color:red;">TEST</div>
```
想给该div在添加个css属性width

```
div.style.cssText = "width:200px;"
```
这时虽然width属性加上了，但之前的color却被覆盖丢失了。因此使用cssText时应该采用叠加的方式以保留原有的样式。

```
function setStyle(el, strCss){
    var sty = el.style;
    sty.cssText = sty.cssText + strCss;
}
```
二、不要一条条的修改DOM属性，可以预先定义好CSS的Class，然后修改DOM的ClassName；这方法应该很好理解我就不写例子了

**我的个人博客：[http://xiaolongwu.cn](http://xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**


**邮箱：wuxiaolong802@163.com**