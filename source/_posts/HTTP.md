---
title: HTTP
date: 2018-12-07 17:58:00
tags:
---


## 本文主要包括以下内容：

1. HTTP是什么？

2. HTTP 请求包括哪些部分？

3. HTTP 响应包括哪些部分？

4. 如何用Chrome开发者工具查看 HTTP 请求及请求的内容？

5. 如何使用 curl 命令？

### 1 HTTP是什么?

- `HTTP` 全称：HyperText Transfer Protocol，即超文本传输协议[HTTP](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE)的作用。

- `HTTP作用` : 指导浏览器和服务器之间进行沟通。

### 2 HTTP 请求包括哪些部分？

- HTTP请求主要包括四部分（第四部分可以为空），主要格式如下：

> 1 动词 路径 协议/版本
> 2 Key1: value1
> 2 Key2: value2
> 2 Key3: value3
> 2 Content-Type: application/x-www-form-urlencoded
> 2 Host: www.baidu.com
> 2 User-Agent: curl/7.54.0
> 3 
> 4 要上传的数据 

### 3、HTTP 响应包括哪些部分？

- HTTP响应主要包括四部分（第四部分可以为空），主要格式如下：

> 1 协议/版本号 状态码 状态解释
> 2 Key1: value1
> 2 Key2: value2
> 2 Content-Length: 17931
> 2 Content-Type: text/html
> 3
> 4 要下载的内容

### 4、如何用Chrome开发者工具查看 HTTP 请求及响应的内容？

- eg：用**Chrome**发请求
1. 打开 Network
2. 地址栏输入网址
3. 在 Network 点击，查看 request，点击「view source」
4. 点击「view source」可查看请求的前三部分
5. 如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到

- 用**Chrome**查看响应
1. 打开 Network
2. 输入网址
3. 选中第一个响应
4. 查看 Response Headers，点击「view source」
5. 查看响应的前两部分
6. 查看 Response 或者 Preview，你会看到响应的第 4 部分

![http图示](../public/images/http.png)

### 5、如何使用 curl 命令？
- `Curl`是Linux下一个很强大的http命令行工具。
- curl的基本用途：创造一个请求，并得到响应，主要如下图：
> curl -s -v -H "Nola: xxx" -- "https://www.baidu.com"
> 请求内容：
> GET / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.0
> Accept: */*
> Nola: xxx



> curl -X POST -s -v -H "Nola: xxx" -- "https://www.baidu.com"
> 请求内容：
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.0
> Accept: */*
> Nola: xxx



> curl -X POST -d "1234567890" -s -v -H "Nola: xxx" -- "https://www.baidu.com"
> 请求内容：
> POST / HTTP/1.1
> Host: www.baidu.com
> User-Agent: curl/7.54.0
> Accept: */*
> Nola: xxx
> Content-Length: 10
> Content-Type: application/x-www-form-urlencoded