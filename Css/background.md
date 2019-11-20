# 背景

  ## 内容

    背景图片
    background-image: url

  ## 位置
    `background-position` 可以对背景图进行偏移操作，
    1. background-position: right 10px bottom 10px; 可以指定  left right bottom top 四个方向上的偏移值
    2. calc()
      `background-position: cal(100% - 20px) calc(100% - 10px);`
      计算也可以实现各个方向上的偏移




## 场景
  [css tricks](https://css-tricks.com/perfect-full-page-background-image/)
  全屏背景图，要求
   * 覆盖整个屏幕，没有空白
   * 必要时可以拉伸图片
   * 保留图片属性
   * 图片居中
   * 不产生滚动条
   * 尽可能浏览器适配
   
   ```
    html {
      background: url('https://static.infragistics.com/marketing/Website/Ignite-UI/images/marketing-sample-app-320.jpg?v=201709121100') no-repeat center center fixed;
      background-size: cover;
      height: 100%;
      overflow: hidden;
    }
   ```