node note
===========================

> #### 1. next()与next(error)
next()函数通知下一个中间件处理请求，而next(error)是通知错误中间件去处理错误请求，就像promise的resolve(result)和reject(error)这两个是不一样的。在express里，app.js中有默认的404捕捉和错误捕捉，可以直接统一定义错误值。
