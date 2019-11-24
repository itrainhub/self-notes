## tree shake 摇树

  编译时将 首尾没有用到的import 链接去掉, 缩小代码体积，将没有使用到的包去除掉，虽然 tree shake 的概念 90 年代就已经有了，但用到 js 上只有在 ES6 之后，因为 ES6支持 静态包加载，虽然之前我们也有 commonJS 可以使用 require() 语法来加载其他文件，require() 是动态的，意味着，我们可以根据条件来判断是否加载包。

  在 webpack 的实现中，tree shake 不止能筛选出没有使用到函数方法，而且能筛选出没有使用到的键值。但 tree shake 并不能完全筛选出全部的无用代码。

  副作用：比如 polyfill, 它其实没有提供 export 的方法给其他方法，但我们整个项目都需要把它加载进来。

## Angular 中的摇树



# 参考链接
  * https://bitsofco.de/what-is-tree-shaking/
  * https://coryrylan.com/blog/tree-shakeable-providers-and-services-in-angular
