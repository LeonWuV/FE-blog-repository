欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
#### 1. 前言
flex弹性盒，是一种布局方式，当页面需要适应不同的屏幕大小以及设备类型时，它依然能确保元素

拥有更恰当的排布行为，弹性盒属于 CSS 3 部分，IE9 以下不支持，现代浏览器指的就是 IE9 及以上的浏览器

#### 2. flex的优势
举个例子：这里我们要实现一个功能，让一个dom元素水平垂直居中;

##### 2.1 传统实现方式（1），居中元素的宽高已知

```
    .box1{
            position: relative;
            background: darkcyan;
            width: 800px;
            height: 300px;
    }
    
    .box1-son{
        position: absolute;
        border: 1px solid seashell;
        width: 200px;
        height: 200px;
        top: 50%;
        left: 50%;
        transform: translate(-100px,-100px);
    }
    
    <div class="box1">
        <div class="box1-son">传统布局1</div>
    </div>
```
##### 2.2 传统实现方式（2），居中元素的宽高未知


```
    .box2{
        position: relative;
        background: darkcyan;
        width: 800px;
        height: 300px;
        
    }
    
    .box2-son{
        position: absolute;
        border: 1px solid seashell;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
    }


    <div class="box2">
        <div class="box2-son">传统布局2</div>
    </div>
```
当然这种方式同时以可以实现方式一的功能

##### 2.3 flex方式实现

```
    .flex-container {
        background-color: #FECE3F;
        width: 600px;
        height: 220px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    
    .flex-item {
        width: 120px;
        height: 120px;
        background-color: blue;
    }
```
这种方式很简单，我们只需要给容器添加三个属性即可，即：

```
    display: flex;
    justify-content: center;
    align-items: center;
```
就是这么简单，display: flex表示容器为弹性盒，justify-content: center表示子元素在主轴方向居中，align-items: center表示子元素在侧轴方向居中；

这里的主轴和侧轴不理解没关系，请看下面介绍；



#### 3. flex的基本理解
首先理解flex的几个概念：
1. 弹性容器 (Flex container)即父容器，包含着弹性项目的父元素，通过设置 display 属性的值为 flex 
来定义弹性容器；
2. 弹性项目 (Flex item)即子容器，弹性容器的每个子元素都称为弹性项目；
3. 一个弹性容器可以包含多个弹性项目，但是一个弹性项目 只有一个直接弹性容器；
4. 主轴 (main axis)和侧轴 (cross axis，也称交叉轴)，弹性项目依次排列的轴为主轴，与其垂直的那根轴为侧轴，flex默认水平方向为主轴
5. 我们可以通过改变弹性容器的flex-direction属性来改变它的主轴方向
6. flex 布局涉及到 12 个 CSS 属性（不含 display: flex），其中父容器、子容器各 6 个。不过常用的属性只有 4 个，父容器、子容器各 2 个；

<p align="center">
  <img width="600" src="https://upload-images.jianshu.io/upload_images/1662958-4b155644efe4ca7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/563" alt="logo of vue-awesome repository">
</p>




#### 4. 父容器的属性 共6个

前两个为常用属性，我们先说常用的

    - justify-content   
    - align-items       
    - flex-direction
    - flex-wrap
    - flex-flow
    - align-content

##### 4.1 justify-content

该属性定义了子容器在主轴上的排列对齐方式。它有5个取值

```
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}

flex-start（默认值）：左对齐
flex-end：右对齐
center： 居中
space-between：两端对齐，项目之间的间隔都相等。
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
```

