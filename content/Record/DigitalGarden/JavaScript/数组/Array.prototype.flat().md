---
UID: 20230413135355 
title: "{{title}}"
tags: 
aliases: 
source: 
cssclass: 
created: 2023-04-13
Update: NaN
---

## ✍内容
# Array.prototype.flat()
**`flat()`** 方法创建一个新的数组，并根据指定深度递归地将所有子数组元素拼接到新的数组中。
```js
const arr1 = [0, 1, 2, [3, 4]];

console.log(arr1.flat());
// Expected output: Array [0, 1, 2, 3, 4]

const arr2 = [0, 1, 2, [[[3, 4]]]];

console.log(arr2.flat(2));
// Expected output: Array [0, 1, 2, Array [3, 4]]
```

# Array.prototype.flatMap()

```js
const arr1 = [1, 2, 3, 4];

arr1.map((x) => [x * 2]);
// [[2], [4], [6], [8]]

arr1.flatMap((x) => [x * 2]);
// [2, 4, 6, 8]

// 只有一层被展平
arr1.flatMap((x) => [[x * 2]]);
// [[2], [4], [6], [8]]
```


