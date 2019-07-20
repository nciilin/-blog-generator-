---
layout: 
title: JS里的数据类型转换
date: 2019-07-05 21:05:17
tags:
---

## 任意类型转字符串
### String(x)
![图片](https://static.xiedaimala.com/FrpnWPAjH4_Zh1Ru58nEIC0I4onn)
### toString()
![图片](https://static.xiedaimala.com/FnbB3yikB790jzpavhE6eyqioUPP)
### + 0 
![图片](https://static.xiedaimala.com/FgaPxjEAu8-hzeBRnQ7jdHlZiw85)


## 任意类型转为number

```
 '1' -> 1
 Number('1') === 1
 parseInt('1', 10) === 1
 parseFloat('1.23') === 1.23
 '1' + 0 === 1
 
```

## 任意类型转boolean
```

 Boolean(x)
 !!x

```

## 数据类型的false值
 `0`、`NaN`、`false`、` `、`undefined`、`null`
