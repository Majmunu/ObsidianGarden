# Array.prototype.includes()

**`includes()`** 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 `true`，否则返回 `false`。

## [尝试一下](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E5%B0%9D%E8%AF%95%E4%B8%80%E4%B8%8B)

## [语法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E8%AF%AD%E6%B3%95)

```
includes(searchElement)
includes(searchElement, fromIndex)
```

Copy to Clipboard

### [参数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E5%8F%82%E6%95%B0)

`searchElement`

需要查找的元素值。

**备注：** 使用 `includes()` 比较字符串和字符时是区分大小写的。

`fromIndex` 可选

从`fromIndex` 索引处开始查找 `searchElement`。如果为负值，则按升序从 `array.length + fromIndex` 的索引开始搜（即使从末尾开始往前跳 `fromIndex` 的绝对值个索引，然后往后搜寻）。默认为 0。

### [返回值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E8%BF%94%E5%9B%9E%E5%80%BC)

返回一个布尔值 [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean) 。 如果在数组中（或 `fromIndex` 指定的范围中）找到了 `searchElement`，则返回 `true`，否则返回 `false`。

0 的值将全部视为相等，与符号无关（即 -0 与 0 和 +0 相等），但 `false` 不被认为与 0 相等。

**备注：** 技术上来讲，`includes()` 使用 [`零值相等`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Equality_comparisons_and_sameness#%E9%9B%B6%E5%80%BC%E7%9B%B8%E7%AD%89) 算法来确定是否找到给定的元素。

## [示例](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E7%A4%BA%E4%BE%8B)

```
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

Copy to Clipboard

### [fromIndex 大于等于数组长度](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#fromindex_%E5%A4%A7%E4%BA%8E%E7%AD%89%E4%BA%8E%E6%95%B0%E7%BB%84%E9%95%BF%E5%BA%A6)

如果 `fromIndex` 大于等于数组的长度，则将直接返回 `false`，且不搜索该数组。

```
var arr = ['a', 'b', 'c'];

arr.includes('c', 3);   // false
arr.includes('c', 100); // false
```

Copy to Clipboard

### [计算出的索引小于 0](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E8%AE%A1%E7%AE%97%E5%87%BA%E7%9A%84%E7%B4%A2%E5%BC%95%E5%B0%8F%E4%BA%8E_0)

如果 `fromIndex` 为负值，计算出的索引将作为开始搜索`searchElement`的位置。如果计算出的索引小于 0，则整个数组都会被搜索。

```
// array length is 3
// fromIndex is -100
// computed index is 3 + (-100) = -97

var arr = ['a', 'b', 'c'];

arr.includes('a', -100); // true
arr.includes('b', -100); // true
arr.includes('c', -100); // true
arr.includes('a', -2); // false
```

Copy to Clipboard

### [作为通用方法的 includes()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E4%BD%9C%E4%B8%BA%E9%80%9A%E7%94%A8%E6%96%B9%E6%B3%95%E7%9A%84_includes)

`includes()` 方法有意设计为通用方法。它不要求`this`值是数组对象，所以它可以被用于其他类型的对象 (比如类数组对象)。下面的例子展示了 在函数的 [arguments](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments) 对象上调用的 `includes()` 方法。

```
(function() {
  console.log([].includes.call(arguments, 'a')); // true
  console.log([].includes.call(arguments, 'd')); // false
})('a','b','c');
```

Copy to Clipboard

## [规范](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#%E8%A7%84%E8%8C%83)