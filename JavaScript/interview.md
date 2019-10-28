一面；
CSS编程，用纯CSS实现一个自适应正方形，并且水平垂直居中。
js Function.prototype.bind实现
跨域问题，遇到302的情况。
HTTP缓存，304和200(from cache)
redux
浏览器并发限制，如何解决
还有一段JS代码纠错题 主要是考察JS闭包，ES6新特性的
bind 函数的实现，两个数组的有序归并；setTimeout 的相关知识点
二面
1. 询问以前项目，对以前项目需要的进行讨论
2. CSS题，实现3栏布局，左右两个占100px，中间的自适应
3. CSS选择器优先级
4. 将连字符格式的字符串转化为驼峰式的字符串
5. 从1000万个数里查出前10个

头条效率工程前端  
写一个开源防抖
混合集成函数
输入输出


一面：
笔试

body视口下块级元素垂直水平居中
----可以分为固定高度和不固定高度实现。

if([]==false){console.log(1)};
if({}==false){console.log(2)};
if([]){console.log(3)}
if([1]==[1]){console.log(4)}
----1，3

修改错误
name = ‘string’;
for (var i = 0; i < 4; i++) {
  setTimeout(function() {
    console.log(i);
    console.log(this.name);
  }, 1000 * i);
}
要求输出
string
0
string
1
String
2
String
3

arguments变成数组

算法：
从一无序数组中取出n个数和为sum（如果n为2，时间复杂度是多少）
n=2时，时间复杂度o(n2)
方法一：暴力循环
方法二：动态规划.....

笔试题
css 三栏布局
== 号的运用
纠错题，闭包相关
arguments 转数组
防抖函数实现
从数组中选 k 个数和为 sum
bind 函数实现
将连字符串转为驼峰字符串

面试题
问项目遇到什么问题，如何解决
CSS选择器优先级
flexbox 布局
安全相关
HTTP缓存
为什么使用 react
webpack 使用
前端项目搭建过程和问题
