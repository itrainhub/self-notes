## Math 操作

 Js 中的 Math 操作方法虽然不多，但是应对 web 测大部分需求应该是hi足够了

 ### Math.trunc()

 该方法可以将小数位截断（cut off），不论是正数还是负数。

 ```js
  Math.trunc(80.9); // 80
  Math.trunc(80.8); // 80
  Math.trunc(80.8); // 80
  Math.trunc(80.6); // 80
  Math.trunc(80.5); // 80
  Math.trunc(80.4); // 80
  Math.trunc(80.3); // 80
  Math.trunc(80.2); // 80
  Math.trunc(80.1); // 80
  Math.trunc(-80.1); // -80
 ```

非小数的情况

```js
  Math.trunc('80.1'); // 80
  Math.trunc('hello'); // NaN
  Math.trunc(NaN); // NaN
  Math.trunc(undefined); // NaN
  Math.trunc(); // NaN
```

与之相对的， parseInt() 也能进行截断操作，但它的本质是将 string 类型的变量转为整数。因此如果是非 string 类型，会先调用 toString() 方法转为 stirng， 再执行 parse 操作，正因如此，会有一些边界极端情况，导致出错。
比如：

```js
  parseInt(100000000000000000000000.01) // 1
```

原因是 1000000000000000000000.1 调用 toString() 方法会转为 1e+13,导致整个操作不符合我们的预期。

浏览器支持情况：全线支持，除了 IE


#### 其他方法

1. 位操作符 ~~

    `~~80.6`

2. 位操作符 |

   `80.6 | 0`

3. toFixed()

   `Number((80.6).toFixed())`

