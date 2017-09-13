> 本文旨在加深对前端知识点的理解，资料来源于网络。如有错误，欢迎 [指正](https://github.com/qingtan99/Front_interview/issues)

#### position的值， relative和absolute分别是相对于谁进行定位的？

+  absolute :生成绝对定位的元素， 相对于最近一级的 定位不是 static 的父元素来进行定位。
+  fixed （老IE不支持）生成绝对定位的元素，通常相对于浏览器窗口或 frame 进行定位。
+  relative 生成相对定位的元素，相对于其在普通流中的位置进行定位。
+  static 默认值。没有定位，元素出现在正常的流中
+  sticky 生成粘性定位的元素，容器的位置根据正常文档流计算得出

#### 跨域问题

原因：
```
  由于同源策略的限制，XmlHttpRequest只允许请求当前源（域名、协议、端口）的资源
```

解决原理：
```
  动态插入script标签，通过script标签引入一个js文件，这个js文件载入成功后会执行我们在url参数中指定的函数，并且会把我们需要的json数据作为参数传入。
```

优点：
```
  兼容性好，简单易用，支持浏览器与服务器双向通信。缺点是只支持GET请求。
```

#### 对作用域链的理解
作用域链的作用是保证执行环境里有权访问的变量和函数是有序的，作用域链的变量只能向上访问，变量访问到window对象即被终止，作用域链向下访问变量是不被允许的。

#### 创建ajax过程
```
  (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象.
  (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.
  (3)设置响应HTTP请求状态变化的函数.
  (4)发送HTTP请求.
  (5)获取异步调用返回的数据.
  (6)使用JavaScript和DOM实现局部刷新.
```

#### ajax的缺点

```
  1、ajax不支持浏览器back按钮。
  2、安全问题 AJAX暴露了与服务器交互的细节。
  3、对搜索引擎的支持比较弱。
  4、破坏了程序的异常机制。
  5、不容易调试。
```

#### 渐进增强和优雅降级

渐进增强 ：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。

优雅降级 ：一开始就构建完整的功能，然后再针对低版本浏览器进行兼容。

#### Web Worker 和webSocket
worker主线程: 
```
  1.通过 worker = new Worker( url ) 加载一个JS文件来创建一个worker，同时返回一个worker实例。

  2.通过worker.postMessage( data ) 方法来向worker发送数据。

  3.绑定worker.onmessage方法来接收worker发送过来的数据。

  4.可以使用 worker.terminate() 来终止一个worker的执行。
```

WebSocket是Web应用程序的传输协议，它提供了双向的，按序到达的数据流。他是一个HTML5协议，WebSocket的连接是持久的，他通过在客户端和服务器之间保持双工连接，服务器的更新可以被及时推送给客户端，而不需要客户端以一定时间间隔去轮询。

#### 对前端模块化的认识

```
  AMD 是 RequireJS 在推广过程中对模块定义的规范化产出。

  CMD 是 SeaJS 在推广过程中对模块定义的规范化产出。
```

AMD 是提前执行，CMD 是延迟执行。
AMD推荐的风格通过返回一个对象做为模块对象，CommonJS的风格通过对module.exports或exports的属性赋值来达到暴露模块对象的目的。

#### 前端工程的价值体现在哪

```
  为简化用户使用提供技术支持（交互部分）

  为多个浏览器兼容性提供支持

  为提高用户浏览速度（浏览器性能）提供支持

  为跨平台或者其他基于webkit或其他渲染引擎的应用提供支持

  为展示数据提供支持（数据接口）
```

#### 谈谈性能优化问题

代码层面：避免使用css表达式，避免使用高级选择器，通配选择器。

缓存利用：缓存Ajax，使用CDN，使用外部js和css文件以便缓存，添加Expires头，服务端配置Etag，减少DNS查找等

请求数量：合并样式和脚本，使用css图片精灵，初始首屏之外的图片资源按需加载，静态资源延迟加载。

请求带宽：压缩文件，开启GZIP

> 代码层面的优化

+  用hash-table来优化查找
+  少用全局变量
+  用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能
+  用setTimeout来避免页面失去响应
+  缓存DOM节点查找的结果
+  避免使用CSS Expression
+  避免全局查询
+  避免使用with(with会创建自己的作用域，会增加作用域链长度)
+  多个变量声明合并
+  避免图片和iFrame等的空Src。空Src会重新加载当前页面，影响速度和效率
+  尽量避免写在HTML标签中写Style属性

#### 移动端性能优化

+  尽量使用css3动画，开启硬件加速。
+  适当使用touch事件代替click事件。
+  避免使用css3渐变阴影效果。
+  可以用transform: translateZ(0)来开启硬件加速。
+  不滥用Float。Float在渲染时计算量比较大，尽量减少使用
+  不滥用Web字体。Web字体需要下载，解析，重绘当前页面，尽量减少使用。
+  合理使用requestAnimationFrame动画代替setTimeout
+  CSS中的属性（CSS3 transitions、CSS3 3D transforms、Opacity、Canvas、WebGL、Video）会触发GPU渲染，请合理使用。过渡使用会引发手机过耗电增加
+  PC端的在移动端同样适用

#### 你觉得jQuery或zepto源码有哪些写的好的地方
(答案仅供参考)

jquery源码封装在一个匿名函数的自执行环境中，有助于防止变量的全局污染，然后通过传入window对象参数，可以使window对象作为局部变量使用，好处是当jquery中访问window对象的时候，就不用将作用域链退回到顶层作用域了，从而可以更快的访问window对象。同样，传入undefined参数，可以缩短查找undefined时的作用域链。

```
  (function( window, undefined ) {

       //用一个函数域包起来，就是所谓的沙箱

       //在这里边var定义的变量，属于这个函数域内的局部变量，避免污染全局

       //把当前沙箱需要的外部变量通过函数参数引入进来

       //只要保证参数对内提供的接口的一致性，你还可以随意替换传进来的这个参数

      window.jQuery = window.$ = jQuery;

  })( window );
```

jquery将一些原型属性和方法封装在了jquery.prototype中，为了缩短名称，又赋值给了jquery.fn，这是很形象的写法。
有一些数组或对象的方法经常能使用到，jQuery将其保存为局部变量以提高访问速度。
jquery实现的链式调用可以节约代码，所返回的都是同一个对象，可以提高代码效率。

#### ES6的了解

```
  新增模板字符串（为JavaScript提供了简单的字符串插值功能）、箭头函数（操作符左边为输入的参数，而右边则是进行的操作以及返回的值Inputs=>outputs。）、for-of（用来遍历数据—例如数组中的值。）arguments对象可被不定参数和默认参数完美代替。ES6将promise对象纳入规范，提供了原生的Promise对象。增加了let和const命令，用来声明变量。增加了块级作用域。let命令实际上就增加了块级作用域。ES6规定，var命令和function命令声明的全局变量，属于全局对象的属性；let命令、const命令、class命令声明的全局变量，不属于全局对象的属性。。还有就是引入module模块的概念
```

#### js继承方式
原型链继承，借用构造函数（类式继承），组合式继承，原型式继承，寄生式继承，寄生组合式继承

具体请看：[JavaScript继承方式详解](https://segmentfault.com/a/1190000002440502)

#### defer和async

```
  defer并行加载js文件，会按照页面上script标签的顺序执行
  async并行加载js文件，下载完成立即执行，不会按照页面上script标签的顺序执行
```

#### 用过哪些设计模式？
+  工厂模式：

主要好处就是可以消除对象间的耦合，通过使用工程方法而不是new关键字。将所有实例化的代码集中在一个位置防止代码重复。工厂模式解决了重复实例化的问题 ，但还有一个问题,那就是识别问题，因为根本无法 搞清楚他们到底是哪个对象的实例。

```
  function createObject(name,age,profession){//集中实例化的函数var obj = new Object();
      obj.name = name;
      obj.age = age;
      obj.profession = profession;
      obj.move = function () {
          return this.name + ' at ' + this.age + ' engaged in ' + this.profession;
      };
      return obj;
  }
  var test1 = createObject('trigkit4',22,'programmer');//第一个实例var test2 = createObject('mike',25,'engineer');//第二个实例
```

+  构造函数模式

使用构造函数的方法 ，即解决了重复实例化的问题 ，又解决了对象识别的问题，该模式与工厂模式的不同之处在于：

```
  1.构造函数方法没有显示的创建对象 (new Object());
  2.直接将属性和方法赋值给 this 对象;
  3.没有 renturn 语句。
```

#### 说说你对闭包的理解

使用闭包主要是为了设计私有的方法和变量。闭包的优点是可以避免全局变量的污染，缺点是闭包会常驻内存，会增大内存使用量，使用不当很容易造成内存泄露。在js中，函数即闭包，只有函数才会产生作用域的概念。

闭包有三个特性：

```
  1.函数嵌套函数
  2.函数内部可以引用外部的参数和变量
  3.参数和变量不会被垃圾回收机制回收
```

具体请看：[详解js闭包](https://segmentfault.com/a/1190000000652891)

#### 谈谈Cookie的弊端

cookie虽然在持久保存客户端数据提供了方便，分担了服务器存储的负担，但还是有很多局限性的。

第一：每个特定的域名下最多生成20个cookie

```
  1.IE6或更低版本最多20个cookie
  2.IE7和之后的版本最后可以有50个cookie。
  3.Firefox最多50个cookie
  4.chrome和Safari没有做硬性限制
```

IE和Opera 会清理近期最少使用的cookie，Firefox会随机清理cookie。

cookie的最大大约为4096字节，为了兼容性，一般不能超过4095字节。

IE 提供了一种存储可以持久化用户数据，叫做userdata，从IE5.0就开始支持。每个数据最多128K，每个域名下最多1M。这个持久化数据放在缓存中，如果缓存没有清理，那么会一直存在。

> 优点：极高的扩展性和可用性

```
  1.通过良好的编程，控制保存在cookie中的session对象的大小。
  2.通过加密和安全传输技术（SSL），减少cookie被破解的可能性。
  3.只在cookie中存放不敏感数据，即使被盗也不会有重大损失。
  4.控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。
```

> 缺点：
```
  1.cookie数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。
  2.安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。
  3.有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。

```

#### 浏览器本地存储

在较高版本的浏览器中，js提供了sessionStorage和globalStorage。在HTML5中提供了localStorage来取代globalStorage。
html5中的Web Storage包括了两种存储方式：sessionStorage和localStorage。
sessionStorage用于本地存储一个会话（session）中的数据，这些数据只有在同一个会话中的页面才能访问并且当会话结束后数据也随之销毁。因此sessionStorage不是一种持久化的本地存储，仅仅是会话级别的存储。
而localStorage用于持久化的本地存储，除非主动删除数据，否则数据是永远不会过期的。

#### cookie 和session 的区别

```
  1、cookie数据存放在客户的浏览器上，session数据放在服务器上。
  2、cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗考虑到安全应当使用session。
  3、session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能考虑到减轻服务器性能方面，应当使用cookie。
  4、单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。
  5、所以个人建议：
    将登陆信息等重要信息存放为session
    其他信息如果需要保留，可以放在cookie中
```

#### CSS中 link 和@import 的区别

```
  (1) link属于HTML标签，而@import是CSS提供的;
  (2) 页面被加载的时，link会同时被加载，而@import被引用的CSS会等到引用它的CSS文件被加载完再加载;
  (3) import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
  (4) link方式的样式的权重 高于@import的权重.
```

#### box-sizing属性

box-sizing属性主要用来控制元素的盒模型的解析模式。默认值是content-box。
+  content-box：让元素维持W3C的标准盒模型。元素的宽度/高度由border + padding + content的宽度/高度决定，设置width/height属性指的是content部分的宽/高
+  border-box：让元素维持IE传统盒模型（IE6以下版本和IE6~7的怪异模式）。设置width/height属性指的是border + padding + content

> CSS 选择符有哪些？哪些属性可以继承？优先级算法如何计算？ CSS3新增伪类有那些？

```
  1.id选择器（ # myid）
  2.类选择器（.myclassname）
  3.标签选择器（div, h1, p）
  4.相邻选择器（h1 + p）
  5.子选择器（ul > li）
  6.后代选择器（li a）
  7.通配符选择器（ * ）
  8.属性选择器（a[rel = "external"]）
  9.伪类选择器（a: hover, li:nth-child）
```

优先级为: !important > id > class > tag，important 比 内联优先级高,但内联比 id 要高

#### CSS3有哪些新特性？

```
  CSS3实现圆角（border-radius），阴影（box-shadow），
  对文字加特效（text-shadow、），线性渐变（gradient），旋转（transform）
  transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);//旋转,缩放,定位,倾斜
  增加了更多的CSS选择器  多背景 rgba
  在CSS3中唯一引入的伪元素是::selection.
  媒体查询，多栏布局
  border-image
```

#### 对BFC规范的理解

```
  BFC，块级格式化上下文，一个创建了新的BFC的盒子是独立布局的，盒子里面的子元素的样式不会影响到外面的元素。在同一个BFC中的两个毗邻的块级盒在垂直方向（和布局方向有关系）的margin会发生折叠。
  （W3C CSS 2.1 规范中的一个概念，它决定了元素如何对其内容进行布局，以及与其他元素的关系和相互作用。
```

#### 对语义化的理解

```
  1，去掉或者丢失样式的时候能够让页面呈现出清晰的结构
  2，有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重；
  3，方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
  4，便于团队开发和维护，语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化。
```

#### Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?

```
  1）、<!DOCTYPE> 声明位于文档中的最前面，处于 <html> 标签之前。告知浏览器以何种模式来渲染文档。
  2）、严格模式的排版和 JS 运作模式是 以该浏览器支持的最高标准运行。
  3）、在混杂模式中，页面以宽松的向后兼容的方式显示。模拟老式浏览器的行为以防止站点无法工作。
  4）、DOCTYPE不存在或格式不正确会导致文档以混杂模式呈现。
```

#### 浮动元素引起的问题和解决办法？

浮动元素引起的问题：
```
  （1）父元素的高度无法被撑开，影响与父元素同级的元素
  （2）与浮动元素同级的非浮动元素（内联元素）会跟随其后
  （3）若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构
```

解决方法：

> 使用CSS中的clear:both;属性来清除元素的浮动可解决2、3问题，对于问题1，添加如下样式，给父元素添加clearfix样式：

```
.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}
.clearfix{display: inline-block;} /* for IE/Mac */
```

#### html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 HTML 和 HTML5？

```
  HTML5 现在已经不是 SGML 的子集，主要是关于图像，位置，存储，多任务等功能的增加。
  拖拽释放(Drag and drop) API
  语义化更好的内容标签（header,nav,footer,aside,article,section）
  音频、视频API(audio,video)
  画布(Canvas) API
  地理(Geolocation) API
  本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；
  sessionStorage 的数据在浏览器关闭后自动删除
```

```
  表单控件，calendar、date、time、email、url、search
  新的技术webworker, websocket, Geolocation
```

> 移除的元素

```
纯表现的元素：basefont，big，center，font, s，strike，tt，u；
对可用性产生负面影响的元素：frame，frameset，noframes；
```

> 支持HTML5新标签：

```
IE8/IE7/IE6支持通过document.createElement方法产生的标签，可以利用这一特性让这些浏览器支持HTML5新标签，当然最好的方式是直接使用成熟的框架、使用最多的是html5shim框架
 <!--[if lt IE 9]>
 <script> src="http://html5shim.googlecode.com/svn/trunk/html5.js"</script>
 <![endif]-->
如何区分： DOCTYPE声明\新增的结构元素\功能元素
```

#### null和undefined的区别？

null是一个表示"无"的对象，转为数值时为0；undefined是一个表示"无"的原始值，转为数值时为NaN。
当声明的变量还未被初始化时，变量的默认值为undefined。
null用来表示尚未存在的对象，常用来表示函数企图返回一个不存在的对象。
undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义。典型用法是：

```
（1）变量被声明了，但没有赋值时，就等于undefined。
（2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。
（3）对象没有赋值的属性，该属性的值为undefined。
（4）函数没有返回值时，默认返回undefined。
```

null表示"没有对象"，即该处不应该有值。典型用法是：

```
（1） 作为函数的参数，表示该函数的参数不是对象。
（2） 作为对象原型链的终点。
```

#### js延迟加载的方式有哪些？

```
defer和async、动态创建DOM方式（创建script，插入到DOM中，加载完毕后callBack）、按需异步载入js
```

####　call() 和 apply() 的区别和作用？

apply()函数有两个参数：第一个参数是上下文，第二个参数是参数组成的数组。如果上下文是null，则使用全局对象代替。例如：

```
function.apply(this,[1,2,3])
```

call()的第一个参数是上下文，后续是实例传入的参数序列，例如：

```
function.call(this,1,2,3);
```

#### WEB应用从服务器主动推送Data到客户端有那些方式？

Javascript数据推送:

```
  1、Commet：基于HTTP长连接的服务器推送技术
  2、基于WebSocket的推送方案
  3、SSE（Server-Send Event）：服务器推送数据新方式
```

#### 一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？

```
  分为4个步骤：
    （1），当发送一个URL请求时，不管这个URL是Web页面的URL还是Web页面上每个资源的URL，浏览器都会开启一个线程来处理这个请求，同时在远程DNS服务器上启动一个DNS查询。这能使浏览器获得请求对应的IP地址。
    （2）， 浏览器与远程`Web`服务器通过`TCP`三次握手协商来建立一个`TCP/IP`连接。该握手包括一个同步报文，一个同步-应答报文和一个应答报文，这三个报文在 浏览器和服务器之间传递。该握手首先由客户端尝试建立起通信，而后服务器应答并接受客户端的请求，最后由客户端发出该请求已经被接受的报文。
    （3），一旦`TCP/IP`连接建立，浏览器会通过该连接向远程服务器发送`HTTP`的`GET`请求。远程服务器找到资源并使用HTTP响应返回该资源，值为200的HTTP响应状态表示一个正确的响应。
    （4），此时，`Web`服务器提供资源服务，客户端开始下载资源。
```

#### HTTP状态码

```
  100  Continue  继续，一般在发送post请求时，已发送了http header之后服务端将返回此信息，表示确认，之后发送具体参数信息
  200  OK   正常返回信息
  201  Created  请求成功并且服务器创建了新的资源
  202  Accepted  服务器已接受请求，但尚未处理
  301  Moved Permanently  请求的网页已永久移动到新位置。
  302 Found  临时性重定向。
  303 See Other  临时性重定向，且总是使用 GET 请求新的 URI。
  304  Not Modified  自从上次请求后，请求的网页未修改过。
  400 Bad Request  服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。
  401 Unauthorized  请求未授权。
  403 Forbidden  禁止访问。
  404 Not Found  找不到如何与 URI 相匹配的资源。
  500 Internal Server Error  最常见的服务器端错误。
  503 Service Unavailable 服务器端暂时无法处理请求（可能是过载或维护）。
```

#### 说说你对Promise的理解

依照 Promise/A+ 的定义，Promise 有四种状态：
```
pending: 初始状态, 非 fulfilled 或 rejected
fulfilled: 成功的操作
rejected: 失败的操作
settled: Promise已被fulfilled或rejected，且不是pending
```

另外， fulfilled 与 rejected 一起合称 settled。
Promise 对象用来进行延迟(deferred) 和异步(asynchronous ) 计算。

> Promise 的构造函数

构造一个 Promise，最基本的用法如下：

```
  var promise = new Promise(function(resolve, reject) {
      if (...) {  // succeed
          resolve(result);
      } else {   // fails
          reject(Error(errMessage));
      }
  });
```

Promise 实例拥有 then 方法（具有 then 方法的对象，通常被称为 thenable）。它的使用方法如下：

```
promise.then(onFulfilled, onRejected)
```

接收两个函数作为参数，一个在 fulfilled 的时候被调用，一个在 rejected 的时候被调用，接收参数就是 future，onFulfilled 对应 resolve, onRejected 对应 reject。

#### 对AMD和Commonjs的理解

CommonJS是服务器端模块的规范，Node.js采用了这个规范。CommonJS规范加载模块是同步的，也就是说，只有加载完成，才能执行后面的操作。AMD规范则是非同步加载模块，允许指定回调函数。

AMD推荐的风格通过返回一个对象做为模块对象，CommonJS的风格通过对module.exports或exports的属性赋值来达到暴露模块对象的目的。

