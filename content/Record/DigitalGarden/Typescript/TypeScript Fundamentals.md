---
title: TypeScript Fundamentals
tags: 
- TypeScript
- 基础
created: <% tp.date.now("YYYY-MM-DD") %>
Update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
---
#  <font color="#92d050">类型类别  </font>
---
## <font color="#ffc000">可选类型</font>
> 我们可以使用以下运算符声明此属性是可选的：`?`

```js
function printCar(car: {

make: string

model: string

year: number

chargeVoltage?: number

}) {

let str = `${car.make} ${car.model} (${car.year})`

car.chargeVoltage

(property) chargeVoltage?: number | undefined

if (typeof car.chargeVoltage !== "undefined")

str += `// ${car.chargeVoltage}v`

(property) chargeVoltage?: number

console.log(str)

}
```

> ？可选不仅是简单的添加或者未定义，而是这个属性可以存在或者不存在


> 这将允许我们的函数工作，无论属性是否存在：`printCar``chargeVoltage`

```js
// Works

printCar({

make: "Honda",

model: "Accord",

year: 2017,

})

// Also works

printCar({

make: "Tesla",

model: "Model 3",

year: 2020,

chargeVoltage: 220,

})
```

---
##  <font color="#00b050">索引签名和对象问答</font>

有时我们需要表示**字典**的类型，其中一致类型的值可通过键检索
让我们考虑以下电话号码集合：
```js
const phones = {

home: { country: "+1", area: "211", number: "652-4515" },

work: { country: "+1", area: "670", number: "752-5856" },

fax: { country: "+1", area: "322", number: "525-4357" },

}
```
显然，我们似乎可以将电话号码存储在“密钥”下 - 在这种情况下，，以及我们选择的其他单词 - 并且每个电话号码由三个字符串组成。`home``office``fax`

我们可以使用所谓的_<span style="background:#b1ffff">索引签名</span>_来描述此值：
```TypeScript
const phones: {

  [k: string]: {

    country: string

    area: string

    number: string

  }

} = { home: { country: "+1", area: "211", number: "652-4515" },

  work: { country: "+1", area: "670", number: "752-5856" },

  fax: { country: "+1", area: "322", number: "525-4357" },}

  
  

// phones.fax.area

console.log(phones.fax.area)
```
---
## <font color="#dbeef3">数组和元组</font>
> 🐱‍🏍简单类型数组
```js
const fileExtensions = ["js", "ts"]

// const fileExtensions: string[]
声明初始化
var array_name[:datatype] = [val1,val2…valn]
实例
var numlist:number[] = [2,4,6,8]
或者 
var sites:string[] = new Array("Google","Runoob","Taobao","Facebook")
```
> 如果数组声明时未设置类型，则会被认为是 any 类型，在初始化时根据第一个元素的类型来推断数组的类型。

> 多维数组

```ts
var arr_name:datatype[][]=[ [val1,val2,val3],[v1,v2,v3] ]

```
>🐱‍👤 元组

>可以为每一个变量分配类型

局限性
```ts
const numPair: [number, number] = [4, 5, 6] //error

//Type '[number, number, number]' is not assignable to type '[number, number]'. Source has 3 element(s) but target allows only 2.
但是可以通过push和pop操控数组
const numPair: [number, number] = [4, 5]

numPair.push(6) // [4, 5, 6]

numPair.pop() // [4, 5]

numPair.pop() // [4]

numPair.pop() // []
```