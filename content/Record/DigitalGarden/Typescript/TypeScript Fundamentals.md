---
title: TypeScript Fundamentals
tags: 
- TypeScript
- 基础
created: <% tp.date.now("YYYY-MM-DD") %>
Update: <%+ tp.file.last_modified_date("YYYY-MM-DD dddd HH:mm:ss") %>
---
#  <font color="#92d050">TypeScript Fundamentals</font>

---
## <font color="#7030a0">对象，数值和元组</font>
> 现在我们知道了如何键入简单的变量和函数，让我们做一些事情集合更有趣一点：在 JavaScript 中，这包括对象和数组。
### <font color="#ffc000">可选类型</font>
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
###  <font color="#00b050">索引签名和对象问答</font>

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
###  <font color="#dbeef3">数组和元组</font>
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

>可以为每一个变量分配类型我们知道数组中元素的数据类型都一般是相同的（any[] 类型的数组可
不同），如果存储的元素数据类型不同，则需要使用元组。组中允许存储不同类型的元素，元组可
以作为参数传递给函数。
>创建元组的语法格式如下：
>```ts
>Var tuple_name = [value 1, value 2, value 3,…value n]
>```
```
```

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

现在支持只读：

const numPair: readonly [number, number] = [4, 5]
```
---
##  [<font color="#205867">结构类型与标称类型</font>](https://www.typescript-training.com/course/fundamentals-v3/05-structural-vs-nominal-types/)
### 什么是类型检查？
类型检查可以被认为是一个尝试评估的任务 _兼容性_或_类型等效性_问题：

将类型系统分类为[静态](https://www.typescriptlang.org/docs/handbook/2/basic-types.html#static-type-checking)或动态与类型检查是否有关 **在编译时或运行时**执行。

> **TypeScript 的类型系统是静态的。**
[关于静态类型见检查(typescriptlang.org)](https://www.typescriptlang.org/docs/handbook/2/basic-types.html#static-type-checking)

>Java，C # C ++都属于这一类。请记住，推断仍然可以发生在静态类型系统中——TypeScript、Scala 和 Haskell 都有某种形式的静态类型检查。

**动态类型系统在运行时执行其“类型等效性”评估**。JavaScript， Python， Ruby，Perl 和 PHP 属于这一类。
### <font color="#b2a2c7">标称与结构</font>
**标称型系统都是关于名称的**。让我们看一个简单的 Java 示例：
```java
public class Car {

String make;

String model;

int make;

}

public class CarChecker {

// takes a `Car` argument, returns a `String`

public static String printCar(Car car) { }

}

Car myCar = new Car();

// TYPE CHECKING

// -------------

// Is `myCar` type-equivalent to

// what `checkCar` wants as an argument?

CarChecker.checkCar(myCar);
```

在上面的代码中，当考虑最后一行的类型等价问题时，重要的是类的实例是否**名为** 。`myCar``Car`

> 打字稿类型系统是结构化的

结构**类型系统都是关于结构或形状**的。让我们看一个 TypeScript 示例：

```ts
class Car {

make: string

model: string

year: number

isElectric: boolean

}

class Truck {

make: string

model: string

year: number

towingCapacity: number

}

const vehicle = {

make: "Honda",

model: "Accord",

year: 2017,

}

function printCar(car: {

make: string

model: string

year: number

}) {

console.log(`${car.make} ${car.model} (${car.year})`)

}

printCar(new Car()) // Fine

printCar(new Truck()) // Fine

