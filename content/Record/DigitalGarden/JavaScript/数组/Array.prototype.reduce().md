
---
title: "Array.prototype.reduce()"
UID: <% tp.date.now("YYYYMMDDHHmmss") %> 
tags: 
- 数组方法
aliases: 
source: 
cssclass: 
created: <% tp.date.now("YYYY-MM-DD") %>
Update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
---

# [Array.prototype.reduce() - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

**`reduce()`** 方法对数组中的每个元素按序执行一个由您提供的 **reducer** 函数，每一次运行 **reducer** 会将先前元素的计算结果作为参数传入，最后将其结果汇总为单个返回值。

第一次执行回调函数时，不存在“上一次的计算结果”。如果需要回调函数从数组索引为 0 的元素开始执行，则需要传递初始值。否则，数组索引为 0 的元素将被作为初始值 _initialValue_，迭代器将从第二个元素开始执行（索引为 1 而不是 0）。

下面的例子能够帮助你理解 `reduce()` 的用处——计算数组所有元素的总和：
## [尝试一下](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce#%E5%B0%9D%E8%AF%95%E4%B8%80%E4%B8%8B)
>常见用法求和
```js
let sum = [0, 1, 2, 3].reduce(function (previousValue, currentValue) {
  return previousValue + currentValue
}, 0)
// sum is 6

**reducer** 逐个遍历数组元素，每一步都将当前元素的值与上一步的计算结果相加（上一步的计算结果是当前元素之前所有元素的总和）——直到没有更多的元素被相加。
```

## [语法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#%E8%AF%AD%E6%B3%95)

```
// 箭头函数
reduce((previousValue, currentValue) => { /* … */ } )
reduce((previousValue, currentValue, currentIndex) => { /* … */ } )
reduce((previousValue, currentValue, currentIndex, array) => { /* … */ } )

reduce((previousValue, currentValue) => { /* … */ } , initialValue)
reduce((previousValue, currentValue, currentIndex) => { /* … */ } , initialValue)
reduce((previousValue, currentValue, currentIndex, array) => { /* … */ }, initialValue)

// 回调函数
reduce(callbackFn)
reduce(callbackFn, initialValue)

// 内联回调函数
reduce(function(previousValue, currentValue) { /* … */ })
reduce(function(previousValue, currentValue, currentIndex) { /* … */ })
reduce(function(previousValue, currentValue, currentIndex, array) { /* … */ })

reduce(function(previousValue, currentValue) { /* … */ }, initialValue)
reduce(function(previousValue, currentValue, currentIndex) { /* … */ }, initialValue)
reduce(function(previousValue, currentValue, currentIndex, array) { /* … */ }, initialValue)
```

### [参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce#%E5%8F%82%E6%95%B0)
`callbackFn`

一个“reducer”函数，包含四个参数：

-   `previousValue`：上一次调用 `callbackFn` 时的返回值。在第一次调用时，若指定了初始值 `initialValue`，其值则为 `initialValue`，否则为数组索引为 0 的元素 `array[0]`。
-   `currentValue`：数组中正在处理的元素。在第一次调用时，若指定了初始值 `initialValue`，其值则为数组索引为 0 的元素 `array[0]`，否则为 `array[1]`。
-   `currentIndex`：数组中正在处理的元素的索引。若指定了初始值 `initialValue`，则起始索引号为 0，否则从索引 1 起始。
-   `array`：用于遍历的数组。

`initialValue` 可选

作为第一次调用 `callback` 函数时参数 _previousValue_ 的值。若指定了初始值 `initialValue`，则 `currentValue` 则将使用数组第一个元素；否则 `previousValue` 将使用数组第一个元素，而 `currentValue` 将使用数组第二个元素
>>>>>>> 7cdf15a65fae3d3a232b5f58f142594ab9aa4eea
