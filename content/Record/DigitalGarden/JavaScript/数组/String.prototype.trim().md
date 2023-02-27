# String.prototype.trim()

**`trim()`** 方法从字符串的两端清除空格，返回一个新的字符串，而不修改原始字符串。此上下文中的空格是指所有的空白字符（空格、tab、不换行空格等）以及所有行终止符字符（如 LF、CR 等）。

## [尝试一下](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim#%E5%B0%9D%E8%AF%95%E4%B8%80%E4%B8%8B)

## [语法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim#%E8%AF%AD%E6%B3%95)

```
trim()
```

Copy to Clipboard

### [返回值](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim#%E8%BF%94%E5%9B%9E%E5%80%BC)

一个表示 `str` 去掉了开头和结尾的空白字符后的新字符串。

如果 `str` 的开头和结尾都没有空白字符，仍然会返回一个新字符串（本质上是 `str` 的副本），而不会抛出异常。

要返回一个只从一端删除空白字符的新字符串，可以使用 [`trimStart()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimStart) 或 [`trimEnd()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trimEnd)。

## [示例](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim#%E7%A4%BA%E4%BE%8B)

### [使用 `trim()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim#%E4%BD%BF%E7%94%A8_trim)

下面的例子显示小写字符串 `'foo'`：

```
const orig = "   foo  ";
console.log(orig.trim()); // 'foo'
```