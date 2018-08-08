###前端问题记录
#### html
#####1 html语义化
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
![Alt text](./h5新元素.png)

#####2 meta viewport相关
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
#####3 canvas 相关
```javascript
使用前需要获得上下文环境，暂不支持3d
常用api:
	1.fillRect(x,y,width,height)实心矩形
	2.strokeRect(x,y,width,height)空心矩形
	3.fillText("Hello world",200,200);实心文字
    4.strokeText("Hello world",200,300)空心文字
各种东西！！！
```
####CSS
#####1.盒模型

####javascript
#####1 ["1", "2", "3"].map(parseInt)
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
#####2 [[3,2,1].reduce(Math.pow), [].reduce(Math.pow)]
```javascript
arr.reduce(callback[, initialValue])
reduce接受两个参数, 一个回调, 一个初始值.
回调函数接受四个参数 previousValue, currentValue, currentIndex, array
需要注意的是 If the array is empty and no initialValue was provided, TypeError would be thrown.
所以第二个表达式会报异常. 第一个表达式等价于 Math.pow(3, 2) => 9; Math.pow(9, 1) =>9
```
#####3
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
#####4 [typeof null, null instanceof Object]
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
#####6 promise 用法
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
#####7 es6 promise ajax
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
#####8闭包
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
#####9 什么是立即执行函数？使用立即执行函数的目的是什么？
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
#####13正则实现trim()功能
```javascript
function myTrim(str) {
  let reg = /^\s+|\s+$/g;
  return str.replace(reg, "");
}
console.log(myTrim('    asdf    '));
```
#####14 JS原型
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
![Alt text](./性能优化.jpg)
