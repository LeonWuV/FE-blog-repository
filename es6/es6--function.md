欢迎访问我的个人博客：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)


<div data-v-41d33d72="" itemprop="articleBody" class="entry-content article-content"><p>如同我们所看到的，ES6 中引入来箭头函数，相比 ES5 来讲是最为直观而明显的特性。</p>
<p>在 ES6 之前，声明一个函数：</p>
<pre><code>function add(a, b) {
  return a + b;
}
add(1, 2); // 3</code></pre>
<p>如果用箭头函数的形式写：</p>
<pre><code>const add = (a, b) =&gt; a + b;
add(1, 2); // 3</code></pre>
<p>计算圆面积的例子：</p>
<pre><code>const square = (r) =&gt; {
  const PI = 3.14;
  return PI*r*r;
}
square(4);</code></pre>
<p>形式上的改变仅仅是一部分，接下来关注一个很有用的特性：默认值。</p>
<h2 data-id="heading-0">默认值</h2>
<p>在 ES6 之前，函数内给定参数的默认值，只能这样：</p>
<pre><code>function add(a, b) {
  console.log(arguments[0]);
  a = a || 2000;
  b = b || 333;
  return a + b;
}
add(); // 2333</code></pre>
<p>但是此方案遇到 boolean 为 false 的 js 值无法工作，例如：</p>
<pre><code>add(0); // 2333</code></pre>
<p>显然，结果错误。运算中 a 仍旧采用了默认值。</p>
<p>所以，当函数传参为 <code>null, undefined, '', 0, -0, NaN</code> 时，短路操作符 || 会给定默认值。</p>
<p>修订版成了这样：</p>
<pre><code>function add(a, b) {
  a = (typeof a !== 'undefined') ? a : 2000;
  b = (typeof b !== 'undefined') ? b : 333;
  return a + b;
}
add(0); // 333</code></pre>
<p>而在 ES6 中，只需要给参数直接赋予默认值即可：</p>
<pre><code>const add = (a = 2000, b = 333) =&gt; a + b;
add(); // 2333
add(0); // 333</code></pre>
<h3 data-id="heading-1">默认值对 arguments 的影响</h3>
<p>在 ES5 中：</p>
<pre><code>function add(a, b) {
  console.log(arguments.length);
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
  a = 200;
  b = 33;
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
}
add(1, 2);
// 2
// true
// true
// true
// true</code></pre>
<p>如果在严格模式下运行，结果是这样的：</p>
<pre><code>function add(a, b) {
  'use strict';
  console.log(arguments.length);
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
  a = 200;
  b = 33;
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
}
add(1, 2);
// 2
// true
// true
// false
// false</code></pre>
<p>在 ES5 中的非严格模式下，更改参数值将会同步的更改 arguments 对象内的参数值，而在严格模式下不会更改。</p>
<p>对于 ES6 来说，无论是否在严格模式下，更改参数值的行为都不会同步更改 arguments 对象。</p>
<pre><code>function add(a = 2000, b = 333) {
  console.log(arguments.length);
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
  a = 200;
  b = 33;
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
}
add(0);
// 1
// true
// false
// false
// false</code></pre>
<p>再来看个例子：</p>
<pre><code>const add = (a = 2000, b = 333) =&gt; {
  console.log(arguments.length);
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
  a = 200;
  b = 33;
  console.log(a === arguments[0]);
  console.log(b === arguments[1]);
}
add(0);
// Uncaught ReferenceError: arguments is not defined</code></pre>
<p>另外需要注意的点是，箭头函数没有自己的 arguments 对象。但它可以访问外围函数的 arguments 对象：</p>
<pre><code>function add(a = 2000, b = 333) {
  return (() =&gt; arguments[0] + arguments[1])();
}
add(); // NaN
add(200, 33); // 233</code></pre>
<p>由于箭头函数没有自己的 arguments 对象，我们想要对箭头函数的参数进行扩展和处理，所以 ES6 中引入了 rest 参数。</p>
<h3 data-id="heading-2">rest 参数</h3>
<p>ES6 内 rest 参数的实现实际上更符合现代编程语言的直觉。在 ES5 中操作 arguments 对象的时候，由于 arguments 对象并非数组对象，需要先把它转换为数组对象来使用数组的方法。</p>
<pre><code>function numSort() {
  return Array.prototype.slice.call(arguments).sort();
}

