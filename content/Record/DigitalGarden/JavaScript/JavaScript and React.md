---
UID: 20230410142525 
title: "JavaScript and React"
tags: JavaScript
aliases: 
source: 
cssclass: 
created: 2023-04-10
Update: NaN
---

##  Object.freeze() 
**`Object.freeze()`** 方法可以**冻结**一个对象。一个被冻结的对象再也不能被修改；冻结了一个对象则不能向这个对象添加新的属性，不能删除已有属性，不能修改该对象已有属性的可枚举性、可配置性、可写性，以及不能修改已有属性的值。此外，冻结一个对象后该对象的原型也不能被修改。`freeze()` 返回和传入的参数相同的对象。

>[!question]
>代理
>做验证

```js
const user = {

    firstName: 'John',

    lastName: 'Doe',

    age: 30,

    email: 'TEST@TEST.com',

    address: {

        street: '50 Main st',

        city: 'Boston',

        state: 'MA',

    },

};

const handler = {

    get: function (target, property) {

        console.log(123, target, 456, property);

  

        if (property === 'email') {

            console.log('My name is email');

        }

        return property in target ? target[property] : 'Not found';

    },

    set: function (target, property, value) {

        console.log(target, property, value);

    },

};

const proxy = new Proxy(user, handler);

proxy.email;

proxy.firstName;
```


