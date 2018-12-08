---
title: HTML
date: 2018-12-08 17:42:01
tags:
---

## 本文主要包括以下内容：

1. HTML 的版本
2. 怎样理解 HTML 语义化
3. 怎样理解内容与样式分离的原则
4. 有哪些常见的meta标签
5. 文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用?
6. 浏览器乱码的原因是什么？如何解决?
7. 常见的浏览器有哪些？什么内核？
8. 列出常见的标签，并简单介绍这些标签用在什么场景

### 1、HTML 的版本

- HTML `超文本标记语言`（HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言。
- XML `可扩展标识语言`(The Extensible Markup Language)的简写，主要用于存储数据和结构。
- XHTML `可扩展标识语言` (The Extensible HyperText Markup Language)的缩写,基于XML，作用与HTML类似,目的就是实现HTML向XML的过渡。 

### 2、怎样理解 HTML 语义化

- 语义化HTML是一种编写HTML的方式。
- 选择合适的标签、使用合理的代码结构，便于开发者阅读，同时让浏览器的爬虫和机器很好地解析。
- 语义化的好处:
    1. 页面呈现出很好地**内容结构、代码结构**。
    2. **用户体验好**。
    3. 利于**SEO优化**。
    4. 方便其他设备**解析**来渲染网页。
    5. 便于**团队开发和维护**，语义化更具**可读性**。

### 3、怎样理解内容与样式分离的原则

- 在WEB开发中， 一个网页分为三部分：`Html——结构（内容）`，`css——表现（样式）`，`javascrip——行为`。内容与样式分离，就是让内容的归 HTML, 样式归 CSS。同时，HTML 内不允许出现属性样式，尽量不要出现行内样式。
- 编码正确做法是HTML和CSS要分开使用，不要混着用。重点放在HTML的结构和语义化上，让HTML能提现页面结构或者内容,，然后进行 css 样式设置（即内容与样式分离） ，写JS的时候，尽量不要用JS去直接操作样式，而是通过给元素添加删除class来控制样式变化（即行为分离）。
- 分离原则的优点:
  1. **浏览器加载网页页面速度变快**。分离原则下，大部分页面代码写在了CSS当中，页面体积容量变得更小。
  2. **网页修改设计时，效率、省时**。根据html标签内ID或class的标记，到CSS里找到相应的ID或class，可以快速替换指定位置的样式，不会破坏页面架构和其他部分的样式。
  3. **典型的应用就是网页换肤**。使用相同的 html 结构，不同的 CSS 样式。
  4. **更好地被搜索引擎收录**。基于内容与样式分离的原则，html的语义化就是首要考虑的,网页中语义化的标签代码就会更加适合搜索引擎。
  5. **CSS样式的分离，它可以根据不同的浏览器，达到显示效果的统一**。保证网页架构不变形的前提下，放心在不同浏览器渲染显示样式。

### 4、有哪些常见的meta标签

- 语言采用**中文**
  `<meta http-equiv="Content-Language" content="zh-CN" />`       
       
- 编码格式：**告诉给浏览器用什么方式来都这页代码**
    `<meta charset="utf-8">`       
- 如果支持Google Chrome Frame：GCF，则使用GCF渲染；如果系统安装ie8或以上版本，则使用最高版本ie渲染； 否则，这个设定可以忽略。 目的**使内容在移动端上比较合理展示**。
    `<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">`    
- 控制网页为全屏幕大小
    `<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">`
- 目的是方便**SEO优化**内容关键字搜索
    `<meta name="keywords" content="">`

### 5、文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用?

- 文档声明的作用
    <p>文档声明目的是**防止出现乱码**情况。</p>
- 严格模式和混杂模式指什么
  **严格模式**：又称标准模式，是指**浏览器按照 W3C 标准解析代码**。
  **混杂模式**：又称怪异模式或兼容模式，是指**浏览器用自己的方式解析代码**。
     **区分**    ：浏览器解析时到底使用严格模式还是混杂模式，与网页中的 **DTD** 直接相关。
