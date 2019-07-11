# Angular & Rxjs 最佳实践

  参考链接：

    https://blog.strongbrew.io/rxjs-best-practices-in-angular/#learning-how-to-think-reactive

### 一、不要手动 subscribe

  

### 二、使用 pipeable 操作符

  原因： 具有 treeshaking 特点, 导入依赖更加方便


### 三、 画 marble 图

```js
  // ---a--b--c--d---e...
  // ---a--b--c--d---e|
  // ---a--b--c--d---e#
```

* -(时间帧)
* a-z (values that are next'ed in the stream)
* | (means stream has completed)
* \# (error occurred)
* ^ (indicate where we start subscribing (only for hot streams))


### 四、 使用纯函数(pure function)

  pure function 的定义：

  * it doesn't mutate anything
  * it will always return same value based on the same parameters
  * it doesn't have any side effects. it can't mutate state outside of the function
