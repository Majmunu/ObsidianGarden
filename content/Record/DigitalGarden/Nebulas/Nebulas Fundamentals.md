---
UID: 20230301092237 
title: NebulasFundamentals
tags: 
- 基础
- Nebulas
aliases: 
source: 
cssclass: 
created: 2023-03-01
Update: NaN
---
# <font color="#7030a0">简介</font>

---
## 基本结构

```js
class FirstContract {
    //创建一个对象
    constructor() {

        //You need to ensure that each contract has a different __contractName

        this.__contractName = 'FirstContract'
        //使用LocalContractStorage.defineMapProperty方法定义size属性
        LocalContractStorage.defineMapProperty(this, 'authentication')

    }
       部署时只会执行一次的函数
    init (authentication) {
         //将value存储到链上
        this.authentication=authentication
    }
    accept() {

        // You can use the following code to get the transaction information

        Event.Trigger('transfer', {

            // The transaction hash

            from: Blockchain.transaction.from,

            // The transaction hash

            to: Blockchain.transaction.to,

            // The transaction value

            value: Blockchain.transaction.value,
            //
        })
    }

}
 

module.exports = FirstContract
```
## <font color="#3f3151"> 函数</font>
> 在 Nebulas 中为函数定义了两种可见性（Javascript 中中没有这种可见性）

-  `publick` 名称名称与正则表达式匹配的所有函数都是公共的
- `private` 名称的所有函数都是私有的，私有函数只能由公告函数调用 

## <font color="#3f3151">存储</font>
> 星云的智能合约环境内置了存储对象，可以存储数字、字符串和JavaScript对象。存储的数据只能在智能合约中使用。其他合约无法读取存储的数据。`LocalContractStorage`
### <font color="#b2a2c7">基本</font>
API 包括和，可用于存储、读取和删除数据。存储可以是数字、字符串、对象 `LocalContractStorage` `set` `get`  `del`

#### 存储数据：`LocalContractStorage`
```js
// store data. The data will be stored as JSON strings
LocalContractStorage.put(key, value);
// Or
LocalContractStorage.set(key, value);
```
#### 读取数据：`LocalContractStorage`
```js
// get the value from key
LocalContractStorage.get(key);
```
#### 删除数据：`LocalContractStorage`
```js
// delete data, data can not be read after deletion
LocalContractStorage.del(key);
// Or
LocalContractStorage.delete(key);
```
<font color="#ccc1d9">### 高深</font>
>绑定映射属性

```js
'use strict';

var SampleContract = function () {
    // Set `SampleContract`'s property to `userMap`. Map data then can be stored onto the chain using `userMap`
    LocalContractStorage.defineMapProperty(this, "userMap");

    // Set `SampleContract`'s property to `userBalanceMap`, and custom define the storing and serializtion reading functions.
    LocalContractStorage.defineMapProperty(this, "userBalanceMap", {
        stringify: function (obj) {
            return obj.toString();
        },
        parse: function (str) {
            return new BigNumber(str);
        }
    });

    // Set `SampleContract`'s properties to mulitple map batches
    LocalContractStorage.defineMapProperties(this,{
        key1Map: null,
        key2Map: null
    });
};

SampleContract.prototype = {
    init: function () {
    },
    testStorage: function () {
        // Store the data in userMap and serialize the data onto the chain
        this.userMap.set("robin","1");
        // Store the data into userBalanceMap and save the data onto the chain using a custom serialization function
        this.userBalanceMap.set("robin",new BigNumber(1));
    },
    testRead: function () {
        //Read and store data
        var balance = this.userBalanceMap.get("robin");
        this.key1Map.set("robin", balance.toString());
        this.key2Map.set("robin", balance.toString());
    }
};

module.exports = SampleContract;
```
## <font color="#ccc1d9">区块链</font>
> 该模块用于获取当前执行合约中的交易和区块。此外，NAS 可以从合同中转移并提供地址验证 `Blockchain`

Blockchain 具有两个属性
1. `block` 具有属性的合约执行的当前块
 -  _块时间戳 `timsetamp`
 - _块哈希 `hash`
 - _块高度 height
 2. 具有属性的合约执行的当前交易 `transaction`
 - _交易哈希 `hash`
 - _来自地址的交易 `from`
 - _交易到地址 `to`
 - _交易价值，合约使用的 BigNumber 对象 `value`
 - _交易随机数 `nonce`
 - _交易时间戳 `timestams`
 - _交易 gasLimit，一个用于合约的 BigNumber 对象 `gasLimit`
 
 并提供两种方法：`Blockchain`
 1. `transfer (address, value) ` 将 NAS 从从合同转到地址
 - 参数：接受 NAS 的星云地址 `address`
 - param：传输的值，一个 BigNumber 对象对象 `value`
 返回：传输成功传输失败 0 1
 2. `verifyAddress(address) address` 验证参数是否为有效的星云地址 
 返回： 地址有效地址地址无效 1 0
 
 
 