- 关于<!DOCTYPE html>
    - 关于<DOCTYPE>声明叫做文件类型定义（DTD），声明的作用**为了告诉浏览器该文件的类型。让浏览器解析器知道应该用哪个规范来解析文档**。

### 6、浏览器乱码的原因是什么？如何解决?

- html源代码内中文字内容与html编码不同造成。但无论是哪种情况造成乱码在网页开始时候都需要设置网页编码。
- 解决： 
    `<meta charset="utf-8">`

### 7、常见的浏览器有哪些？什么内核？

- 浏览器
<p>chrome浏览器、火狐浏览器（Mozilla Firefox）、IE浏览器、360极速浏览器、搜狗浏览器、猎豹极轻浏览器等。</p>

- 内核
  1、Trident(IE内核)； 
  2、Gecko(Firefox内核)；
  3、Presto(Opera前内核) (已废弃)；
  4、Webkit(Safari内核,Chrome内核原型,开源)。

### 8、列出常见的标签，并简单介绍这些标签用在什么场景
- **注意点**
  1、标签属性全小写;
  2、标签要闭合、自闭合标签可以省略 /;
  3、标题里不能有段落，段落里不能有标题;
- `h1~h6` 标题
  > <h1>代表页面最大的标题</h1>
  > <h2>二级标题</h2>
  > <h3>更弱的标题</h3>
  > <h4>...</h4>
  > <h5>...</h5>
  > <h6>最小标题</h6>
- `p`段落
  > <p>表示大段文字</p>
- `a`链接，链到一个地址
  > <a href="http://www.google.com"" target="_blank" title="ABC">google.com</a>
  > <a href="#">空</a>
  > <a href="#about">定位ID标签about位置</a>
  > <a href="/getCourse">链接路径地址</a>
- `img`展示一张图片
    > ![](a.png)
- `div`语义为“一大块”，用于给页面划分区块，让结构更清晰
    > <div id="header">...</div>
    > <div id="content">...</div>
    > <div id="footer">...</div>
- `ul li`
- ul: unsort list 无序列表
- 用于表示并列的内容
- ul的直接子元素是li
- 可以嵌套
  > <ul class="nav">
  >   <li><a href="#">首页</a></li>
  >   <li><a href="#">关于</a></li>
  >       <li>
  >             <a href="#">更多</a>
  >             <ul>
  >                   <li>联系</li>
  >                   <li>地址</li>
  >             </ul>
  >       </li>
  > </ul>·
- `ol li`
- ol: order list 有序序列表 
- 用于表示带步骤或者编号的并列内容 
- ol的直接子元素只能是li 可以嵌套
  > <h2>把大象关到冰箱的步骤</h2>
  > <ol>
  >   <li>把大象变小</li>
  >   <li>打开冰箱</li>
  >   <li>把大象塞进去</li>
  > </ol>
- dl dt dd用于展示一系列 “标题:内容... ”的场景
  > <dl>
  >   <dt>商品名称:</dt>
  >   <dd>青花瓷</dd>
  >   <dt>特征:</dt>
  >   <dd>白色</dd>
  >   <dd>圆口</dd>
  >   <dt>商品介绍</dt>
  >   <dd>这是一个年代久远的瓷器，很贵，易碎</dd>
  > </dl>
- `button`按钮
  > <button>点我</button>
- `strong em`
- em 需要强调一下
- strong 很重要、强调性更强
  > <p>优惠 <strong>100</strong> 元</p>
  > <p>小谷 <em>2</em> 岁了</p>
- `iframe`用于嵌入一个页面 注意跨域操作问题
  > <iframe src="http://www.google.com" name="myPage"></iframe>
  > <p><a href="http://www.baidu.com"" target="myPage">baidu.com</a></p>
- `table`用于展示表格，不要用来做布局 thead tbody tfoot可省略，浏览器会自动添加 border-collapse: collapse;用于合并边框
  > <table>
  > <tr>
  >   <th>姓名</th>
  >   <th>年纪</th>
  > </tr>
  > <tr>
  >   <td>小明</td>
  >   <td>18</td>
  > </tr>
  > <tr>
  >   <td>小花</td>
  >   <td>20</td>
  > </tr>
  > </table>
