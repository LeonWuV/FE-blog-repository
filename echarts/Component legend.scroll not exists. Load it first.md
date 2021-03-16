

###  先看问题

Component legend.scroll not exists. Load it first--

这是由于echarts报错引起的一个问题，大概意思就是说，我们缺少一个模块，让我们先引入这个模块；

### 如何引起的

我们在优化代码时，为了减少包的体积，对echarts做了按需引入，大概如下；

```javascript
// 按需加载echarts

// 引入主模块
import echarts from 'echarts/lib/echarts';

// 引入工具模块
import 'echarts/lib/component/legend';
import 'echarts/lib/component/dataZoom';
import 'echarts/lib/component/title';
import 'echarts/lib/component/axis';
import 'echarts/lib/component/tooltip';
import 'echarts/lib/component/markPoint';
import 'echarts/lib/component/markLine';
import 'echarts/lib/component/timeline';

// 引入图表模块
import 'echarts/lib/chart/bar';
import 'echarts/lib/chart/line';
import 'echarts/lib/chart/pie';
```

我们需要使用scroll功能，但是没有引入scroll这个模块，这时会出现上面题目中的报错；

这个其实是很常见的一类问题；

### 如何解决

这类问题很简单，引入所需的模块即可

```javascript
import 'echarts/lib/component/legendScroll';
```

我们再来看下，echarts按需引入的模块都有哪些

```javascript
import echarts from 'echarts/lib/echarts';
import "echarts/lib/chart/line";
import "echarts/lib/chart/bar";
import "echarts/lib/chart/pie";
import "echarts/lib/chart/scatter";
import "echarts/lib/chart/radar";
import "echarts/lib/chart/map";
import "echarts/lib/chart/tree";
import "echarts/lib/chart/treemap";
import "echarts/lib/chart/graph";
import "echarts/lib/chart/gauge";
import "echarts/lib/chart/funnel";
import "echarts/lib/chart/parallel";
import "echarts/lib/chart/sankey";
import "echarts/lib/chart/boxplot";
import "echarts/lib/chart/candlestick";
import "echarts/lib/chart/effectScatter";
import "echarts/lib/chart/lines";
import "echarts/lib/chart/heatmap";
import "echarts/lib/chart/pictorialBar";
import "echarts/lib/chart/themeRiver";
import "echarts/lib/chart/sunburst";
import "echarts/lib/chart/custom";
import "echarts/lib/component/grid";
import "echarts/lib/component/polar";
import "echarts/lib/component/geo";
import "echarts/lib/component/singleAxis";
import "echarts/lib/component/parallel";
import "echarts/lib/component/calendar";
import "echarts/lib/component/graphic";
import "echarts/lib/component/toolbox";
import "echarts/lib/component/tooltip";
import "echarts/lib/component/axisPointer";
import "echarts/lib/component/brush";
import "echarts/lib/component/title";
import "echarts/lib/component/timeline";
import "echarts/lib/component/markPoint";
import "echarts/lib/component/markLine";
import "echarts/lib/component/markArea";
import "echarts/lib/component/legendScroll";
import "echarts/lib/component/legend";
import "echarts/lib/component/dataZoom";
import "echarts/lib/component/dataZoomInside";
import "echarts/lib/component/dataZoomSlider";
import "echarts/lib/component/visualMap";
import "echarts/lib/component/visualMapContinuous";
import "echarts/lib/component/visualMapPiecewise";
import "echarts/lib/component/dataset";
import "echarts/zrender/lib/vml/vml";
import "echarts/zrender/lib/svg/svg";
```

这样我们就很完美的解决了这类问题；



欢迎大家关注博主的公众号，不定期会推送文章；

<p align="center">
  <img src="http://storage.360buyimg.com/cdn-upload/yuanRenQR83057a63644441fda8a095ae68c574c5.jpg" alt="猿人说事-logo" width="150px" height="150px"/>
  <br>
</p>
<p align="center">
  <strong>猿人说事</strong>
  <br>
</p>

---

github资源地址：[echarts -- Component legend.scroll not exists. Load it first](https://github.com/LeonWuV/FE-blog-repository/blob/master/echarts/Component%20legend.scroll%20not%20exists.%20Load%20it%20first.md)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com