![justify-content](http://www.runoob.com/wp-content/uploads/2015/07/c55dfe8e3422458b50e985552ef13ba5.png)

##### 4.2 align-items 

该属性定义了子容器在侧轴上的排列对齐方式。它有5个取值


```
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}

flex-start：交叉轴的起点对齐。
flex-end：交叉轴的终点对齐。
center：交叉轴的中点对齐。
baseline: 项目的第一行文字的基线对齐。
stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
```
![align-items ](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071012.png)

##### 4.3  flex-direction

该属性指定了内部元素是如何在 flex 容器中布局的，定义了主轴的方向(正方向或反方向)
```
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}

row（默认值）：主轴为水平方向，起点在左端。
row-reverse：主轴为水平方向，起点在右端。
column：主轴为垂直方向，起点在上沿。
column-reverse：主轴为垂直方向，起点在下沿。
```

![flex-direction](http://www.runoob.com/wp-content/uploads/2015/07/0cbe5f8268121114e87d0546e53cda6e.png)

##### 4.4  flex-wrap

flex-wrap属性定义，如果一条轴线排不下，如何换行

```
.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}

nowrap（默认）：不换行。
wrap：换行，第一行在上方。
wrap-reverse：换行，第一行在下方。
```
##### 4.5  flex-flow

flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap。


##### 4.6  align-content

align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。




```
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}

flex-start：与交叉轴的起点对齐。
flex-end：与交叉轴的终点对齐。
center：与交叉轴的中点对齐。
space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
stretch（默认值）：轴线占满整个交叉轴。
```

![align-content](http://www.runoob.com/wp-content/uploads/2015/07/f10918ccb8a13247c9d47715a2bd2c33.png)

#### 5. 子容器属性 共6个

前两个为常用的属性，我们先说常用的属性

    - flex
    - align-self
    - order
    - flex-grow
    - flex-shrink
    - flex-basis
   
##### 5.1 flex 

flex 属性，是flex-grow，flex-shrink，felx-basis三个属性的简写：

属性    | 默认值    | 描述
--- |--- | ---
flex-grow | 0 | 定义弹性盒子项的拉伸因子，即子项分配父项剩余空间的比，默认值为 0
flex-shrink | 1 | 指定了 flex 元素的收缩规则，子项的收缩所占的份数，默认值为1 [ 当所有子项相加的宽度大于父项的宽度，每个子项减少的多出的父项宽度的 1/n ]
felx-basis | auto | 指定了 flex 元素在主轴方向上的初始大小，即子项的宽度
    
    如果属性值为none        则表示 0 0 auto
    如果属性值为1或者auto   则表示 1 1 auto
    
    

属性值可以为1-3个值连用，他们的具体用法请看下面单独属性的详解

##### 5.2 flex-grow

flex-grow 属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。

我们通过下面的例子来更直观的认识一下flex-grow

```
.flex {
  display: flex;
  width: 600px;
  margin: 0;
  padding: 0;
  list-style: none;
}
.flex li:nth-child(1) {
  width: 200px;
  background-color: red;
}
.flex li:nth-child(2) {
  flex-grow: 1;
  width: 50px;
  background-color: blue;
}
.flex li:nth-child(3) {
  flex-grow: 3;
  width: 50px;
  background-color: green;
}

<ul class="flex">
  <li>a</li>
  <li>b</li>
  <li>c</li>
</ul>

```

结果如下

![flex-grow结果](http://olv6wm3nj.bkt.clouddn.com/18-5-4/15523922.jpg)

    
```
上面的例子中 b，c 两项都定义了 flex-grow属性，
flex容器的剩余空间分成了4份其中 b 占 1 份，c 占 3 份，即 1:3，
flex 容器的剩余空间长度为600-200-50-50=300px
所以最终abc的长度分别为：a: 200px；b: 50+(300*1/4)=125px；c: 50+(300*3/4)=275px
```

##### 5.3  flex-shrink

flex-shrink 属性的默认值为1，如果没有显示定义该属性，将会自动按照默认值 1 在所有子项宽度相加之后计算比率来进行空间收缩

这个属性正好和flex-grow相反，为缩小时所占的份数，这里我们可以自己动手写一下，自己感受一下，我就不再举例了

##### 5.4  flex-basis

flex-basis 属性的初始值为auto，设置或检索弹性盒伸缩基准值，如果所有子元素的基准值之和大于剩余空间，则会根据每项设置的基准值，按比率伸缩剩余空间

取值可以为百分比，也可以为具体的数值，如（20%，或者300px）

这里需要注意的是 ，如果子容器设置了flex-basis属性，则他自己的width属性将会失效，这里可以理解为flex-basis属性的权重高于width的权重


##### 5.5  order

order 属性规定了弹性容器中的可伸缩项目在布局时的顺序，元素按照 order 属性的数值的增序进行布局，数值小的排在前面，可以为负值，默认值为 0，拥有相同 order 属性值的元素按照它们在源代码中出现的顺序进行布局



##### 5.6  align-self


align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。


该属性可能取6个值，除了auto，其他都与align-items属性完全一致。


```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

文章到这里就结束了，感谢阅读。





github资源地址：[https://github.com/深入理解弹性盒flex布局.md](https://github.com/LeonWuV/leonwuv.github.io/blob/hexo/source/_posts/%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%BC%B9%E6%80%A7%E7%9B%92flex%E5%B8%83%E5%B1%80.md)

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

csdn博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com