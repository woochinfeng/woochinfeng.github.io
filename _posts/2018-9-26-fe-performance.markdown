---
layout: post
title: 前端页面性能类
date: 2018-9-26 00:00:00 +0300
description: fe-property # Add post description (optional)
img:   # Add image post (optional)
tags: [JS, HTTP] # add tag
---

### 前端页面性能类

### 提升页面性能的方法

- 1.资源压缩合并，减少HTTP请求

- 2.非核心代码异步加载
    - 异步加载的方式
        - 1）动态脚本加载（document.createElement）
        
        - 2）defer
        
        - 3）async
    - 异步加载的区别
        - 1）defer是在HTML解析完成之后才会执行，如果是多个，按照加载的顺序依次执行
        
        - 2）async是在加载完成之后立即执行，如果是多个，执行顺序和加载顺序无关

- 3.利用浏览器缓存
    - 缓存的分类
    - 缓存的原理

- 4.使用CDN（网络优化）

- 5.预解析DNS
    - `<meta http-equiv="x-dns-prefetch-control" content="on">`强制打开`https`协议`<a></a>`链接dns预解析
    
    - `<link rel="dns-prefetch" href="//host_name_to_prefetch.com"` 开启dns预解析


#### 浏览器缓存

- 1.缓存的分类
    - 1）强缓存
        - 从网上请求图片缓存到本地磁盘中，浏览器下次请求直接读取磁盘缓存（不询问请求直接拿取磁盘缓存）
        
        - **Expires** Expires:Thu,21 Jan 2017 23:39:02 GMT
        
            - Expires（过期时间），以key:value形式，value时间为绝对时间，服务器时间
        
        - **Cache-Control** Cache-Control:max-age=3600
            - 相对时间 在某时间内不询问直接拿取本地缓存
        
        - 如果服务器同时下发绝对时间与相对时间，则规定以后者为准

    - 2）协商缓存
        - 浏览器在本地发现副本，向服务器发送请求询问能不能使用
        - **Last-Modified If-Modified-Since** Lase-Modified:Wed,26 Jan 2017 00:35:11 GMT
        
            - Last-Modified为服务器下发时间，If-Modified-Since为请求时给服务器带的（两者所带时间相同）
        
        - **Etag If-None-Match**
            
            - Etag hash值