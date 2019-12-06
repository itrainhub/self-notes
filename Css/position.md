定位

常见:
1. static - 默认位置，按文档流布局，top，right,bottom,left, z-index 都不起作用
2. relative - 相对位置，相对正常位置布局，top,right,bottom,left, z-index 等值可以起到作用
3. fixed - 固定位置，相对于 window 定位
4. absolute - 绝对位置, 相对于第一个非 static 定位的父亲元素布局

不常见:
1. initial - set this property to its default value
2. inherit - 从 parent element 中继承
3. sticky - behaves like position: static within its parent until a given offset threshold is reached, then it acts as position: fixed
4. unset - initial 和 inherit 的结合


relative, absolute, fixed 布局元素可以通过 z-index 来调整层叠

### 绝对布局

  脱离文档流，相对它的 container 进行定位

## 固定布局
  相对于浏览器进行布局，应用场景：当页面滚动到底部，但顶部的内容依然显示