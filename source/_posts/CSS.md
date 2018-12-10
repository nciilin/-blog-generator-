---
title: CSS
date: 2018-12-10 23:45:52
tags:
---


## 本文主要包括以下内容：

1. 高度是由什么决定的?
2. line-box 是啥?
3. box 是啥（盒模型）?
4. 宽度是由什么决定的?
5. position 的 5 个取值
6. z-index

### 1、高度是由什么决定的?

- **内联元素** (自左往右,自动换行，但如果内联元素是一个很长的英文单词，则不会分开换行)
`内联元素的高是由字体设计师决定` 
- **块级元素** (从上往下，占据整行)
`块级元素的高度由其内部文档流元素的高度总分决定的`

### 2、line-box 是啥?

- 每一行称为一条Line Box，它又是由这一行的许多**inline-box组成，它的高度可以直接由line-height决定**，line boxes的高度垂直堆叠形成了containing box的高度，就是我们见到的div或是p标签之类的高度了。

### 3、box 是啥（盒模型）?

- 盒模型对比
![盒模型对比.png](http://upload-images.jianshu.io/upload_images/6970717-2046f9172e7c0e58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
`W3C标准中padding、border所占的空间不在width、height范围内，大家俗称的IE的盒模型width包括content尺寸＋padding＋border`

### 4、宽度是由什么决定的?

- **行内元素**的宽度是由它的**内容**决定的，行内元素不能设置宽高
- **块级元素**当没有设置宽度是**默认100%宽**，当设置了宽度是就是固定的宽度 

### 5、position 的 5 个取值

- sticky
- absolute
- fixed
- relative
- static

### 6、z-index

- **z-index 属性指定了一个具有定位属性的元素及其子代元素的 z-order。 当元素之间重叠的时候，z-order 决定哪一个元素覆盖在其余元素的上方显示。 通常来说 z-index 较大的元素会覆盖较小的一个。**
- 链接：[z-index标签](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)