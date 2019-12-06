# call,apply,bind 模拟实现

## call 的模拟实现
  准备材料：

  ```js
    var obj = {
      name: 'allen',
    }

    function test() {
      console.log(this.name)
    }
  ```

  思路：我们要实现：

    ```
      test.call(obj)
    ```

  如果将 `test` 作为 `obj` 的一个属性，就可以运行它

    ```js
        /** 简单版实现 */
        Function.prototype.call2 = function(context) {
          context.fn = this
          context.fn()
          delete context.fn
        }
    ```

  进阶版：可以接受多个参数. 思路：借助 arguments

  ```js
    Function.prototype.call2 = function(context) {
      var arg = Array.prototype.slice.call(arguments, 1)
      context.fn = this
      context.fn(...arg)
      delete context.fn
    }
  ```

  高级版：函数有返回体.

  ```js
    Function.prototype.call2 = function(context) {
      var arg = Array.prototype.slice.call(arguments, 1)
      context.fn = this
      const result = context.fn(...arg)
      delete context.fn
      return result
    }
  ```


## apply 的模拟实现

  和 `call` 类似，最终实现：

  ```js
    Function.prototype.apply2 = function(context) {
      var arg = Array.prototype.slice.call(arguments, 1)[0]
      context.fn = this
      const result = context.fn(...arg)
      delete context.fn
      return result
    }
  ```

## bind 的模拟实现

  代码实现：

  ```js
    var foo = {
      value: 1
    }
    function test() {
      console.log(this.value)
    }

    Function.prototype.bind2 = function (context) {
      const self = this
      return function () {
        return self.apply(context)
      }
    }

    var test2 = test.bind(foo)
    var test3 = test.bind2(foo)
    test3()
    test2()
  ```