# web-performance-guide

## Cache
+ 静态页面

    这种方案适用于url请求的页面内容几乎不会变动，浏览器或者cdn分发服务可以长期缓存这份资源。只要不超过max-age期限，资源不会对服务器发起请求而是直接从缓存获取。

    > Cache-Control: max-age=31536000 // 31536000是一年(365天)的秒数

    通常来讲请求的资源文件名会包含一个独一无二的字符串，可能是版本信息、修改日期、或者基于内容得出的hash值。

+ 非静态页面
  
    针对这些页面内容很可能发生变化的情况，例如博客文章等，必须要向服务器确认是否可以采用本地缓存。
    本地会以缓存资源的修改时间向服务器询问，如果确认没有发生更改则可以继续使用缓存，否则就要从服务器拉取新的资源内容。
    
    > Cache-Control: no-cache 
    // no-cache不代表不使用缓存，而是要先向服务器询问再决定是否使用缓存
    // no-store则告诉浏览器永远不要缓存
    // must-revalidate也不代表必须要重新验证，而是在超过max-age以后必须要重新 验证
