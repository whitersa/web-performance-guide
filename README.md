# web-performance-guide

## Cache
+ 静态页面
这种方案适用于url请求的页面内容几乎不会变动，浏览器或者cdn分发服务可以长期缓存这份资源。只要不超过max-age期限，资源不会对服务器发起请求而是直接从缓存获取。
> Cache-Control: max-age=31536000