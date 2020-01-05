## 一、 HTML4与HTML5有什么不同？
### HTML5主要解决了以往文档的一些痛点：
1. **解决文档结构混乱**：以前的文档结构过于依赖div，HTML5推出了多种语义化标签，使得文档更利于阅读器等理解，更利于SEO优化。
2. **解决浏览器之间的兼容性问题**：市场上的浏览器种类繁多，每个浏览器厂商都在做自己的东西，没有一个标准限值，HTML5的出现就是为了统一标准。
3. **扩展Web应用的功能**：以前Web页面仅仅只是展示作用，HTML5出现许多新的api，浏览器厂商也在迅速的封装这些api，使的Web页面更像是一个多交互的应用而非单纯的页面展示。
### HTML4与HTML5主要区别
1. **文档类型声明** 文档声明的作用就是告诉标记语言解析器，应该用什么文档类型定义（DTD）来解析，HTML5的文档解析不再基于SGML(Standard Generalized Markup Language)标准，而是形成了自己的一套标准。
```
// HTML4.0.1
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//en" "http://www.w3.org/TR/html4/strict.dtd">

// HTML5
<!DOCTYPE HTML>
```
2. **标签方面**  
   新增语义标签，包括：
   ```
   <header>、<footer>、<section>、<aside>、<nav>、<article>、<hgroup>、<figure>
   ```
   **废除一些网页美化方面的标签，使样式与结构分离更加彻底**  
   ```
   <big>、<u>、<font>、<basefont>、<center>、<s>、<tt>
   ```
   增加了 ``<audio> <video>`` 两个标签实现对对媒体中的音频、视频的支持。
3. **属性方面**  
   增加了一些表单属性，主要是对input属性的增强  
   ```
   <!-- 要求输入正确的email地址 -->
   <input type="email">
   <!-- 要求输入正确的URL地址 -->
   <input type="url">
   <!-- 要求输入数字，默认会有上下两个按钮 -->
   <input type="number">
   <!-- 时间格式，但目前只有Opera和Chrome支持 -->
   <input type="date">
   <input type="time">
   <input type="datetime">
   <input type="datetime-local">
   <input type="month">
   <input type="week">
   <!-- 默认占位文字 -->
   <input type="text" placeholder="***">
   <!-- 聚焦属性 -->
   <input type="text" autofocus="true">
   ```
   其他标签也新增了一些属性  
   ```
   <!-- meta标签增加charset属性 -->
   <meta charset="utf-8">
   <!-- script标签增加async属性 -->
   <script async></async>
   ```
   部分属姓名默认具有boolean属性  
   ```
   <!-- 只写属性名默认为true -->
   <input type="checkbox"  checked/>
   <!-- 属性名="属性名"也为true -->
   <input type="checkbox"  checked="checked"/>
   ```
4. **存储方面**  
   - 新增WebStorage，包括localStorage、sessionStorage  
   - 引入了IndexDB和Web SQL，允许在浏览器端创建数据库并存储数据，两者的区别在于IndexDB更像是一个NoSQL数据库，而WebSQL更像是关系型数据库。W3C已经不再支持WebSQL。
   - 引入了应用程序缓存器(application cache)，可对Web进行缓存，在没有网络的情况下使用，通过创建cache mainfest文件创建应用缓存，为PWA提供了底层的技术支持。
