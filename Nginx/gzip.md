## nginx 下开启 Gzip 压缩

  gzip 可以对资源文件进行压缩，能够很大程度上减小前端文件的体积，减少首页加载时间

  如何在 nginx 下开启 gzip ？

  1. 明确当前使用的 nginx 的版本；不同的版本下略有不同。本篇文章的 version 为 1.10.x
  2. 配置项：
    ```
      gzip on;
      gzip_vary on;
      gzip_min_length 1024;
      gzip_proxied expired no-cache no-store private auth;
      gzip_types text/plain text/css text/xml text/javascript application/x-javascript application/xml;
      gzip_disable "MSIE [1-6]\.";
    ```

  各个字段的解释：
  
  gzip on: 开启 gzip
  gzip_vary on: 对压缩后的文件和未压缩的文件进行缓存
  gzip_min_length: 最小压缩体积，超过该体积才开启压缩
  gzip_poxied: 对客户端的请求进行压缩
  gzip_types: 开启压缩的文件类型，很多人觉得自己开了gzip但发现并没有压缩，原因可能就是类型没有添加；
  gzip_diable: 对 IE 1-6 版本不压缩

  3. 重启nginx: nginx -s reload


如何查看文件开启了压缩？

打开控制台，查看某个文件，看是否有 content-encoding: gzip 字段
另外，可以借用 [Google's PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights) 来对网页进行分析