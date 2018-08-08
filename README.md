### 前端问题记录
#### Html相关
##### 1 html语义化
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
#### CSS相关
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
#### JavaScript相关
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
es6通常用let const块级作用域代替
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
3.
```

性能优化图
![性能优化](http://pd4ar0u4q.bkt.clouddn.com/%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96.jpg)


#### DOM相关

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

#### HTTP相关
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


#### Vue相关

##### 生命周期顺序
![生命周期](http://pd4ar0u4q.bkt.clouddn.com/vue%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png)

##### 组件通信
1.父传子用props,父用子用ref 子调父用$emit,无关系用Bus

##### 

##### Vuex

##### VueRouter

##### Vue双向绑定
原理：
实现：
缺点：

##### Computed 
用处：
用法：
与methods区别：
