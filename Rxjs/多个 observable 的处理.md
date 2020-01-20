我们经常会遇到需要处理多个 observable 的场景，并根据它们的值的不同，做出不同的策略。尽管 `rxjs` 提供了多个 `operators` 来 handle， 但中间还是存在挺多需要注意的点。

支持 combination 的操作符:

  * zip
  * forkJoin
  * combineLatest
  * race
  * concat
  ... 

我们依次来看一下：

  ####  `zip: zip(observables: *): Observable`
  zip 可以将多个 obs 绑定，当所有的 observables ***emit***，会以 array 的形式 emit.
  (请注意，当zip中包含了 `Subject`, Subject 必须 emit 之后，才能触发 zip，并且触发一次之后，不能再触发第二次)

  ```js
    const sourceOne = of("hello")
    const sourceTwo = of("world")
    const sourceSubject = new Subject()

    zip(sourceOne, sourceTwo, sourceSubject.asObservable()).subscribe(console.log)
    sourceSubject.next('!')
    sourceSubject.next('.')

    /** output */
    // ['hello', 'world', '!]
  ```

  #### `forkJoin: forkJoin(...args, selector: function): Observable`
  当所有的 obs ***complete***, 输出所有的 obs 的最新值.

  (请注意： Subject，BehaviorSubject 等在 next 之后，需要显示地 complete 才能触发上面说的 emit, 而 Subject complete 之后，再 next 之后不能再更新值了，这有违 Subject 的初衷——)

  ```js
    const sourceOne = of("hello")
    const sourceTwo = of("world")
    const sourceSubject = new Subject()

    forkJoin(sourceOne, sourceTwo, sourceSubject.asObservable()).subscribe(console.log)
    sourceSubject.next('!')
    sourceSubject.complete()
    sourceSubject.next('.')
    sourceSubject.complete()

    /** output */
    // ['hello', 'world', '!']
  ```

  #### `combineLatest`

  combineLatest 也可以将多个 obs 绑定，并且当它们中的任意一个 ***emit***，都会输出最新值, 对于需要多次更新的情况，combineLatest 可以解决 zip 和 forkJoin 的尴尬

  ```js
  /** combineLatest */
  const sourceOne = new BehaviorSubject('Hello');
  const sourceTwo = of('World!');
  const sourceThree = of('Goodbye');
  const sourceFour = of('World!');
  //wait until all observables have emitted a value then emit all as an array
  const example = combineLatest(
    sourceOne,
    sourceTwo,
    sourceThree,
    sourceFour
  );

  //output: ["Hello", "World!", "Goodbye", "World!"]
  const subscribe = example.subscribe(val => console.log(val));
  sourceOne.next('xxxx')

  /** output */
  /**
    ["Hello", "World!", "Goodbye", "World!"]
    ["xxxx", "World!", "Goodbye", "World!"]
  */
  ```
  ####  `race`
  在一组 obs 中输出 最先输出的那个, 但只要有一个 throw error，结果不执行

  ```js
  const sourceOne = of(1).pipe(delay(3000))
  const sourceTwo = interval(2000).pipe(mapTo(2))
  race(sourceOne, sourceTwo).subscribe(console.log)
  // 输出: 2

  // 抛出错误，不执行
  const sourceOne = of(1).pipe(delay(3000))
  const sourceTwo = interval(2000).pipe(mapTo(2)).pipe(map(_ => {throw 'ee'}))
  race(sourceOne, sourceTwo).subscribe(console.log)

  ```

  #### `concat`
    顺序执行，等上一个执行结束后，下一个才会执行, 如果某个 throw error，剩下的都不会执行, 如果一个 obs 没有complete ，那么它剩下的都不会执行, 比如 `interval`, 比如 Subject() 的 next(), 无效，必须手动 complete()

    ```js
      concat(
        of(1,2,3),
        of(4,5,6),
        of(7,8,9),
      ).subscribe(console.log)
      // 输出：123456789

      // 抛出错误，不执行
      concat(
        of(1,2,3),
        of(4,5,6).pipe(map(_ => {throw 'e'})),
        of(7,8,9),
      ).subscribe(console.log)
      // 输出 123
    ```

  #### `merge`

    将多个 observables 合并为一个 observable
    它和 `concat` 就一点不同， concat 输出是有序的，而 merge 的输出是依赖于执行的顺序，谁先执行完就先走 subscribe 的逻辑
    但是，它的参数顺序也很重要, 它会依次执行


  #### `startWith`

  #### `endWith`