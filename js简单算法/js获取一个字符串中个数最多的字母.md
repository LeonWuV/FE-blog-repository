欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)
### 前言 
如题

### 代码
```
        function num (str){
            var a = {};
            var b = str.split("");
            // key为元素   值为个数
            for (let i = 0; i < b.length; i++) {
                if(a[b[i]]){
                    a[b[i]]++;
                }else{
                    a[b[i]] = 1;
                }
            }
            // 通过比较找出最大的
            var maxLetter = "";
            var levelNum = 0;
            for (const k in a) {
                if(a[k] > levelNum){
                    levelNum = a[k];
                    maxLetter = k;
                }
            }
            
            console.log(maxLetter + ":" + levelNum);
            
            return maxLetter;
        }
        var cc = "dafsfsfasfafaqertyyuuioll,mmnnbvvsfsdfqgsafsafgff";
        num(cc);
```

我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com