printCar(vehicle) // Fine
```
[Try](https://www.typescriptlang.org/play/#code/PTAEAEGcBcCcEsDG0AKsD2AHApraBPASQDt5p4BDAG3gC8Lz1iAuUAM2smwChEqLIkUAGEKsUAG9uoUAFsKAa2ysYCYgHNpc9ABNsVFXHgat+bGNbEArrIBGuLfEgBRKtmQJErW+nRuKxNwAvty8-IKgACqwVogKklrySoZqmjKyuvopxmmgZhag1nYOMtDoAO45opgUiGT4ljb2sMGhiEwwoABu2AAWSG6gALwJ6YrKoABEABJMOhSTADSJmQZTAIKI7bA6S6bmsKwATAAMAIwA7Msh3GxWxMjwTKCYatCisAAUiAVSY8mgVQ5FZ6NZAkwyfKHQpNBxBACUo1A7WIkD82AAdFR0OpPgADAAkEh+sAxSWwQVARJJZNWlM+1LEGKhCLx8Na3FexneYk+xGw5REvPhiJAoAAYsYeFziDyvvzBdFYgpPiLQGLJfzOW8Pp8ev0+NhRWBNdggA)

该函数不关心它的参数来自哪个构造函数从，它只关心它是否有：`printCar`

-   类型的属性 `make``string`
-   类型的属性 `model``string`
-   类型的属性 `year``number`

如果传递给它的参数满足这些要求，则很高兴。`printCar`

### <font color="#548dd4">鸭子打字</font>

“鸭子打字”得名于“鸭子测试”。

> “如果它看起来像鸭子，像鸭子一样游泳，像鸭子一样嘎嘎叫，那么它很可能是一只鸭子”。

在实践中，这与结构类型非常相似，但“鸭子类型”通常是用于描述动态类型系统。
### “<font color="#548dd4">强”与“弱”类型</font>

这些术语虽然经常使用，但没有商定的技术定义。在 TypeScript 对于那些说“强”的人来说，真正意味着“静态”是很常见的。
## <font color="#d99694">并集和交集类型</font>

### 并集和交集类型，概念上

在概念上可以将联合和交集类型视为逻辑布尔运算符 （， ），因为它们与类型有关。让我们看看这组重叠的两个以项目集为例：`AND``OR`
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230301112440.png)
联合类型有一个[非常具体的技术定义]( https://en.wikipedia.org/wiki/Union_ (set_theory))，它来自集合论，但是对于**类型，将其视为 OR**是完全可以的。

在上图中，如果我们有一个类型，它将包括 整个图表上的每个项目。`Fruit OR Sour`

交集类型也有[名称 以及来自集合论的定义](https://en.wikipedia.org/wiki/Intersection_(set_theory))， 但对于**类型，**它们可以被认为是 AND。

在上面的同一张图中，如果我们想要的_水果也是酸的（_），我们最终会得到只得到. `Fruit AND Sour``{ Lemon, Lime, Grapefruit }`

### TypeScript 中的联合类型

TypeScript 中的联合类型可以使用 （pipe） 运算符进行描述。`|`

例如，如果我们有一个类型可以是两个字符串之一，或者，我们可以将其定义为 `"success"``"error"`

```ts
"success" | "error"
```

例如，如果从中选择的数字为 >= 0.5，或者如果 <=0.5，则该函数将返回。`flipCoin()``"heads"``(0, 1)``"tails"`
```ts
function flipCoin(): "heads" | "tails" {

if (Math.random() > 0.5) return "heads"

return "tails"

}

const outcome = flipCoin()

const outcome: "heads" | "tails"
```
让我们通过使用元组使它更有趣一些，元组的结构如下：

-   `[0]`要么或`"success"``"failure"`
-   `[1]`不同的东西，具体取决于在 中找到的值`[0]`
    
    -   `"success"`案例：一条联系方式：`{ name: string; email: string; }`
    -   `"error"`案例：一个实例`Error`

我们仍然会根据上面的 50/50 硬币翻转来决定这些事情中的哪一件实际发生。
```ts
function flipCoin(): "heads" | "tails" {

if (Math.random() > 0.5) return "heads"

return "tails"

}

function maybeGetUserInfo():

| ["error", Error]

| ["success", { name: string; email: string }] {

if (flipCoin() === "heads") {

return [

"success",

{ name: "Mike North", email: "mike@example.com" },

]

} else {

return [

"error",

new Error("The coin landed on TAILS :("),

]

}

}

const outcome = maybeGetUserInfo()

const outcome: ["error", Error] | ["success", { name: string; email: string; }]
```
这种类型明显更有趣。

### 使用联合类型

让我们继续上面的示例，并尝试使用 “结果”值。

首先，让我们解构元组，看看 TypeScript 对其成员的看法
```ts
const outcome = maybeGetUserInfo()

const [first, second] = outcome

first

const first: "error" | "success"

second

const second: Error | { name: string; email: string; }
```

```ad-tip
单击按钮并在 TS 操场中探索。 探索自动完成功能中针对每个选项的可用功能。`Try``first``second`
```