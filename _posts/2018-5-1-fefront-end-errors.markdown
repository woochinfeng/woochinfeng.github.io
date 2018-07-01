---
layout: post
title: 前端的错误监控
date: 2018-5-1 00:00:00 +0300
description: HTTP # Add post description (optional)
img:   # Add image post (optional)
tags: [JS, HTTP] # add tag
---

### 前端的错误监控

#### 前端错误的分类

- 即时运行错误：代码错误

    - 1）try..catch
    
    - 2）window.onerror（不能捕获资源加载错误）

- 资源加载错误（不会冒泡）

    - 1）object.onerror
    
    - 2）performance.getEntries()
        - 返回的是一个数组，可以用`performance.getEntries().forEache(item=>{console.log(item.name)})`遍历出资源都是成功加载的 ，对比其它的资 源集合，减去遍历出的资源剩下的就是没加载成功的资源
    
    - 3）Error事件捕获
        ```
        window.addEventListener('error',function(e) {
            console.log('捕获' + e)
        },true)
        //必须是true捕获，false是冒泡无法获得error
        ```

**延伸：跨域的js运行错误跨域捕获吗，错误提示什么，应该怎么处理？**
跨域的js错误信息返回为`Script error`,但是却不能显示出错文件和出错行号或出错详情等，需要做处理

- 1.在script标签增加`crossorigin`属性（客户端）

- 2.设置js资源响应`Access-Control-Allow-Origin:*`（服务端）


#### 错误的捕获方式

#### 上报错误的基本原理

- 1.采用Ajax通信的方式上报

- 2.利用Image对象上报
    ```
    (new Image().src = 'http://www.xxx.com/test?=test')
    ```

