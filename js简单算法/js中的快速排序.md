### 快速排序代码

```
function quickSort(arr){
    //判断如果数组长度为一，则直接返回
        if(arr.length <= 1){
	    return arr;
        }
			
	//找出一个标识，一般为最中间的数组
	var tag = Math.floor(arr.length/2);//向下取整，
			
	//截取标识位的数组，这里splice(index,howmany,addNewItem)可以改变原数组的长度，
	//而同样可以截取的slice(starIndex,endIndex)方法不能改变原数组的长度；			
	var middle = arr.splice(tag,1)[0];
		
	//申明两个空数组
	var left = [],right = [];
	for(i = 0; i < arr.length; i ++){
			
	//比标识位小的放到左边，大的放到右边
	if(arr[i] < middle){
	    left.push(arr[i]);
	}else{
		right.push(arr[i]);
	}

	//利用递归，不停的自调用此方法，直到每个数组长度都为1时return；
			
	return quickSort(left).concat([middle],quickSort(right));
}

------------------------------------------------

    arr1 = [15,12,18,20,2,15,34,100,7];
	var aa = quickSort(arr1);
	console.log(aa); //[2, 7, 12, 15, 15, 18, 20, 34, 100];
	



		
```

**如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。**

**邮箱：wuxiaolong802@163.com**

