## Rxjs 操作符备忘

### tap
  只做一些操作，不会影响整体流

```js
  http$.pipe(
    tap(() => console.log('http request'))
  )
```

### Map

  * map
  * mergeMap
  * switchMap
  * concatMap
  
 `*Map` series contain most of rxjs situations.

`Map` 最简单， map a plain value like 1 to another value like 10, 其他的 `*Map` 则不同，它们会 map a value into an Observable, they can help us avoid nested subscriptions.


mergeMap: This operator is best used when you wish to flatten an inner observable but want to manually control the number of inner subscriptions.

### shareDelay
  后续的监听也能得到值

### scan
  相当于 Array 中的 reduce

### pluck 
  选择 source 中的某个属性

### from
  turn an array, promise, or iterable into an observable