## 二、meta标签属性都有哪些？
   **charset属性**  
   ```
   <!-- 定义网页文档的字符集 -->
   <meta charset="utf-8">
   ```
   **name + content属性**
   ```
   <!-- 网页作者 -->
   <meta name="author" content="作者名称"/>
   <!-- 网页地址 -->
   <meta name="website" content="url"/>
   <!-- 网页版权信息 -->
   <meta name="copyright" content="2019-2020 ***"/>
   <!-- 网页关键字 用于SEO -->
   <meta name="keywords" content="关键字"/>
   <!-- 网页描述 -->
   <meta name="description" content="网页描述"/>
   <!-- 搜索引擎索引方式，一般为all -->
   <meta name="robots" content="all"/>
   <!-- 移动端常用视口设置，参数详解
    width: 宽度（数值 / device-width 默认为980像素）
    height: 高度（数值 / device-height）
    initial-scale: 初始的缩放比例 范围从 0+ ~ 10
    minimum-scele: 允许用户缩放的最小比例
    maxmum-scale: 允许用户缩放的最大比例
    user-scalable: 用户是否可以手动缩放 no yes
   -->
   <meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no"/>
   ```
   **http-equiv属性**
   ```
   <!-- expires指定网页的过期时间，一旦过期，必须从服务器上下载 -->
   <meta http-equiv="expires" content="Fri, 12 Jan 2020 23:59:59 GMT" />
   <!-- refresh 等待一定的时间刷新或者跳转到其他url，下面表示一秒 -->
   <meta http-equiv="refresh" content="1; url=https://www.baidu.com" />
   <!-- pragma 禁止浏览器从本地缓存中读取网页，即浏览器一旦离开网页在无法连接网络的情况下就无法访问页面  -->
   <meta http-equiv="prgama" content="no-cache" />
   <!-- set-cookie 也是设置cookie的一种方式，并且可以指定过期时间 -->
   <meta http-equiv="set-cookie" content="name=value expires=Fri, 12 Jan 2020 23:59:59 GMT, path=/" />
   <!-- http-equiv="X-UA-Compatible 使用浏览器版本 -->
   <meta http-equiv="X-UA-Compatible" content="IE=edge, chrom=1" />
   <!-- 针对WebApp全屏模式，隐藏状态栏/设置状态栏颜色，content默认值为default | black | black-translucent -->
   <meta http-equiv="apple-mobile-web-app-status-bar-style" content="black-translucent" />
   ```
## 三、src和href的区别是什么？
   **定义**  
   href是Hypertext Reference的简写，表示超文本引用，指向网络资源所在位置。  
   常见场景：  
   ```
   <a href="https://www.baidu.com">
   <link type="text/css" rel="stylesheet" href="common.css">
   ```
   src是source的简写，目的是要把文件下载到html页面中去。
   常见场景：
   ```
   <img src="img/001.jpg">
   <iframe src="xxx.html">
   <script src="xxx.js">
   ```
   **作用结果**  
   1. href用于在当前文档和引用资源之间确立联系  
   2. src用于替换当前内容
   
   **浏览器解析方式**
   1. 当浏览器遇到href会并行下载资源并且不会停止对当前文档的处理，就是不会阻塞页面加载，这也是为什么建议使用link方式加载css，而不是使用@import。
   2. 当浏览器解析到src，会暂停其他资源的下载和处理，知道将该资源加载或者解析完毕。这也是script标签为什么放在底部而不是头部的原因。
## 四、script标签中的defer和async属性的区别是什么？
   默认情况下，脚本的下载和执行将会按照文档的先后顺序同步进行。当脚本下载和执行的时候，文档解析就会被阻塞，在脚本下载和解析完毕后文档才能继续往下继续解析。  
   
   下面是async和defer的区别：  
   1. 当script中有defer属性时，脚本的加载过程和文档的加载是异步发生的，等到文档解析完毕后（DOMContentLoaded事件发生）脚本才开始执行。
   2. 当script中有async属性时，脚本的加载过程和文档加载也是异步发生的。但是脚本下载完成后会停止HTML解析，会执行脚本，脚本解析完毕后继续HTML解析。
   3. 当script中同时有async和defer属性时，执行效果和async效果一致。
