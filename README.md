### 前端问题记录
1. [HTML相关](#html)
2. [CSS相关](#css)
3. [JAVASCRIPT相关](#javascript)
4. [DOM相关](#dom)
5. [HTTP相关](#http)
4. [VUE相关](#vue)
5. [算法相关](#sort)
6. [网络安全相关](#web)
7. [webpack相关](#webpack)
8. [其他](#other)
#### Html相关
##### <div id="html">1 html语义化</div>
意义：根据内容的结构化（内容语义化），选择合适的标签（代码语义化）便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。
注意：
1.尽可能少的使用无语义的标签div和span；
2.在语义不明显时，既可以使用div或者p时，尽量用p, 因为p在默认情况下有上下间距，对兼容特殊终端有利；
3.不要使用纯样式标签，如：b、font、u等，改用css设置。
4.需要强调的文本，可以包含在strong或者em标签中（浏览器预设样式，能用CSS指定就不用他们），strong默认样式是加粗（不要用b），em是斜体（不用i）；
5.使用表格时，标题要用caption，表头用thead，主体部分用tbody包围，尾部用tfoot包围。表头和一般单元格要区分开，表头用th，单元格用td；
6.表单域要用fieldset标签包起来，并用legend标签说明表单的用途；
7.每个input标签对应的说明文本都需要使用label标签，并且通过为input设置id属性，在lable标签中设置for=someld来让说明文本和相对应的input关联起来。

新标签：
![h5新元素](http://pd4ar0u4q.bkt.clouddn.com/h5%E6%96%B0%E5%85%83%E7%B4%A0.png)
##### 2 meta viewport相关
```htmlbars
<!DOCTYPE html>  H5标准声明，使用 HTML5 doctype，不区分大小写
<head lang=”en”> 标准的 lang 属性写法
<meta charset=’utf-8′>    声明文档使用的字符编码
<meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>   优先使用 IE 最新版本和 Chrome
<meta name=”description” content=”不超过150个字符”/>       页面描述
<meta name=”keywords” content=””/>      页面关键词
<meta name=”author” content=”name, email@gmail.com”/>    网页作者
<meta name=”robots” content=”index,follow”/>      搜索引擎抓取
<meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no”> 为移动设备添加 viewport
<meta name=”apple-mobile-web-app-title” content=”标题”> iOS 设备 begin
<meta name=”apple-mobile-web-app-capable” content=”yes”/>  添加到主屏后的标题（iOS 6 新增）
是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏
<meta name=”apple-itunes-app” content=”app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL”>
添加智能 App 广告条 Smart App Banner（iOS 6+ Safari）
<meta name=”apple-mobile-web-app-status-bar-style” content=”black”/>
<meta name=”format-detection” content=”telphone=no, email=no”/>  设置苹果工具栏颜色
<meta name=”renderer” content=”webkit”>  启用360浏览器的极速模式(webkit)
<meta http-equiv=”X-UA-Compatible” content=”IE=edge”>     避免IE使用兼容模式
<meta http-equiv=”Cache-Control” content=”no-siteapp” />    不让百度转码
<meta name=”HandheldFriendly” content=”true”>     针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓
<meta name=”MobileOptimized” content=”320″>   微软的老式浏览器
<meta name=”screen-orientation” content=”portrait”>   uc强制竖屏
<meta name=”x5-orientation” content=”portrait”>    QQ强制竖屏
<meta name=”full-screen” content=”yes”>              UC强制全屏
<meta name=”x5-fullscreen” content=”true”>       QQ强制全屏
<meta name=”browsermode” content=”application”>   UC应用模式
<meta name=”x5-page-mode” content=”app”>    QQ应用模式
<meta name=”msapplication-tap-highlight” content=”no”>    windows phone 点击无高光
设置页面不缓存
<meta http-equiv=”pragma” content=”no-cache”>
<meta http-equiv=”cache-control” content=”no-cache”>
<meta http-equiv=”expires” content=”0″>
```
##### 3 canvas 相关
```javascript
使用前需要获得上下文环境，暂不支持3d
常用api:
	1.fillRect(x,y,width,height)实心矩形
	2.strokeRect(x,y,width,height)空心矩形
	3.fillText("Hello world",200,200);实心文字
    4.strokeText("Hello world",200,300)空心文字
各种东西！！！
```
##### 新标签兼容低版本
1. ie9之前版本通过createElement创建html5新标签
2. 引入html5shiv.js
#### <div id="css">CSS相关</div>
##### 1.盒模型
1.ie盒模型算上border、padding及自身（不算margin），标准的只算上自身窗体的大小
css设置方法如下
```css
/* 标准模型 */
box-sizing:content-box;
 /*IE模型*/
box-sizing:border-box;
```
2.margin、border、padding、content由外到里
3.几种获得宽高的方式
+ dom.style.width/height 
　　这种方式只能取到dom元素内联样式所设置的宽高，也就是说如果该节点的样式是在style标签中或外联的CSS文件中设置的话，通过这种方法是获取不到dom的宽高的。
+ dom.currentStyle.width/height 
　　这种方式获取的是在页面渲染完成后的结果，就是说不管是哪种方式设置的样式，都能获取到。但这种方式只有IE浏览器支持。
+ window.getComputedStyle(dom).width/height
　　这种方式的原理和2是一样的，这个可以兼容更多的浏览器，通用性好一些。
+ dom.getBoundingClientRect().width/height
　　这种方式是根据元素在视窗中的绝对位置来获取宽高的
+ dom.offsetWidth/offsetHeight
　　这个就没什么好说的了，最常用的，也是兼容最好的。

4.拓展 各种获得宽高的方式
+ 获取屏幕的高度和宽度（屏幕分辨率）：
window.screen.height/width
+ 获取屏幕工作区域的高度和宽度（去掉状态栏）：
window.screen.availHeight/availWidth
+ 网页全文的高度和宽度：
document.body.scrollHeight/Width
+ 滚动条卷上去的高度和向右卷的宽度：
document.body.scrollTop/scrollLeft
+ 网页可见区域的高度和宽度（不加边线）：
document.body.clientHeight/clientWidth
+ 网页可见区域的高度和宽度（加边线）：
document.body.offsetHeight/offsetWidth

5.边距重叠解决方案(BFC)
BFC原理
+ 内部的box会在垂直方向，一个接一个的放置
每个元素的margin box的左边，与包含块border box的左边相接触（对于从做往右的格式化，否则相反）
+ box垂直方向的距离由margin决定，属于同一个bfc的两个相邻box的margin会发生重叠
+ bfc的区域不会与浮动区域的box重叠
+ bfc是一个页面上的独立的容器，外面的元素不会影响bfc里的元素，反过来，里面的也不会影响外面的
+ 计算bfc高度的时候，浮动元素也会参与计算
创建bfc
+ float属性不为none（脱离文档流）
+ position为absolute或fixed
+ display为inline-block,table-cell,table-caption,flex,inine-flex
+ overflow不为visible
+ 根元素
demo
```htmlbars
<section class="top">
	<h1>上</h1>
	这块margin-bottom:30px;
</section>
<!-- 给下面这个块添加一个父元素，在父元素上创建bfc -->
<div style="overflow:hidden">
	<section class="bottom">
	<h1>下</h1>
	这块margin-top:50px;
	</section>
</div>
```
##### css reset 和 normalize.css 有什么区别
+ 两者都是通过重置样式，保持浏览器样式的一致性
+ 前者几乎为所有标签添加了样式，后者保持了许多浏览器样式，保持尽可能的一致
+ 后者修复了常见的桌面端和移动端浏览器的bug：包含了HTML5元素的显示设置、预格式化文字的font-size问题、在IE9中SVG的溢出、许多出现在各浏览器和操作系统中的与表单相关的bug。
+ 前者中含有大段的继承链
+ 后者模块化，文档较前者来说丰富
##### 居中方法
水平方向上
```css
针对inline, 内联块inline-block, 内联表inline-table, inline-flex元素及img,span,button等元素
.text_div{
	text-align:center;
}
```
```css
不定宽块状元素居中
.text_div{
    margin:0 auto;
}

```
```css
通过给父元素设置 float，然后给父元素设置 position:relative 和 left:50%，子元素设置 position:relative 和 left: -50% 来实现水平居中。
.wrap{
    float:left;
    position:relative;
    left:50%;
    clear:both;
}
.wrap-center{
    left:-50%;
}
```
垂直居中
```css
单行内联(inline-)元素垂直居中 
通过设置内联元素的高度(height)和行高(line-height)相等，从而使元素垂直居中。

.text_div{
    height: 120px;
    line-height: 120px;
}
```
```css
利用表布局
.father {
    display: table;
}
.children {
    display: table-cell;
    vertical-align: middle;
}
```
```css
flex布局
.center-flex {
    display: flex;
    flex-direction: column;//上下排列
    justify-content: center;
}
```
```css
绝对布局方式
已知高度
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  height: 100px;
  margin-top: -50px; 
}
未知高度
.parent {
    position: relative;
}
.child {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
}
```
垂直水平居中根据上方结合
```css
flex方式
.parent {
    display: flex;
    justify-content: center;
    align-items: center;
}
grid方式
.parent {
  height: 140px;
  display: grid;
}
.child { 
  margin: auto;
}
```
##### css优先级确定
+ 每个选择器都有权值，权值越大越优先
+ 继承的样式优先级低于自身指定样式
+ ！important优先级最高 js也无法修改
+ 权值相同时，靠近元素的样式优先级高  顺序为内联样式表（标签内部）> 内部样式表（当前文件中）> 外部样式表（外部文件中）
##### bfc内容见盒模型
##### 如何清除浮动
不清楚浮动会发生高度塌陷：浮动元素父元素高度自适应（父元素不写高度时，子元素写了浮动后，父元素会发生高度塌陷）
+ clear清除浮动（添加空div法）在浮动元素下方添加空div,并给该元素写css样式：   {clear:both;height:0;overflow:hidden;}
+ 给浮动元素父级设置高度
+ 父级同时浮动（需要给父级同级元素添加浮动）
+ 父级设置成inline-block，其margin: 0 auto居中方式失效
+ 利用br标签的clear属性
+ 给父级添加overflow:hidden 清除浮动方法
+ 万能清除法 after伪类 清浮动（现在主流方法，推荐使用）
```css
.float_div:after{
	content:".";
	clear:both;
	display:block;
	height:0;
	overflow:hidden;
	visibility:hidden;
}
.float_div{
	zoom:1
} 
```
##### 自适应布局
思路：
1. 左侧浮动或者绝对定位，然后右侧margin撑开
2. 使用div包含，然后靠负margin形成bfc
3. 使用flex
##### 画三角形
```css
#item {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-top: 50px solid transparent;
	border-bottom: 50px solid blue;
	background: white;
}
```
##### link @import导入css
1. link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS。
2. link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载。
3. link无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持。
3. ink支持使用Javascript控制DOM去改变样式；而@import不支持。
##### animation
![](http://pd4ar0u4q.bkt.clouddn.com/animation.png)
##### 长宽比方案
1. 使用padding方式结合calc实现
2. 长宽一项设置百分比另一项aspect-ratio实现（需借助插件实现）
##### display相关
1. block:div等容器类型
2. inline:img span等行内类型
3. table系列：将样式变成table类型
4. flex:重点把握，非常强大
5. grid:同上
6. inline-block:可设置宽度，两者间有一点间隙
7. inherit:继承父级
#### <div id="javascript">JavaScript相关</div>
##### 1 ["1", "2", "3"].map(parseInt)
```javascript
首先, map接受两个参数, 一个回调函数 callback, 一个回调函数的this值

其中回调函数接受三个参数 currentValue, index, arrary;

而题目中, map只传入了回调函数--parseInt.

其次, parseInt 只接受两个两个参数 string, radix(基数).  
本题理解来说也就是key与 index 

所以本题即问
parseInt('1', 0);
parseInt('2', 1);
parseInt('3', 2);

parseInt(string, radix)
string	必需。要被解析的字符串。
radix 可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。
如果省略该参数或其值为 0，则数字将以 10 为基础来解析。如果它以 “0x” 或 “0X” 开头，将以 16 为基数。
```
##### 2 [[3,2,1].reduce(Math.pow), [].reduce(Math.pow)]
```javascript
arr.reduce(callback[, initialValue])
reduce接受两个参数, 一个回调, 一个初始值.
回调函数接受四个参数 previousValue, currentValue, currentIndex, array
需要注意的是 If the array is empty and no initialValue was provided, TypeError would be thrown.
所以第二个表达式会报异常. 第一个表达式等价于 Math.pow(3, 2) => 9; Math.pow(9, 1) =>9
```
##### 3
```javascript
var ary = [0,1,2];
ary[10] = 10;
ary.filter(function(x) { return x === undefined;});
我们看到在迭代这个数组的时候, 首先检查了这个索引值是不是数组的一个属性, 那么我们测试一下.

0 in ary; => true
3 in ary; => false
10 in ary; => true
也就是说 从 3 - 9 都是没有初始化的bug !, 这些索引并不存在与数组中. 在 array 的函数调用的时候是会跳过这些坑的.
```
##### 4 [typeof null, null instanceof Object]
```javascript
typeof 返回一个表示类型的字符串.
instanceof 运算符用来检测 constructor.prototype 是否存在于参数 object 的原型链上.
type         result
Undefined   "undefined"
Null        "object"
Boolean     "boolean"
Number      "number"
String      "string"
Symbol      "symbol"
Host object Implementation-dependent
Function    "function"
Object      "object"
```
##### 5 js数据类型
1.number; 

2.string;

3.boolean;

4.undefined;

5.null;

6.symbol（ES6新增，文章后面有对着新类型的解释）Symbol 生成一个全局唯一的值。

7.Object.（包括Object，Array，Function）
##### 6 promise 用法
```javascript
定义
var promise = new Promise(function(resolve, reject) {
  // ... some code
  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
使用
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
//等价于：
promise.then(function(){
  //success
}).catch(function(){
  //failure
})
```
##### 7 es6 promise ajax
```javascript
定义
const myHttpClient = url => {
  return new Promise((resolve, reject) => {
    let client = new XMLHttpRequest();
    client.open("GET", url);
    client.onreadystatechange = handler;
    client.responseType = "json";
    client.setRequestHeader("Accept", "application/json");
    client.send();
    function handler() {
      if (this.readyState !== 4) {
        return;
      }
      if (this.status === 200) {
        resolve(this.response);
      } else {
        reject(new Error(this.statusText));
      }
    }
  });
};
使用
myHttpClient('https://www.baidu.com').then(res => {
  console.log(res);
}).catch(error => {
  console.log(error);
});
```
##### 8闭包
```javascript
function foo(x) {
    var tmp = 3;
    return function (y) {
        alert(x + y + (++tmp));
    }
}
var bar = foo(2); // bar 现在是一个闭包
bar(10);
结果是16
es6通常用let const块级作用域代替，
闭包缺点，ie中会引起内存泄漏，严格来说是ie的缺点不是闭包的问题
```
##### 9 什么是立即执行函数？使用立即执行函数的目的是什么？
```javascript
常见两种方式
1.(function(){...})()
  (function(x){
	  console.log(x);
  })(12345)
2.(function(){...}())
  (function(x){
	  console.log(x);
  }(12345))
作用 不破坏污染全局的命名空间，若需要使用，将其用变量传入如
（function(window){...}(window)）
```
##### 10 async/await 语法
```javascript
作用：异步代码的新方式
promise示例
const makeRequest = () => {
  return getJSON()
    .then(data => {
      if (data.needsAnotherRequest) {
        return makeAnotherRequest(data)
          .then(moreData => {
            console.log(moreData)
            return moreData
          })
      } else {
        console.log(data)
        return data
      }
    })
}
async/await示例
const makeRequest = async () => {
  const data = await getJSON()
  if (data.needsAnotherRequest) {
    const moreData = await makeAnotherRequest(data);
    console.log(moreData)
    return moreData
  } else {
    console.log(data)
    return data    
  }
}
函数前面多了一个aync关键字。await关键字只能用在aync定义的函数内。async函数会隐式地返回一个promise，该promise的reosolve值就是函数return的值。(示例中reosolve值就是字符串"done")
```
##### 11 深浅拷贝
```javascript
let a = {
  aa: 1,
  bb: 2,
  cc: 3,
  dd: {
    ee: 5,
  },
  ff: {
    gg: 6,
  }
};
let d = JSON.parse(JSON.stringify(a));//深复制包含子对象
let c = {...a};//深拷贝单不包含子对象
let b = a;//浅拷贝
b.bb = 22;
c.cc = 33;
c.dd.ee = 55;
d.ff.gg = 66;
console.log(a);
console.log(b);
console.log(c);
console.log(d);
```
##### 12数组去重 
```javascript
思路1：定义一个新数组，并存放原数组的第一个元素，然后将元素组一一和新数组的元素对比，若不同则存放在新数组中
思路2：先将原数组排序，在与相邻的进行比较，如果不同则存入新数组。
思路3：利用对象属性存在的特性，如果没有该属性则存入新数组。
思路4（最常用）：使用es6 set
let arr= [1, 2, 3, 3, 5, 7, 2, 6, 8];
console.log([...new Set(arr)]);
```
##### 13正则实现trim()功能
```javascript
function myTrim(str) {
  let reg = /^\s+|\s+$/g;
  return str.replace(reg, "");
}
console.log(myTrim('    asdf    '));
```
##### 14 JS原型
```javascript
1.每个对象都有 __proto__ 属性，但只有函数对象才有 prototype 属性
2.个人粗略理解与python的类方法静态方法实例方法差不多
```
#####15 es6 class 
``` javascript
面向对象，java中类
```
##### 16 JS 如何实现继承
```javascript
1.使用原型继承（既继承了父类的模板，又继承了父类的原型对象。优点是继承了父类的模板，又继承了父类的原型对象，缺点就是父类实例传参，不是子类实例化传参，不符合常规语言的写法）
2.使用call的方式（继承了父类的模板，不继承了父类的原型对象。优点是方便了子类实例传参，缺点就是不继承了父类的原型对象）
```
##### 17 手写jquery插件
```javascript
(function ($) {
	$.fn.myPlugins = function (options) {
	  //参数赋值
	  options = $.extend(defaults, options);//对象合并
	  this.each(function () {
	      //执行代码逻辑
	  });
	};
})(jQuery);

$(selector).myPlugins({参数});
```
##### 18 数组合并去重排序
```javascript
let arr1 = [1, 25, 2, 26, 1234, 6, 213];
let arr2 = [2, 6, 2134, 6, 31, 623];
let c = [...new Set([...arr1, ...arr2])].sort((a, b) => {
	return a - b;
});
```
##### 19 call apply
作用：在函数调用时改变函数的执行上下文也就是this的值
区别：call采用不定长的参数列表，而apply使用一个参数数组。
性能优化图
![性能优化](http://pd4ar0u4q.bkt.clouddn.com/%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96.jpg)
##### 20 for 中setTimeOut
要为循环题创建不同的循环副本
##### 21 sort函数
V8 引擎 sort 函数只给出了两种排序 InsertionSort 和 QuickSort，数量小于10的数组使用 插入，比10大的数组则使用 快排。
##### 22 navigator
![Navigator](http://pd4ar0u4q.bkt.clouddn.com/Navigator.png)
##### 23 jquery绑定方式
1. click后者覆盖
2. bind后者覆盖
3. on(jquery>=1.7)
4. live
5. delegate
##### 24 事件流向
1. 冒泡：子节点一层层冒泡到根节点
2. 捕获顺序与冒泡相反
3. addEventListener最后个参数true代表捕获反之代表冒泡
4. 阻止冒泡不停止父节点捕获
##### 25原生操作class
```javascript
//判断有无
function hasClass(ele, cls) {
	return ele.className.match(new RegExp("(\\s|^)" + cls + "(\\s|$)"));
}

//添加
function addClass(ele, cls) {
	if (!this.hasClass(ele, cls)) ele.className += " " + cls;
}

//删除
function removeClass(ele, cls) {
	if (hasClass(ele, cls)) {
		let reg = new RegExp("(\\s|^)" + cls + "(\\s|$)");
		ele.className = ele.className.replace(reg, " ");
	}
}

html5中加入classList 
一系列操作
兼容至IE10
```
#### <div id="dom">DOM相关</div>
##### dom事件模型
DOM之事件模型分脚本模型、内联模型(同类一个，后者覆盖)、动态绑定(同类多个)
demo
```javascript
<body>
<!--行内绑定：脚本模型-->
<button onclick="javascrpt:alert('Hello')">Hello1</button>
<!--内联模型-->
<button onclick="showHello()">Hello2</button>
<!--动态绑定-->
<button id="btn3">Hello3</button>
</body>
<script>
/*DOM0：同一个元素，同类事件只能添加一个，如果添加多个，
* 后面添加的会覆盖之前添加的*/
function shoeHello() {
alert("Hello");
}
var btn3 = document.getElementById("btn3");
btn3.onclick = function () {
alert("Hello");
}
/*DOM2:可以给同一个元素添加多个同类事件*/
btn3.addEventListener("click",function () {
alert("hello1");
});
btn3.addEventListener("click",function () {
alert("hello2");
})
if (btn3.attachEvent){
/*IE*/
btn3.attachEvent("onclick",function () {
alert("IE Hello1");
})
}else {
/*W3C*/
btn3.addEventListener("click",function () {
alert("W3C Hello");
})
}
</script>
```
冒泡解释：当点击一个元素触发事件时. 事件会先从元素的最外层父元素一层一层进入到触发的元素, 然后在从触发元素一层一层返回到最外层父元素, 从最外层一层一层进入的阶段叫事件捕获阶段, 从最里层一层一层往外的阶段叫事件冒泡,

##### 移动端触摸事件
①touchstart：当手指触碰到屏幕的时候触发 
②touchmove：当手指在屏幕上滑动的时候触发 
③touchend：当手指离开屏幕的时候时候触发 
④touchcancel事件：当系统停止跟踪触摸的时候触发(这个事件很少会用，一般不做深入研究)。 电话接入或者弹出信息等其他事件切入
event： 
1. touches：表示当前跟踪的触摸操作的touch对象的数组。 
2. targetTouches：特定于事件目标的Touch对象的数组。 
3. changeTouches：表示自上次触摸以来发生了什么改变的Touch对象的数组。 

每个touch对象包含的属性 
1. clientX：触摸目标在视口中的x坐标。 
2. clientY：触摸目标在视口中的y坐标。 
3. identifier：标识触摸的唯一ID。 
4. pageX：触摸目标在页面中的x坐标。 
5. pageY：触摸目标在页面中的y坐标。 
6. screenX：触摸目标在屏幕中的x坐标。 
7. screenY：触摸目标在屏幕中的y坐标。 
8. target：触目的DOM节点目标。 

##### 事件委托
参考定义：事件委托就是利用事件冒泡，只指定一个事件处理程序，就可以管理某一类型的所有事件
好处：给重复的节点添加相同操作，减少dom交互，提高性能
实现思路：给父组件添加事件，通过事件冒泡，排查元素是否为指定元素，并进行系列操作

#### <div id="http">HTTP相关</div>
##### 常见状态码
<b>2开头 （请求成功）表示成功处理了请求的状态代码。</b>

200   （成功）  服务器已成功处理了请求。 通常，这表示服务器提供了请求的网页。 
201   （已创建）  请求成功并且服务器创建了新的资源。 
202   （已接受）  服务器已接受请求，但尚未处理。 
203   （非授权信息）  服务器已成功处理了请求，但返回的信息可能来自另一来源。 
204   （无内容）  服务器成功处理了请求，但没有返回任何内容。 
205   （重置内容） 服务器成功处理了请求，但没有返回任何内容。
206   （部分内容）  服务器成功处理了部分 GET 请求。

<b>3开头 （请求被重定向）表示要完成请求，需要进一步操作。 通常，这些状态代码用来重定向。</b>

300   （多种选择）  针对请求，服务器可执行多种操作。 服务器可根据请求者 (user agent) 选择一项操作，或提供操作列表供请求者选择。 
301   （永久移动）  请求的网页已永久移动到新位置。 服务器返回此响应（对 GET 或 HEAD 请求的响应）时，会自动将请求者转到新位置。
302   （临时移动）  服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。
303   （查看其他位置） 请求者应当对不同的位置使用单独的 GET 请求来检索响应时，服务器返回此代码。
304   （未修改） 自从上次请求后，请求的网页未修改过。 服务器返回此响应时，不会返回网页内容。 
305   （使用代理） 请求者只能使用代理访问请求的网页。 如果服务器返回此响应，还表示请求者应使用代理。 
307   （临时重定向）  服务器目前从不同位置的网页响应请求，但请求者应继续使用原有位置来进行以后的请求。

<b>4开头 （请求错误）这些状态代码表示请求可能出错，妨碍了服务器的处理。</b>

400   （错误请求） 服务器不理解请求的语法。 
401   （未授权） 请求要求身份验证。 对于需要登录的网页，服务器可能返回此响应。 
403   （禁止） 服务器拒绝请求。
404   （未找到） 服务器找不到请求的网页。
405   （方法禁用） 禁用请求中指定的方法。 
406   （不接受） 无法使用请求的内容特性响应请求的网页。 
407   （需要代理授权） 此状态代码与 401（未授权）类似，但指定请求者应当授权使用代理。
408   （请求超时）  服务器等候请求时发生超时。 
409   （冲突）  服务器在完成请求时发生冲突。 服务器必须在响应中包含有关冲突的信息。 
410   （已删除）  如果请求的资源已永久删除，服务器就会返回此响应。 
411   （需要有效长度） 服务器不接受不含有效内容长度标头字段的请求。 
412   （未满足前提条件） 服务器未满足请求者在请求中设置的其中一个前提条件。 
413   （请求实体过大） 服务器无法处理请求，因为请求实体过大，超出服务器的处理能力。 
414   （请求的 URI 过长） 请求的 URI（通常为网址）过长，服务器无法处理。 
415   （不支持的媒体类型） 请求的格式不受请求页面的支持。 
416   （请求范围不符合要求） 如果页面无法提供请求的范围，则服务器会返回此状态代码。 
417   （未满足期望值） 服务器未满足"期望"请求标头字段的要求。

<b>5开头（服务器错误）这些状态代码表示服务器在尝试处理请求时发生内部错误。 这些错误可能是服务器本身的错误，而不是请求出错。</b>

500   （服务器内部错误）  服务器遇到错误，无法完成请求。 
501   （尚未实施） 服务器不具备完成请求的功能。 例如，服务器无法识别请求方法时可能会返回此代码。 
502   （错误网关） 服务器作为网关或代理，从上游服务器收到无效响应。 
503   （服务不可用） 服务器目前无法使用（由于超载或停机维护）。 通常，这只是暂时状态。 
504   （网关超时）  服务器作为网关或代理，但是没有及时从上游服务器收到请求。 
505   （HTTP 版本不受支持） 服务器不支持请求中所用的 HTTP 协议版本。

##### 缓存
1. Expires在http1.0中使用，与服务器时间有误差，在1.1中由Cache-control替代
<meta http-equiv="Cache-Control" content="max-age=7200" />
<meta http-equiv="Expires" content="Mon, 20 Jul 2009 23:00:00 GMT" />
2. cdn

#####  Cache-Control 和 Etag 的区别
如下图
![区别图](http://pd4ar0u4q.bkt.clouddn.com/%E5%8C%BA%E5%88%AB%E5%9B%BE.png)

##### Cookie sessionStorage  localStorage
共同点：都是保存在浏览器端，且同源的。
区别：cookie数据始终在同源的http请求中携带，即cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。cookie数据不能超过4k(适合保存小数据)。
sessionStorage和localStorage容量较大，数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效。localStorage：始终有效，窗口或浏览器关闭也一直保存，需手动清楚；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。作用域不同。
sessionStorage不在不同的浏览器窗口中共享；localStorage 在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的。

应用场景：localStorage：常用于长期登录（+判断用户是否已登录），适合长期保存在本地的数据。sessionStorage ：敏感账号一次性登录； cookies与服务器交互。

##### GET POST区别

![get_post](http://pd4ar0u4q.bkt.clouddn.com/get_post.png)
##### 请求行，请求头，请求体详解
![如图](http://pd4ar0u4q.bkt.clouddn.com/http%E8%AF%B7%E6%B1%82%E4%B8%80%E4%BD%93.jpg)
1,2,3请求行，4请求体，5请求体
##### 跨域、JSONP 、CORS、postMessage
跨域概念解释：当前发起请求的域与该请求指向的资源所在的域不一样。这里的域指的是这样的一个概念：我们认为若协议 + 域名 + 端口号均相同，那么就是同域。
如下表
![图](http://pd4ar0u4q.bkt.clouddn.com/%E8%B7%A8%E5%9F%9F%E6%83%85%E5%86%B5%E6%A0%87%E8%AF%86.png)

jsoup实现
```javascript
原生
<script>
    var script = document.createElement('script');
    script.type = 'text/javascript';
 
    // 传参并指定回调执行函数为onBack
    script.src = 'http://www.domain2.com:8080/login?user=admin&callback=onBack';
    document.head.appendChild(script);
 
    // 回调执行函数
    function onBack(res) {
        alert(JSON.stringify(res));
    }
 </script>
 
jquery
$.ajax({
    url: 'http://www.domain2.com:8080/login',
    type: 'get',
    dataType: 'jsonp',  // 请求方式为jsonp
    jsonpCallback: "onBack",    // 自定义回调函数名
    data: {}
});

vue
this.$http.jsonp('http://www.domain2.com:8080/login', {
    params: {},
    jsonp: 'onBack'
}).then((res) => {
    console.log(res); 
})

配合的后端node实现,其他服务器语言也可以
const querystring = require('querystring');
const http = require('http');
const server = http.createServer();
server.on('request', function(req, res) {
    var params = qs.parse(req.url.split('?')[1]);
    var fn = params.callback;
 
    // jsonp返回设置
    res.writeHead(200, { 'Content-Type': 'text/javascript' });
    res.write(fn + '(' + JSON.stringify(params) + ')');
 
    res.end();
});
server.listen('8080');

jsoup缺点只能实现get请求
```

CORS：跨源资源共享 Cross-Origin Resource Sharing(CORS)，通常服务器设置，若带cookie请求，则前后端都需要设置
后端常见设置
response.setHeader("Access-Control-Allow-Origin", "http://www.domain1.com");  // 若有端口需写全（协议+域名+端口），允许那些外源请求
response.setHeader("Access-Control-Allow-Credentials", "true"); //是否需要验证

前端示例

```javascript
原生

var xhr = new XMLHttpRequest(); // IE8/9需用window.XDomainRequest兼容
// 前端设置是否带cookie
xhr.withCredentials = true;
xhr.open('post', 'http://www.domain2.com:8080/login', true);
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
xhr.send('user=admin');
 
xhr.onreadystatechange = function() {
    if (xhr.readyState == 4 && xhr.status == 200) {
        alert(xhr.responseText);
    }

jquery
$.ajax({
    ...
   xhrFields: {
       withCredentials: true    // 前端设置是否带cookie
   },
   crossDomain: true,   // 会让请求头中包含跨域的额外信息，但不会含cookie
    ...
});
```

```javascript
postMessage(data,origin)方法接受两个参数
demo

a.html
<iframe id="iframe" src="http://www.domain2.com/b.html" style="display:none;"></iframe>
<script>       
    var iframe = document.getElementById('iframe');
    iframe.onload = function() {
        var data = {
            name: 'aym'
        };
        // 向domain2传送跨域数据
        iframe.contentWindow.postMessage(JSON.stringify(data), 'http://www.domain2.com');
    };
 
    // 接受domain2返回数据
    window.addEventListener('message', function(e) {
        alert('data from domain2 ---> ' + e.data);
    }, false);
</script>

b.html  与a.html不同源

<script>
    // 接收domain1的数据
    window.addEventListener('message', function(e) {
        alert('data from domain1 ---> ' + e.data);
 
        var data = JSON.parse(e.data);
        if (data) {
            data.number = 16;
 
            // 处理后再发回domain1
            window.parent.postMessage(JSON.stringify(data), 'http://www.domain1.com');
        }
    }, false);
</script>
```
##### osi模型
七层结构：物理层、数据链路层、网络层、传输层、会话层、表示层、应用层
tcp ucp属于传输层；http属于应用层
##### http2.0 http1
1. HTTP2.0的基本单位为二进制帧
2. HTTP2.0中帧具有优先级
3. HTTP2.0的多路复用（ 1次连接）
4. HTTP2.0压缩消息头
5. HTTP2.0服务端推送
6. HTTP2.0只适用于HTTPS的场景
#### <div id="vue">Vue相关</div>

##### 生命周期顺序
![生命周期](http://pd4ar0u4q.bkt.clouddn.com/vue%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png)

##### 组件通信
1.父传子用props,父用子用ref 子调父用$emit,无关系用Bus
##### Vuex
组件通信库，可以避免子组件无法改变props的弊端等
mutations 同步操作， 用于改变状态 官方不推荐异步
action 执行多个mutaions，官方推荐异步操作
mapState、mapGetters、mapActions使用示例
``` javascript
<template>
  <el-dialog :visible.sync="show"></el-dialog>
</template>

<script>
import {mapState} from 'vuex';
export default {
  computed:{

    //这里的三点叫做 : 扩展运算符
    ...mapState({
      show:state=>state.dialog.show
    }),
  }
}
</script>

后两者类似
```
##### VueRouter
```javascript
定义
var routes = [
    {
        path:"/one",

        component:导入的组件1
    },
    {
        path:"/two",
        component:导入的组件2
    },
];
// 定义路由组件
var router = new VueRouter({
    routes
});
// 定义路由
new Vue({
    el:"#box",
    router
});
 访问设定的路由后 会将<router-view></router-view>替换成相应的模版
 html访问方式 <router-link to="/one">One</router-link>(类似a标签)
 js访问方式 this.$router.push('/one'); 
 replace方式 替换当前页面
 携带的参数 可以通过this.$route.query.xxxx来获取
``` 
##### Vue双向绑定
原理：利用了 Object.defineProperty() 这个方法重新定义了对象获取属性值(get)和设置属性值(set)的操作来实现的。
缺点：双向数据流是自动管理状态的, 但是在实际应用中会有很多不得不手动处理状态变化的逻辑, 使得程序复杂度上升, 难以调试。
##### computed  watch methods
用法：
区别：
1. 前两者自动追踪数据，执行相关函数，最后一个手动调用；
2. computed是计算属性，用法与data一致
3. watch像事件监听，对象发生变化时，执行相关操作
4. methods与js中执行方法类似
5. computed通常只有get属性
6. 数据变化的同时进行异步操作或者是比较大的开销，那么watch为最佳选择
7. watch的对象必须事先声明
#### <div id="sort">算法相关</div>
##### 各种排序实现
相关数据
![表格](http://pd4ar0u4q.bkt.clouddn.com/%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95%E7%AD%89%E7%AD%89.png)
```javascript
// 冒泡排序: 比较两个相邻的项，如果第一个大于第二个则交换他们的位置,元素项向上移动至正确的顺序，就好像气泡往上冒一样
冒泡demo:
function bubbleSort(arr) {
    let len = arr.length;
    for (let i = 0; i < len; i++) {
        for (let j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {        //相邻元素两两对比
                [arr[j + 1], arr[j]] = [arr[j], arr[j + 1]];
            }
        }
    }
    return arr;
}
// 1) 首先，在数组中选择一个中间项作为主元
// 2) 创建两个指针，左边的指向数组第一个项，右边的指向最后一个项，移动左指针，直到找到一个比主元大的项，接着，移动右边的指针，直到找到一个比主元小的项，然后交换它们。重复这个过程，直到
// 左侧的指针超过了右侧的指针。这个使比主元小的都在左侧，比主元大的都在右侧。这一步叫划分操作
// 3) 接着，算法对划分后的小数组（较主元小的值组成的的小数组， 以及较主元大的值组成的小数组）重复之前的两个步骤，直到排序完成
快排demo:
function quickSort(arr, left, right) {
    let len = arr.length;
    let partitionIndex;
    left = typeof left !== 'number' ? 0 : left;
    right = typeof right !== 'number' ? len - 1 : right;
    if (left < right) {
        partitionIndex = partition(arr, left, right);
        quickSort(arr, left, partitionIndex - 1);
        quickSort(arr, partitionIndex + 1, right);
    }
    return arr;
}

function partition(arr, left, right) {     //分区操作
    let pivot = left;                      //设定基准值（pivot）
    let index = pivot + 1;
    for (let i = index; i <= right; i++) {
        if (arr[i] < arr[pivot]) {
            [arr[i], arr[index]] = [arr[index], arr[i]];
            index++;
        }
    }
    [arr[pivot], arr[index - 1]] = [arr[index - 1], arr[pivot]];
    return index - 1;
}
// 选择排序：大概思路是找到最小的放在第一位，找到第二小的放在第二位，以此类推 算法复杂度O(n^2)
选择demo:
function selectionSort(arr) {
	let len = arr.length;
	let minIndex;
	for (let i = 0; i < len - 1; i++) {
		minIndex = i;
		for (let j = i + 1; j < len; j++) {
			if (arr[j] < arr[minIndex]) {     //寻找最小的数
			    minIndex = j;                 //将最小数的索引保存
		    }
		}
		[arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
	}
return arr;
}
// 插入排序：每次排一个数组项，假设数组的第一项已经排序，接着，把第二项与第一项进行对比，第二项是该插入到第一项之前还是之后，第三项是该插入到第一项之前还是第一项之后还是第三项
插入demo:
function insertionSort(arr) {
	let len = arr.length;
	let preIndex, current;
	for (let i = 1; i < len; i++) {
	    preIndex = i - 1;
	    current = arr[i];
	    while (preIndex >= 0 && arr[preIndex] > current) {
		    arr[preIndex + 1] = arr[preIndex];
		    preIndex--;
	    }
	    arr[preIndex + 1] = current;
	}
	return arr;
}
// 归并排序：Mozilla Firefox 使用归并排序作为Array.prototype.sort的实现，而chrome使用快速排序的一个变体实现的,前面三种算法性能不好，但归并排序性能不错 算法复杂度O(nlog^n)
// 归并排序是一种分治算法。本质上就是把一个原始数组切分成较小的数组，直到每个小数组只有一个位置，接着把小数组归并成较大的数组，在归并过程中也会完成排序，直到最后只有一个排序完毕的大数组
归并demo:
function mergeSort(arr) {  //采用自上而下的递归方法
    let len = arr.length;
    if(len < 2) {
        return arr;
    }
    let middle = Math.floor(len / 2),
    left = arr.slice(0, middle),
    right = arr.slice(middle);
    return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right){
    let result = [];
    while (left.length && right.length) {
        if (left[0] <= right[0]) {
            result.push(left.shift());
        } else {
            result.push(right.shift());
        }
    }
    result.push(...left);
    result.push(...right);
    return result;
}
//堆排序：堆排序把数组当中二叉树来排序而得名。
// 1）索引0是树的根节点；2）除根节点为，任意节点N的父节点是N/2；3）节点L的左子节点是2*L；4）节点R的右子节点为2*R + 1
// 本质上就是先构建二叉树，然后把根节点与最后一个进行交换，然后对剩下对元素进行二叉树构建，进行交换，直到剩下最后一个
堆demo:
var len;    //因为声明的多个函数都需要数据长度，所以把len设置成为全局变量

function buildMaxHeap(arr) {   //建立大顶堆
    len = arr.length;
    for (let i = Math.floor(len / 2); i >= 0; i--) {
        heapify(arr, i);
    }
}

function heapify(arr, i) {     //堆调整
    let left = 2 * i + 1;
    let right = 2 * i + 2;
    let largest = i;
    if (left < len && arr[left] > arr[largest]) {
        largest = left;
    }
    if (right < len && arr[right] > arr[largest]) {
        largest = right;
    }
    if (largest !== i) {
        [arr[i], arr[largest]] = [arr[largest], arr[i]];
        heapify(arr, largest);
    }
}

function heapSort(arr) {
    buildMaxHeap(arr);
    for (let i = arr.length - 1; i > 0; i--) {
        [arr[0],arr[i]]=[arr[i],arr[0]];
        len--;
        heapify(arr, 0);
    }
    return arr;
}
```
##### 二分查找
思路
（1）首先，从有序数组的中间的元素开始搜索，如果该元素正好是目标元素（即要查找的元素），则搜索过程结束，否则进行下一步。
（2）如果目标元素大于或者小于中间元素，则在数组大于或小于中间元素的那一半区域查找，然后重复第一步的操作。
（3）如果某一步数组为空，则表示找不到目标元素。
```javascript
// 非递归算法
function binary_search(arr, key) {
    let low = 0;
    let high = arr.length - 1;
    while(low <= high){
        let mid = parseInt((high + low) / 2);
        if(key === arr[mid]){
            return  mid;
        }else if(key > arr[mid]){
            low = mid + 1;
        }else if(key < arr[mid]){
            high = mid -1;
        }else{
            return -1;
        }
    }
}
      

// 递归算法
function binary_search(arr,low, high, key) {
    if (low > high){
        return -1;
    }
    let mid = parseInt((high + low) / 2);
    if(arr[mid] === key){
        return mid;
    }else if (arr[mid] > key){
        high = mid - 1;
        return binary_search(arr, low, high, key);
    }else if (arr[mid] < key){
        low = mid + 1;
        return binary_search(arr, low, high, key);
    }
};
```
##### 二叉树相关
``` javascript
创建
function Node(data,left,right){
	this.data = data;//数值
	this.left = left;//左节点
	this.right = right;//右节点
};
插入二叉树
function insert(node,data){
	//创建一个新的节点
	let newNode  = new Node(data,null,null);
	//判断是否存在根节点，没有将新节点存入
	if(node == null){
		node = newNode;
	}else{
		//获取根节点
		let current = node;
		let parent;
		while(true){
			//将当前节点保存为父节点
			parent = current;
			//将小的数据放在左节点
			if(data < current.data){
				//获取当前节点的左节点
				//判断当前节点下的左节点是否有数据
				current = current.left;
				if(current == null){
					//如果没有数据将新节点存入当前节点下的左节点
					parent.left = newNode;
					break;
				}
			}else{
				current = current.right;
				if(current == null){
					parent.right = newNode;
					break;
				}
			}
		}    
	}
}
翻转二叉树
function invertTree(node) {
	if (node !== null) {
		node.left, node.right = node.left, node.right;
		invertTree(node.left);
		invertTree(node.right);
	}
	return node;
}
```
``` javascript
查找链表中倒数第k个结点
2个思路
1：先遍历出长度，然后查找长度-k+1的值
2：2个指针，一个指针先走k-1，然后两个一起走到底部，后者就是结果
```

#### <div id="web">网络安全相关</div>
##### XSS CSRF
XSS(跨站脚本攻击)，恶意的注入html代码，其他用户访问时，会被执行
特点：能注入恶意的HTML/JavaScript代码到用户浏览的网页上，从而达到Cookie资料窃取、会话劫持、钓鱼欺骗等攻击
防御手段：
+ 浏览器禁止页面的JS访问带有HttpOnly属性的Cookie
+ 两端进行输入格式检查
+ 通过编码转义的方式进行输出检查
CSRF(攻击跨站请求伪造)
特点：重要操作的所有参数都是可以被攻击者猜测到的。攻击者预测出URL的所有参数与参数值，才能成功地构造一个伪造的请求。
防御手段：
+ token验证机制，比如请求数据字段中添加一个token，响应请求时校验其有效性
+ 用户操作限制，比如验证码（繁琐，用户体验差）
+ 请求来源限制，比如限制HTTP Referer才能完成操作（防御效果相比较差）
实践中常用第一种
#### <div id="webpack"> webpack相关</div>
#####打包体积
优化思路
1. 提取第三方库或通过引用外部文件的方式引入第三方库
2. 代码压缩插件UglifyJsPlugin
3. 服务器启用gzip压缩
4. 按需加载资源文件 require.ensure
5. 优化devtool中的source-map
6. 剥离css文件，单独打包
7. 去除不必要插件，通常就是开发环境与生产环境用同一套配置文件导致
#####打包效率
1. 开发环境采用增量构建，启用热更新
2. 开发环境不做无意义的工作如提取css计算文件hash等
3. 配置devtool
4. 选择合适的loader
5. 个别loader开启cache 如babel-loader
6. 第三方库采用引入方式
7. 提取公共代码
8. 优化构建时的搜索路径 指明需要构建目录及不需要构建目录
9. 模块化引入需要的部分
##### Loader
编写一个loader
```javascript
loader就是一个node模块，它输出了一个函数。当某种资源需要用这个loader转换时，这个函数会被调用。并且，这个函数可以通过提供给它的this上下文访问Loader API。
reverse-txt-loader
定义
module.exports = function(src) {
  //src是原文件内容（abcde），下面对内容进行处理，这里是反转
  var result = src.split('').reverse().join(''); 
  //返回JavaScript源码，必须是String或者Buffer
  return `module.exports = '${result}'`;
}
使用
{
	test: /\.txt$/,
	use: [
		{
			'./path/reverse-txt-loader'
		}
	]
},
```
##### plugins
使用范围更广，通常只需要require()然后添加到plugins数组中，且需要new一个
#### <div id="other">其他</div>
##### URL到界面显示发生了什么
1. DNS解析
先本地缓存找，在一层层找
将常见的地址解析成唯一对应的ip地址基本顺序为：本地域名服务器->根域名服务器->com顶级域名服务器依次类推下去,找到后记录并缓存下来如www.google.com为<br><b>. -> .com -> google.com. -> www.google.com.</b>
2. TCP连接
三次握手，只要没收到确认消息就要重新发
	1. 主机向服务器发送一个建立连接的请求（您好，我想认识您）；
	2. 服务器接到请求后发送同意连接的信号（好的，很高兴认识您）；
	3. 主机接到同意连接的信号后，再次向服务器发送了确认信号（我也很高兴认识您），自此，主机与服务器两者建立了连接。
3. 发送HTTP请求
浏览器会分析这个url，并设置好请求报文发出。请求报文中包括请求行、请求头、空行、请求主体。https默认请求端口443， http默认80。
常见的http请求如下
``` htmlbars
POST / HTTP1.1
Host:www.wrox.com
User-Agent:Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1; .NET CLR 2.0.50727; .NET CLR 3.0.04506.648; .NET CLR 3.5.21022)
Content-Type:application/x-www-form-urlencoded
Content-Length:40
Connection: Keep-Alive

name=Professional%20Ajax&publisher=Wiley
第一部分：请求行，第一行说明是post请求，以及http1.1版本。
第二部分：请求头部，第二行至第六行。
第三部分：空行，第七行的空行。
第四部分：请求数据，第八行。
4. 服务器处理请求并返回HTTP报文
后端处理返回http报文如下
```

``` htmlbars
HTTP/1.1 200 OK
Date: Fri, 22 May 2009 06:07:21 GMT
Content-Type: text/html; charset=UTF-8

<html>
      <head></head>
      <body>
            <!--body goes here-->
      </body>
</html>
第一行为状态行，（HTTP/1.1）表明HTTP版本为1.1版本，状态码为200，状态消息为（ok）
第二行和第三行为消息报头，
Date:生成响应的日期和时间；Content-Type:指定了MIME类型的HTML(text/html),编码类型是UTF-8
第三部分：空行，消息报头后面的空行是必须的
第四部分：响应正文，服务器返回给客户端的文本信息。
空行后面的html部分为响应正文。
```
5. 浏览器解析渲染页面
+ 通过HTML解析器解析HTML文档，构建一个DOM Tree，同时通过CSS解析器解析HTML中存在的CSS，构建Style Rules，两者结合形成一个Attachment。
+ 通过Attachment构造出一个呈现树（Render Tree）
+ Render Tree构建完毕，进入到布局阶段（layout/reflow），将会为每个阶段分配一个应出现在屏幕上的确切坐标。
+ 最后将全部的节点遍历绘制出来后，一个页面就展现出来了。
遇到script会停下来执行，所以通常把script放在底部
6. 连接结束

##### 组件封装
目的：为了重用，提高开发效率和代码质量
注意：低耦合，单一职责，可复用性，可维护性
常用操作：
1. 分析布局
2. 初步开发
3. 化繁为简
4. 组件抽象

##### JS异步加载
1. 动态生成script标签
2. 添加h5的async defer属性，前者乱序不适合依赖性加载
3. async 是“下载完就执行”， defer 是“渲染完再执行”

##### css与js动画差异
1. css性能好
2. css代码逻辑相对简单
3. js动画控制好
4. js兼容性好
5. js可实现的动画多
6. js可以添加事件

#####  负载均衡
多台服务器共同协作，不让其中某一台或几台超额工作，发挥服务器的最大作用
1. http重定向负载均衡：调度者根据策略选择服务器以302响应请求，缺点只有第一次有效果，后续操作维持在该服务器
2. dns负载均衡：解析域名时，访问多个ip服务器中的一个（可监控性较弱）
3. 反向代理负载均衡：访问统一的服务器，由服务器进行调度访问实际的某个服务器，对统一的服务器要求大，性能受到 服务器群的数量

##### CDN
内容分发网络，基本思路是尽可能避开互联网上有可能影响数据传输速度和稳定性的瓶颈和环节，使内容传输的更快、更稳定。

#####  内存泄漏
定义：程序中己动态分配的堆内存由于某种原因程序未释放或无法释放引发的各种问题
js中可能出现的内存泄漏情况
结果：变慢，崩溃，延迟大等
原因：
1. 全局变量
2. dom清空时，还存在引用
3. ie中使用闭包
4. 定时器未清理
5. 子元素存在引起的内存泄露

避免策略：
1. 减少不必要的全局变量，或者生命周期较长的对象，及时对无用的数据进行垃圾回收；
2. 注意程序逻辑，避免“死循环”之类的 ；
3. 避免创建过多的对象  原则：不用了的东西要及时归还。 
4. 减少层级过多的引用
#####  babel原理
ES6、7代码输入 -> babylon进行解析 -> 得到AST（抽象语法树）-> plugin用babel-traverse对AST树进行遍历转译 ->得到新的AST树->用babel-generator通过AST树生成ES5代码、

##### promise
特性：Promise 对象的错误具有冒泡性质，会一直向后传递，直到被捕获为止，也即是说，错误总会被下一个catch语句捕获

##### js自定义事件
三要素：
document.createEvent()
event.initEvent()
element.dispatchEvent()
``` javascript
demo:
(en:自定义事件名称，fn:事件处理函数，addEvent:为DOM元素添加自定义事件，triggerEvent:触发自定义事件)
window.onload = function(){
    var demo = document.getElementById("demo");
    demo.addEvent("test",function(){console.log("handler1")});
    demo.addEvent("test",function(){console.log("handler2")});
    demo.onclick = function(){
        this.triggerEvent("test");
    }
}
Element.prototype.addEvent = function(en,fn){
    this.pools = this.pools || {};
    if(en in this.pools){
        this.pools[en].push(fn);
    }else{
        this.pools[en] = [];
        this.pools[en].push(fn);
    }
}
Element.prototype.triggerEvent  = function(en){
    if(en in this.pools){
        var fns = this.pools[en];
        for(var i=0,il=fns.length;i<il;i++){
            fns[i]();
        }
    }else{
        return;
    }
}
```

#####  es6模块 commonjs  amd cmd
1.  CommonJS 的规范中，每个 JavaScript 文件就是一个独立的模块上下文（module context），在这个上下文中默认创建的属性都是私有的。也就是说，在一个文件定义的变量（还包括函数和类），都是私有的，对其他文件是不可见的。
2.  CommonJS是同步加载模块,在浏览器中会出现堵塞情况，所以不适用
3.  AMD 异步，需要定义回调define方式
4.  es6 一个模块就是一个独立的文件，该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用export关键字输出该变量
5.  es6还可以导出类、方法，自动适用严格模式

##### 前后端路由差别

1.后端每次路由请求都是重新访问服务器
2.前端路由实际上只是JS根据URL来操作DOM元素，根据每个页面需要的去服务端请求数据，返回数据后和模板进行组合。
