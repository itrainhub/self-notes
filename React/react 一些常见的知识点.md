
1. state 
  state 可以用来管理组件内的变量，当 state 的变量改变时，可以自动去触发页面渲染。
  在类组件中，可以在构造函数中将其初始化，之后每次更新时，需要调用 setState 方法去触发更新
  并且，由于更新后需要去更新虚拟dom，所以不能在 set 之后，立即去同步获取 state 值，有可能新值没有刷新
  setState 提供了回调函数供我们获取值

  ```js
    this.setState({
      ...this.state,
      value,
    }, () => {
      ...
    })
  ```

  如果遇到 setState 之后值不更新，尝试放到 setTimeout 中

  *** 注意点 ***

  1. 永远不要直接修改this.state，需要通过调用this.setState方法来替换你修改后的值。把this.state当做不可变数据来处理。
  2. setState()不会马上去改变this.state，而是会排队等待处理，所以当你调用setState()后访问this.state，有可能会返回旧的state。
  3. 当你调用setState()时，无法保证是同步执行的，因为为了保证性能可能会被批处理。
  4. setState()总是会触发render()进行重新渲染，除非在shouldComponentUpdata()控制了渲染逻辑。如果用了可变数据结构以及在shouldComponentUpdate()中并没有控制渲染逻辑，调用setState()将不会触发重新渲染渲

3. 虚拟 DOM， diff 算法


4. 函数组件中使用 React.memo() 导出
