面向切片编程

```js
  Function.prototype.before = function (beforeFn) {
    var __self = this
    return function () {
      beforeFn.apply(this, arguments)
      return __self.apply(this, arguments)
    }
  }

  Function.prototype.after = function (afterFn) {
    var __self = this
    return function () {
      __self.apply(this, arguments)
      return afterFn.apply(this, arguments)
    }
  }
```