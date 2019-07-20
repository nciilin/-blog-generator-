---
title: JSONP_跨域
date: 2019-07-19 12:28:54
tags:
---

## 什么是同源策略
同源策略限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的关键的安全机制。
**同源政策的目的，是为了保证用户信息的安全，防止恶意的网站窃取数据。**
所谓"同源"指的是"三个相同"。
- 协议相同
- 域名相同
- 端口相同


## 跨域有几种实现形式

跨域有4种实现形式。
1. jsonp
2. CORS
3. 降域
4. postMessage

## 什么是 JSONP？

jsonp是便于客户端使用数据，逐渐形成了一种非正式传输协议。jsonp的核心则是动态添加`<script>`标签来调用服务器提供的js脚本。

## JSONP 为什么不支持 POST

1. 因为JSONP是通过动态`<script>`创建的。
2. 使用动态`<script>`后只能使用GET请求，不能使用POST请求。

## 什么是CORS
CORS 全称是**跨域资源共享**（`Cross-Origin Resource Sharing`），是一种 *AJAX* 跨域请求资源的方式，当你使用 **XMLHttpRequest** 发送请求时，浏览器发现该请求不符合同源策略，会给该请求加一个请求头：Origin，后台进行一系列处理，如果确定接受请求则在返回结果中加入一个响应头：`Access-Control-Allow-Origin`; 浏览器判断该相应头中是否包含 Origin 的值.

```
//  AJAX请求
let request = new XMLHttpRequest()
  request.open('GET', '/xxx')
  request.send()
  request.onreadystatechange(() => {
    if (request.readyState === 4) {
      if (request.status >= 200 && request.status < 300) {
        let string = request.responseText
        let object = JSON.parse(string)
      }
    } else if(request.status >= 400) {
      console.log('请求失败')
    }
  })
```

## AJAX 的所有功能
- 客户端的JS发起请求（浏览器上的）
- 服务端的JS发送响应（Node.js上的）

1. JS 可以设置任意请求 header 吗
  第一部分 request.open('get', '/xxx')
  第二部分 request.setRequestHeader('content-type','x-www-form-urlencoded')
  第四部分 request.send('a=1&b=2')

2. JS 可以获取任意响应 header 吗？
  第一部分 request.status / request.statusText
  第二部分 request.getResponseHeader() / request.getAllResponseHeaders()
  第四部分 request.responseText

## 使用JQuery的异步请求
```
JQuery.ajax({url, method, body, success, fail}) {
    let request = new XMLHttpRequest()
    request.open(method, url)
    request.onreadystatechange = () => {
        if (request.readyState === 4) {
            if(request.status >= 200 && request.status < 300) {
                success.call(undefined, request.responseText)
            } else if (request.status > 400) {
                fail.call(undefined, request)
            }
        }
    }
    request.send(body)
}
```

## 使用Promise规则封装 jQuery.ajax
```
jQuery.ajax = function({url, method}) {
  return new Promise(function(resolve, reject) {
    let request = new XMLHttpRequest()
    request.open(method, url)
    request.onreadystatechange = () => {
      if (request.readyState === 4) {
          if(request.status >= 200 && request.status < 300) {
              resolve.call(undefined, request.responseText)
          } else if (request.status > 400) {
              reject.call(undefined, request)
          }
      }
    }
    request.send()
  })
}
```