numSort(3, 6, 5, 1); // [1, 3, 5, 6]</code></pre>
<p>而如果使用 rest 参数：</p>
<pre><code>function numSort(...nums) {
  return nums.sort()
}

numSort(3, 6, 5, 1); // [1, 3, 5, 6]</code></pre>
<p>nums 是一个纯数组对象，在 python 中类似的写法也称为不定参数的写法。因为 python 的参数个数是指定的，使用不定参数的方式是直接以字典或列表作为参数直接传进去，这样不够优雅，有了 <code>*args</code> 的写法。</p>
<p>而在 js 中本身具有 arguments 对象，天然可以利用它来对参数进行操作，引入箭头函数没有 arguments 对象，弥补这样的一个不足，引入 rest 参数这种更优雅的方式。</p>
<p>需要注意，如果同时传入 rest 参数和非 rest 参数：</p>
<pre><code>function numSort(first, ...other) {
  return other.sort()
}

numSort(3, 6, 5, 1); // [1, 5, 6]</code></pre>
<p>rest 参数代表的也是一个指定的参数列表，而非全部参数。另外，如果对调普通参数和 rest 参数的位置：</p>
<pre><code>function numSort(...other, last) {
  return other.sort()
}

numSort(3, 6, 5, 1); // Uncaught SyntaxError: Rest parameter must be last formal parameter</code></pre>
<p>表明了， rest 参数只能位于参数列表的最后一位。</p>
<h2 data-id="heading-3">this</h2>
<p>在 ES6 的箭头函数中，this 值总是绑定到函数的定义：</p>
<pre><code>const obj = {
  name: 'Rainy',
  say: function () {
    setTimeout(() =&gt; {
      console.log(`I'm ${this.name}`);
    })
  }
}
obj.say(); // I'm Rainy</code></pre>
<p>而如果是普通函数，由于 setTimeout 函数内的 this 指向 window，所以找不到 name 值：</p>
<pre><code>const obj = {
  name: 'Rainy',
  say: function () {
    setTimeout(function () {
      console.log(`I'm ${this.name}`);
    })
  }
}
obj.say(); // I'm</code></pre>
<p>可以将箭头函数的该行为看作：</p>
<pre><code>const obj = {
  name: 'Rainy',
  say: function () {
    const self = this;
    setTimeout(function () {
      console.log(`I'm ${self.name}`);
    })
  }
}
obj.say(); // I'm Rainy</code></pre>
<p>实际上这是由于箭头函数本身没有 this，其中的 this 实际上是外部函数的 this 绑定。</p>
<p>且箭头函数中的 this 值无法改变：</p>
<pre><code>const obj = {
  name: 'Rainy',
  say: function () {
    setTimeout((() =&gt; console.log(`I'm ${this.name}`)).bind({name: 'Null'}))
  }
}
obj.say(); // I'm Rainy</code></pre>
<p>而非箭头函数：</p>
<pre><code>const obj = {
  name: 'Rainy',
  say: function () {
    setTimeout((function () {console.log(`I'm ${this.name}`)}).bind({name: 'Null'}))
  }
}
obj.say(); // I'm Null</code></pre>
<p>也正因为如此，箭头函数无法作为构造函数，因为 this 值无法绑定至构造函数的实例。</p>
<hr>
<h2 data-id="heading-4">参考</h2>
<ul>
    <li>《深入理解 ES6》</li>
    <li>《实战 ES2015》</li>
    <li><a href="https://link.juejin.im?target=https%3A%2F%2Fdeveloper.mozilla.org%2Fzh-CN%2F" target="_blank" rel="nofollow noopener noreferrer">MDN</a></li>
</ul></div>


我的个人博客地址：[http://www.xiaolongwu.cn](http://www.xiaolongwu.cn)

我的CSDN博客地址：[https://blog.csdn.net/wxl1555](https://blog.csdn.net/wxl1555)

我的博客园地址：[http://www.cnblogs.com/wuxiaolong555](http://www.cnblogs.com/wuxiaolong555)


如果您对我的博客内容有疑惑或质疑的地方，请在下方评论区留言，或邮件给我，共同学习进步。

邮箱：wuxiaolong802@163.com

**文章转载自：[ES6 札记：函数](https://juejin.im/entry/5afb9483f265da0b84559865?utm_medium=hao.caibaojian.com&utm_source=hao.caibaojian.com)**