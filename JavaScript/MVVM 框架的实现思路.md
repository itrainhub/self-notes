# MVVM 的实现思路

1. MVVM 是 MVC（Model, View, Control）、MVP(Model, View, Present) 的优化版本，
  即 Model，View, View-Model

2. MVVM 中的 VM 的核心思想是双向数据绑定

3. 实现双向数据绑定的思路有：

 *数据劫持（Vue）
 *发布-订阅模式（Knockout，Backbone）
 *脏值检查（Angular）

数据劫持：
  通过 `Object.defineProperty` 方法进行

  ```js
    var foo = {
      name: 'vue',
      version: '1.0'
    }

    function observe(data) {
      if (!data || typeof data !== 'object') {
        return
      }

      Object.keys(data).forEach(key => defineReactive(data, key, data[key]))
    }

    function defineReactive(obj, key, value) {

      Object.defineProperty(obj, key, {
        get: function reactiveGetter() {
          return value
        },
        set: function reactiveSetter(newVal => {
          if (value === newVal) {return}
          value = newVal
          console.log(`监听成功：${value} --> ${newVal}`)
        })
      })
    }
  ```