## 五、DOM篇
   ### 什么是DOM？
   ```
   MDN：文档对象模型（DOM）是HTML和XML文档的编程接口。它提供了对文档的结构化描述，并定义了一种方式可以使从程序中对该结构进行访问，从而改变文档的结构、样式和内容。DOM将文档解析为一个由节点和对象（包含属性和方法的对象）组成的结构集合。简言之，它会将web页面和脚本或者程序语言连接起来。
   ```
   说白了DOM就是浏览器为JavaScript提供的一系列接口去操作web页面。
   
   ### DOM创建
   DOM节点（Node）通常对应于一个标签、文本或者一个HTML属性。DOM节点有一个**nodeTyoe**属性用来表示当前元素的类型，它是一个整数：  
   1 - Element - 元素  
   2 - Attribute - 属性  
   3 - Text -文本  

   DOM节点创建最常用的就是document.createElement和document.createTextNode方法：  
   ```
   var el1 = document.createElement('div')
   var el2 = document.createElement('input')
   var node = document.createTextNode('Hello')

   ```
   ### DOM查询
   元素查询的API返回的结果是DOM节点或者DOM节点的列表。
   ```
   // 返回文档中第一个类名为"myClass"的元素
   var el = document.querySelector(".myClass")

   // 返回一个文档中所有的class为"node"或者"alert"的元素
   var els = document.querySelectorAll("div.note, div.alert")

   // 获取元素
   var el1 = document.getElementById('el1')
   var el2 = document.getElementByClassName('el2')
   var el3 = document.getElementByTagNAme('el3')
   ```
   Element也提供了很多相对于DOM导航方法：
   ```
   // 获取父元素、父节点
   var parent = ele.parentElement
   var parent = ele.parentNode

   // 获取子节点，子节点可以试试任何一种节点，可以通过nodeType判断
   var node = ele.children

   // 查询寻子元素
   var els = ele.getElementByTagName('td')
   var els = ele.getElementByClassName('test')

   // 当前元素的第一个 / 最后一个子元素节点
   var el = ele.firstElementChild
   var el = ele.lastElementChild

   // 上一个 / 下一个兄弟元素节点
   var el = ele.previousElementsibling
   var el = nextElementSibling
   ```

   ### DOM删改
   ```
   // 添加、删除子元素
   ele.appendChild(el)
   ele.removeChild(el)

   // 替换子元素
   ele.replaceChild(el1, el2)

   // 插入子元素
   parentElement.insertBefore(newElement, referenceElement)
   ```
   ### 属性操作
   
   ```
   // 获取一个{ name: value }的数组
   var attrs = el.attributes

   // 获取设置属性
   var c = el.getAttribute('class')
   el.setAttribute('class', 'newAttr')

   // 判断、移除属性
   el.hasAttribute('class')
   el.removeAttribute('class')

   // 是否有属性设置
   el.hasAttribute()
   ```
## 行内元素和块级元素的区别是什么？inline-block是什么？
   1. 行内元素会在一条直线上排列，默认宽度只与内容有关，水平方向排列；行内元素设置宽高无效，margin上下无效，padding上下无效，可以设置line-height；行内元素只能包含文本或者其他行内元素。
   
   2. 块级元素各占一行，默认宽度是它父容器的100%，与内容无关，垂直方向排列；块级元素从新行开始，结束接着一个断行，且块级元素可以包含块级元素和行内元素。
   
   3. inline-block元素（如img、input）既具有block元素可以设置宽高的特性，同时又具有inline元素默认不换行的特性。inline-block元素还可以设置verticle-align属性。HTML中的换行符、空格符、制表符等都会合并为空白符，字体大小不为0的情况下，空白负占据一定的宽度，使用inline-block会产生元素之间的空隙，需要注意一下。
   4. 行内元素有：
   ```
   <a>、<abbr>、<b>、<br>、<em>、<i>、<img>、<input>、<label>、<q>、<select>、<span>、<sub>、<textarea>、<tt>
   ```
   5. 块级元素有：
   ```
   <address>、<dd>、<dt>、<div>、<dl>、<fieldset>、<form>、<h1 - h6>、<hr>、<legend>、<li>、<ol>、<ul>、<p>、<table>、<td>、<tr>
   ```