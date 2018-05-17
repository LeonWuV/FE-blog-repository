首先需要说明，一个HTML标签的class属性可以有多个class类名，并用空格隔开，这些class类名会同时起作用。如果出现两个以上的class类设置了相同的css样式，则会根据这些class类在==css文件和style标签==中加载的先后顺序，后面的覆盖前面的，和HTML标签中class属性的类名前后没有关系。

以下方法中，被操作的class类名均不带==点==(.)这个特殊符号！

- 增加一个class类
    
```
//增加一个bbb的class类，aaa与bbb同时存在
 $(".aaa").addClass("bbb");
 
```
- 删除一个class类

```
//删除aaa这个class类
$(".aaa").removeClass("aaa");
```
- 修改一个class类

```
//方法一
    //先删除，后添加。或者先添加后删除均可
    $(".aaa").addClass("bbb").removeClass("aaa");
    $(".aaa").removeClass("aaa").addClass("bbb");
//方法二
    //利用attr方法
    $(".aaa").attr("class","bbb");
    //这里需要注意的是，如果这个HTML标签不止有aaa这一个类时，
    //这个方法之后，这个HTML标签会只有bbb这一个class类,
    
    //当然也可以设置多个
    $(".aaa").attr("class","bbb ccc ddd");
    
```
- 判断是否存在一个class类

```
//判断HTML标签中是否有bbb这个class类
$(".aaa").hasClass("bbb");
//返回值是一个boolean值，存在返回true，不存在返回false。
```

- 实例

```
//实现一个hover功能，鼠标上去为aaa，离开为bbb
$(".ccc").hover(function () {
    $(this).addClass("aaa");
    $(this).removeClass("bbb");
}, function () {
    $(this).addClass("bbb");
    $(this).removeClass("aaa");
}); 

```

