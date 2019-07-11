# http 拦截器可以在 请求和后端之间充当一个中间人的角色，对发送前和获取后进行统一处理

场景有：

  * 控制 URL
  * 请求进度显示
  * 统一错误捕捉和处理
  * 统一的请求体
  * 统一的 token 管理刷新
  * 
  
注意事项：

  1. 可以有多个 interceptor, 并且它们会按照注册顺序依次执行； 如果你想动态地控制部分拦截器起作用，需要在特定的拦截器中做处理；
  2. 拦截器可以同时处理 req 和 res;
  3. 


各个场景应用使用心得：

### 1. URL

  我们可以在拦截器中对请求的 url 做校验，比如把 `http` 全量替换成 `https`, 以及检查它有没有加 `http://` OR `https://`, 如果没有的话加补充

  ```typescript
    const httpsReq = req.clone({
      url: req.url.replace("http://", "https://")
    })
  ```


### 2. 请求进度显示

  我们有时需要显示请求的进度，同样可以在拦截器中做到

  ```typescript
    const loaderService = this.injector.get(LoaderService)

    loaderService.show()

    return next.hande(req).pipe(
      delay(500),
      finalize(() => loaderService.hide())
    )
  ```


  问题： 同时发多个请求怎么处理？请求取消了怎么处理？


  