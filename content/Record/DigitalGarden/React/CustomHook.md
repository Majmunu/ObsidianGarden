# 钩子使用规则
- 只能在组件函数内部或者其他钩子内部使用![](https://raw.githubusercontent.com/Majmunu/Gallery-Img/main/202311182306269.png)
- 不能在嵌套函数中使用![](https://raw.githubusercontent.com/Majmunu/Gallery-Img/main/202311182308814.png)
# 为什么要自定义钩子
- 复用
# 什么情况下可以自定义钩子
 - 不返回jsx组件，多次复用
 - 只能在组件内部完成
# 创建自定义钩子
> 以 use开头的函数被React默认识别为钩子函数
# 使用自定义钩子