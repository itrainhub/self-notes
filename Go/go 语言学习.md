
1. 数组
  `s := []int{1,2,3,4}`

2. 切片
  开区间，包含第一个，不包含第二个坐标

  ```go
    s = s[0: 4]
  ```

3. 常用的方法

  `len()` 获取切片的长度，它所包含的元素个数
  `cap()` 获取切片的容量，从它的第一个元素开始数，到其底层数组末尾的个数


4. 循环
  for range

  ```go
    var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}
    for index, value := range pow {

    }
  ```

5. defer 
  函数执行完毕后执行，具有以下特点：
    1. 定义时 evaluated
    2. FILO 先进后出

6. panic & recover