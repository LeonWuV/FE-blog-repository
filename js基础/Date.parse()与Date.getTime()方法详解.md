#### 这两个方法的返回值都是 1970/1/1 午夜距离该日期时间的毫秒数
##### 实际中如何使用


下面的例子中，我们将取得从 1970/01/01 到 2017/03/19 的毫秒数

1、Date.parse()的 使用

```
<script type="text/javascript">

var d = Date.parse("2017/03/19")
//或者var d = Date.parse(new Date());
//返回当前时间毫秒数
console.log(d)
//返回的结果1489881600000，后三位默认为000

</script>
```


2、Date.getTime()的使用方法

```
var dateNow = new Date();
	var ff = dateNow.getTime();
	console.log(ff);
//打印出来的是1489899243209
```
