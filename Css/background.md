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

  ## gradients 渐进梯度
    `background: linear-gradient(to left, red, blue);` 表示 从右到左，由红到蓝线性渐进变化
    TODO: radial-gradient

  ## background-size
    * contain 会让整个图片完整显示出来，但如果container 的宽度或者高度偏小，会对图片做相应的伸缩 
    * cover 会等比缩放图拍呢，使其能够填充整个container，图片不会失真

  ## background-origin
    原点盒模型
    padding-box (默认)
    border-box
    content-box

  ## background-attachment
    * scroll 滚动(默认)
    * fixed 固定
    * local


  ## background-clip
    明确背景绘制区域
    border-box(默认)
    padding-box
    content-box
    clip 和 origin 的差异，见 [stackOverFlow](https://stackoverflow.com/questions/12753900/is-there-any-difference-between-background-clip-and-background-origin)

    origin 是明确背景应该放置区域的起点
    clip 是明确哪部分背景应该显示





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