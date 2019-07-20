---
title: JS操作DOM常用API
date: 2019-07-07 19:53:38
tags:
---

## 基本概念
### Node类型
Node类型中，我们最常用的就是element，text，attribute，comment，document，document_fragment这几种类型。

### Element类型
Element提供了对元素标签名，子节点和特性的访问，我们常用HTML元素比如div，span，a等标签就是element中的一种。

**特性：**
(1) `nodeType为1`
(2) `nodeName为元素标签名，tagName也是返回标签名`
(3) `nodeValue为null`
(4) `parentNode可能是Document或Element`
(5) `子节点可能是Element，Text，Comment，Processing_Instruction，CDATASection或EntityReference`

### Text类型
Text表示文本节点，它包含的是纯文本内容，不能包含html代码，但可以包含转义后的html代码。
**特性：**
(1) `nodeType为3`
(2) `nodeName为#text`
(3) `nodeValue为文本内容`
(4) `parentNode是一个Element`
(5) `没有子节点`

### Attr类型
Attr类型表示元素的特性，相当于元素的attributes属性中的节点。
**特性：**
(1) `nodeType值为2`
(2) `nodeName是特性的名称`
(3) `nodeValue是特性的值`
(4) `parentNode为null`

### Comment类型
Comment表示HTML文档中的注释。
**特性：**
(1) `nodeType为8`
(2) `nodeName为#comment`
(3) `nodeValue为注释的内容`
(4) `parentNode可能是Document或Element`
(5) `没有子节点`

### Document类型
Document表示文档，在浏览器中，document对象是HTMLDocument的一个实例，表示整个页面，它同时也是window对象的一个属性。
**特性：**
(1) `nodeType为9`
(2) `nodeName为#document`
(3) `nodeValue为null`
(4) `parentNode为null`
(5) `子节点可能是一个DocumentType或Element`

### DocumentFragment类型
DocumentFragment是所有节点中唯一一个没有对应标记的类型，它表示一种轻量级的文档，可能当作一个临时的仓库用来保存可能会添加到文档中的节点。
**特性：**
(1) `nodeType为11`
(2) `nodeName为#document-fragment`
(3) `nodeValue为null`
(4) `parentNode为null`

## 节点创建型api

### createElement
通过传入指定的一个标签名来创建一个元素
```
var div = document.createElement("div");
```

### createTextNode 

创建一个文本节点
```
var textNode = document.createTextNode("一个TextNode");
```

### cloneNode
返回调用方法的节点的一个副本，它接收一个bool参数，用来表示是否复制子元素
```
var parent = document.getElementById("parentElement");
var parent2 = parent.cloneNode(true);// 传入true
parent2.id = "parent2";
```

### createDocumentFragment
用来创建一个DocumentFragment
```
var fragment = document.createDocumentFragment();
```

### 创建型API总结

1. 它们创建的节点只是一个孤立的节点，要通过`appendChild`添加到文档中

2. cloneNode要注意如果被复制的节点是否包含子节点以及事件绑定等问题

3. 使用createDocumentFragment来解决添加大量节点时的性能问题

## 页面修改型API
修改页面内容的api主要包括：**appendChild，insertBefore，removeChild，replaceChild**。

### appendChild
child节点将会作为parent节点的最后一个子节点。

```
parent.appendChild(child);
```

### insertBefore

insertBefore用来添加一个节点到一个参照节点之前
```
parentNode.insertBefore(newNode,refNode);
```

### removeChild

删除指定的子节点并返回
```
var deletedChild = parent.removeChild(node);
```

### replaceChild
replaceChild用于使用一个节点替换另一个节点
```
parent.replaceChild(newChild,oldChild);
```
## 页面修改型API总结

1. 不管是新增还是替换节点，如果新增或替换的节点是原本存在页面上的，则其原来位置的节点将被移除，也就是说同一个节点不能存在于页面的多个位置

2. 节点本身绑定的事件会不会消失，会一直保留着。

## 节点查询型API

### document.getElementById
根据元素id返回元素，返回值是Element类型，如果不存在该元素，则返回null。
**注意：**

