##### 欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

今天我们来看看实现随即排序的几种做法
#### 方法一
思路为：遍历数组，每次循环都随机一个在数组长度范围内的数，并交换本次循环的位置和随机数位置上的元素

```
function randomSort1(arr){
    for (let i = 0, l = arr.length; i < l; i++) {
        let rc = parseInt(Math.random() * l );
// 让当前循环的数组元素和随机出来的数组元素交换位置
        const empty = arr[i];
        arr[i] = arr[rc];
        arr[rc] = empty;       
     }
     return arr;
}
// 例子
var arr1 = [1,2,3,4,5,6,7,8,9];
// 下面两次的结果肯定是不一样的；
console.log(randomSort1(arr1));
console.log(randomSort1(arr1));
```
#### 方法二
思路：
1. 申明一个新的空数组,利用while循环，如果数组长度大于0，就继续循环； 
2. 每次循环都随机一个在数组长度范围内的数，将随机数位置上的元素push到新数组里，
3. 并利用splice（[对splice不太理解的同学可以看这里](https://blog.csdn.net/wxl1555/article/details/79388292)）截取出随机数位置上的元素，同时也修改了原始数组的长度；
```
function randomSort2(arr){
    var mixedArr = [];
    while(arr.length > 0){
        let rc = parseInt(Math.random() * arr.length );
         mixedArr.push(arr[rc]);
         arr.splice(rc,1);
    }
    return mixedArr;
}
// 例子
var arr1 = [1,2,3,4,5,6,7,8,9];

console.log(randomSort2(arr1));
```
#### 方法三
思路：利用传入sort排序中的比较函数,比较函数的规则如下：
1. 如果 compareFunction(a, b)的返回值 小于 0 ，那么 a 会被排列到 b 之前；
2. 如果 compareFunction(a, b)的返回值 等于 0 ，那么a 和 b 的相对位置不变；
3. 如果 compareFunction(a, b)的返回值 大于 0 ，那么b 会被排列到 a 之前；

```
 function randomSort3(arr){
    arr.sort(function(a,b){
        return Math.random() - 0.5;
    });
    return arr;
}
// 例子
var arr1 = [1,2,3,4,5,6,7,8,9];

console.log(randomSort3(arr1));
```

如果不传比较函数，会按照字典顺序对元素进行排序，看下面例子

```
var array = [3, 2, 104, 8, 340, 540]  
array.sort()  
console.log(array) // [104, 2, 3, 340, 540, 8]
```
这几种方法就是我目前了解到的，如果您还有别的方案可以再下方留言或者和我联系，相互学习

**我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)**

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**