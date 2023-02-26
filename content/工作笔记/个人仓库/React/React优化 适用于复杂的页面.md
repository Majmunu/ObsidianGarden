# React如何工作
```ad-note
title:React如何工作
![[Pasted image 20230215162902.png]]
 > `函数的变化不一定会引入页面的渲染 `
 > 当组件props state content发生变化时，组件会重新渲染，然后执行函数
 
```

# 问题

```JSX
// DemoOutput.jsx
function DemoOutput(props) {

    console.log('DemoOutput Running');

  return (

    <div>{props.show?<h1>This is DemoOutput</h1>:''}</div>

  )

}

export default DemoOutput;
```

```jsx
//app.jsx
function App() {

  console.log('APP RUNNING');

  const [showText, setShowText] = useState(false)

  const  isShowText = () => {

   setShowText((showText)=> !showText)

  }

  return (

    <div className="App">

     <h1>Hi there</h1>

     <DemoOutput show={false}/>

     <Button type='primary' onClick={isShowText}>SWITCH</Button>

    </div>

  );
```

> `问题：`当一个页面内部组件发生变化时，整个页面都会被重新渲染，当某个组件不是一直显示，而是条件显示时还是会被重新渲染一次（并不是渲染真实DOM，并没有改变页面结构）那么当我们嵌套组件时，只要一个组件变化或者组件的组件变化就会引起整个页面的重新渲染（diff），这样会很浪费资源

`那么我们如何让React只对更改的组件进行渲染？`

![[Pasted image 20230215172929.png]]
# 解决方案 应用场景
> 我们可以给条件显示的组件加上 React.MEMO（仅适用于函数组件）
>比较耗时的函数或者组件

```jsx
function DemoOutput(props) {

  console.log("DemoOutput Running");

  return <h1>{props.show ? <h1>This is DemoOutput</h1> : ""}</h1>;

}

export default React.memo(DemoOutput); 
```
## 代价
>  这种优化是有代价的。 这里的memo方法告诉 React每当应用程序组件发生变化时， 它应该转到此处的此组件,并将新的道具值与以前的道具值进行比较， 因此 React 需要做两件事。它需要存储以前的属性值， 它需要进行比较。 当然，这也有自己的性能成本。因此，它在很大程度上取决于 在要应用此功能的组件上 是否值得因为您正在交易性能成本 重新评估组件 对于比较道具的性能成本。而且不可能说哪个成本更高 因为这取决于你拥有的道具数量 以及组件的复杂性以及组件具有的子组件数。 当然，React.memo可以是一个很好的工具,如果你有一个巨大的组件树有很多子组件。 在组件树中的高级别，你可以避免不必要的重新渲染周期 组件树的整个分支。 就像在这种情况下，通过避免重新评估此DemOutput组件演示输出， 我们也会自动避免组件的组件的重新评估。即使我们没有在那里使用 React Demo。 只是因为我们切断了整个分支，所以组件树的整个分支。 那是一些东西 React.memo绝对值得。 另一方面，如果您有一个组件 你知道它会改变的地方 或者它的道具值会改变，几乎每次重新评估 无论如何，父组件， 那么 React.memo 没有多大意义，如果结果是组件无论如何都应该重新渲染， 这取决于你的应用大小。 对于小应用、小型组件树等，对于某些页面，添加这个可能根本不值得。但是对于大型应用程序 避免不必要的重新评估这很可能是值得的。

## useMemo

### 应用场景 
 > 作为父组件的方法 需要传到子组件里面去，会引起子组件的重新render

## useCallback
当我们知道这个函数应该永远不会改变，可以使用useCallback()来存储

