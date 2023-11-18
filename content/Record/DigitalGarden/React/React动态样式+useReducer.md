---
UID: 20230314165403 
title: "React动态样式+useReducer"
tags: 
- 基础
- React
aliases: 
source: 
cssclass: 
created: 2023-03-14
Update: NaN
---

## ✍内容

## 动态样式
```jsx
className={`${classes.control} ${

            passwordIsValid === false ? classes.invalid : ""

          }`}
```

---
useReducer
 `useReducer` is a React Hook that lets you add a [reducer](https://beta.reactjs.org/learn/extracting-state-logic-into-a-reducer) to your component.
 
> const [state, dispatch] = useReducer(reducer, initialArg, init?)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230314165809.png)

### 使用方法
```js
import { useReducer } from 'react';  

function reducer(state, action) {  

// ...  

}  

function MyComponent() {  

const [state, dispatch] = useReducer(reducer, { age: 42 });  

// ...
```

`useReducer` returns an array with exactly two items:  
`useReducer` 返回一个正好包含两项的数组：

1.  The current state of this state variable, initially set to the initial state you provided.  
    此状态变量的当前状态，最初设置为您提供的初始状态。
2.  The `dispatch` function that lets you change it in response to interaction.  
    `dispatch` 函数，允许您更改它以响应交互。

To update what’s on the screen, call `dispatch` with an object representing what the user did, called an _action_:  
要更新屏幕上的内容，请调用 `dispatch` ，其中包含一个表示用户所做操作的对象，称为 action：
```js
function handleClick() {  

dispatch({ type: 'incremented_age' });  

}
```
React will pass the current state and the action to your reducer function. Your reducer will calculate and return the next state. React will store that next state, render your component with it, and update the UI.  
React 会将当前状态和动作传递给 reducer 函数。您的 Reducer 将计算并返回下一个状态。React 将存储下一个状态，用它呈现组件，并更新 UI。

### 减速器函数  

Then you need to fill in the code that will calculate and return the next state. By convention, it is common to write it as a [`switch` statement.](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch) For each `case` in the `switch`, you need to calculate and return some next state.  
然后您需要填写将计算并返回下一个状态的代码。按照惯例，通常将其编写为 `switch` 语句。对于 `switch` 中的每个 `case` ，您需要计算并返回某个下一个状态。
示例：
```js
function reducer(state, action) {  

switch (action.type) {  

case 'incremented_age': {  

return {  

name: state.name,  

age: state.age + 1  

};  

}  

case 'changed_name': {  

return {  

name: action.nextName,  

age: state.age  

};  

}  

}  

throw Error('Unknown action: ' + action.type);  

}
```
Actions can have any shape. By convention, it’s common to pass objects with a `type` property identifying the action. It should include the minimal necessary information that the reducer needs to compute the next state.  
动作可以有任何形状。按照约定，通常传递带有 `type` 属性的对象来标识操作。它应该包括归约器计算下一个状态所需的最少必要信息。
```js
function Form() {  

const [state, dispatch] = useReducer(reducer, { name: 'Taylor', age: 42 });  


function handleButtonClick() {  

dispatch({ type: 'incremented_age' });  

}   

function handleInputChange(e) {  

dispatch({  

type: 'changed_name',  

nextName: e.target.value  

});  

}  

// ...
```

>[!question] 
>State is read-only. Don’t modify any objects or arrays in state:  
>状态为只读。不要修改状态中的任何对象或数组：
> ```js
> function reducer(state, action) {  
>switch (action.type) {  
case 'incremented_age': {  
// 🚩 Don't mutate an object in state like this:  
state.age = state.age + 1;  
return state;  
}
>```
Instead, always return new objects from your reducer:  
相反，始终从缩减器返回新对象：
> ```js
> // ✅ Instead, return a new object  
return {  
...state,  
age: state.age + 1  
};
> ```

---
