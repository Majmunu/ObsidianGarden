---
UID: 20230317095415 
title: LocalContractStorage.defineProperties和 LocalContractStorage.defineMapProperty区别
tags: 
aliases: 
source: 
cssclass: 
created: 2023-03-17
Update: NaN
---

## ✍内容
`LocalContractStorage.defineProperties` 和 `LocalContractStorage.defineMapProperty` 都是在 Nebulas 区块链上使用 JavaScript 编写智能合约时的方法，但它们有一些不同之处。

`LocalContractStorage.defineProperties` 用于定义智能合约中的属性，这些属性可以是字符串、数字、数组或其他 JavaScript 数据类型。例如：
```js
LocalContractStorage.defineProperties(this, { 
name: null, 
age: 0, 
hobby: [] 
});
```

[新建应用1 (ivx.cn)](https://editor.ivx.cn/?#11221118)

通过这个方法定义的属性可以直接在智能合约代码中被访问和修改，就像普通的 JavaScript 对象一样，例如：

```js
this.name = "Alice";
this.age += 1; 
this.hobby.push("reading");
```

与此不同，`LocalContractStorage.defineMapProperty` 用于定义一个键值对存储映射，其中键和值都可以是字符串或数字。例如：
```js
LocalContractStorage.defineMapProperty(this, "myMap");
```

然后，您就可以使用 `myMap` 对象来存储和检索键值对，例如：

```js
this.myMap.put("key1", "value1"); var value = this.myMap.get("key1");
```

总的来说，`defineProperties` 用于定义存储普通数据类型的属性，而 `defineMapProperty` 则用于定义键值对存储映射。

