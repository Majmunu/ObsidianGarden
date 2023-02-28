---
UID: 20230228164059 
title: Introduction to Node.js
tags: 
- Node
- 基础
aliases: 
source: 
cssclass: 
created: 2023-02-28
Update: NaN
---

#  Introduction to Node.js

## <font color="#205867">基本组件</font>

### <font color="#31859b">全局</font>  
[Node.js 全局对象](https://www.runoob.com/nodejs/nodejs-global-object.html)
> 在浏览器 JavaScript 中，通常 window 是全局对象，而 Node.js 中的全局对象是 global，所有全局变量（除了 global 本身以外）都是 global 对象的属性。在 Node.js 我们可以直接访问到 global 的属性，而不需要在应用中包含它。

#### __filename

>**__filename** 表示当前正在执行的脚本的文件名。它将输出文件所在位置的绝对路径，且和命令行参数所指定的文件名不一定相同。如果在模块中，返回的值是模块文件的路径。

#### __dirname

>**__dirname** 表示当前执行脚本所在的目录。

### <font color="#31859b">模块</font>
> 