1. 元素的Id是大小写敏感的，一定要写对元素的id

2. HTML文档中可能存在多个id相同的元素，则返回第一个元素

3. 只从文档中进行搜索元素，如果创建了一个元素并指定id，但并没有添加到文档中，则这个元素是不会被查找到的

### document.getElementsByTagName
根据元素标签名获取元素，返回一个即时的HTMLCollection类型
**注意：**

1. 如果要对HTMLCollection集合进行循环操作，最好将其长度缓存起来，因为每次循环都会去计算长度，暂时缓存起来可以提高效率

2. 如果没有存在指定的标签，该接口返回的不是null，而是一个空的HTMLCollection

3. “*”表示所有标签

### document.getElementsByName
主要是通过指定的name属性来获取元素，它返回一个即时的NodeList对象。
**注意：**

1. 返回对象是一个即时的NodeList，它是随时变化的

2. 在HTML元素中，并不是所有元素都有name属性，比如div是没有name属性的，但是如果强制设置div的name属性，它也是可以被查找到的

3. 在IE中，如果id设置成某个值，然后传入getElementsByName的参数值和id值一样，则这个元素是会被找到的，所以最好不好设置同样的值给id和name

### document.getElementsByClassName
这个API是根据元素的class返回一个即时的HTMLCollection
`var elements = document.getElementsByClassName(names);`
**注意：**

1. 返回结果是一个即时的HTMLCollection，会随时根据文档结构变化

2. IE9以下浏览器不支持

3. 如果要获取2个以上classname，可传入多个classname，每个用空格相隔

### document.querySelector和document.querySelectorAll
这两个api很相似，通过css选择器来查找元素，注意选择器要符合CSS选择器的规则。
`document.querySelector`返回**第一个匹配的元素**，如果没有匹配的元素，则返回null。
`document.querySelectorAll`的不同之处在于它返回的是**所有匹配的元素**，而且可以匹配多个选择符
**注意：**

1. querySelectorAll也是通过深度优先搜索，搜索的元素顺序和选择器的顺序无关

2. 返回的是一个非即时的NodeList，也就是说结果不会随着文档树的变化而变化

## 节点关系型api

### 父关系型api
`parentNode`：每个节点都有一个parentNode属性，它表示元素的父节点。Element的父节点可能是Element，Document或DocumentFragment。
`parentElement`：返回元素的父元素节点，与parentNode的区别在于，其父节点必须是一个Element，如果不是，则返回null

### 兄弟关系型api
`previousSibling`：节点的前一个节点，如果该节点是第一个节点，则为null。注意有可能拿到的节点是文本节点或注释节点，与预期的不符，要进行处理一下。
`previousElementSibling`：返回前一个元素节点，前一个节点必须是Element，注意IE9以下浏览器不支持。
`nextSibling`：节点的后一个节点，如果该节点是最后一个节点，则为null。注意有可能拿到的节点是文本节点，与预期的不符，要进行处理一下。
`nextElementSibling`：返回后一个元素节点，后一个节点必须是Element，注意IE9以下浏览器不支持。

### 子关系型api
`childNodes`：返回一个即时的NodeList，表示元素的子节点列表，子节点可能会包含文本节点，注释节点等。
`children`：一个即时的HTMLCollection，子节点都是Element，IE9以下浏览器不支持。
`firstNode`：第一个子节点
`lastNode`：最后一个子节点
`hasChildNodes`方法：可以**用来判断是否包含子节点。**

### 元素属性型api

### setAttribute
根据名称和值修改元素的特性

```
element.setAttribute(name, value);
```

### getAttribute
返回指定的特性名相应的特性值，如果不存在，则返回null或空字符串
```
var value = element.getAttribute("id");
```

## 元素样式型api

### window.getComputedStyle
用来获取应用到元素后的样式，假设某个元素并未设置高度而是通过其内容将其高度撑开，这时候要获取它的高度就要用到getComputedStyle
```
var style = window.getComputedStyle(element[, pseudoElt]);
```
### getBoundingClientRect
返回元素的大小以及相对于浏览器可视窗口的位置

```
var clientRect = element.getBoundingClientRect();
```