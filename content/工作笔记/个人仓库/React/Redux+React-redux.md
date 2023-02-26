# Redux
`api`
## createStore
[createStore(reducer, [preloadedState], [enhancer])](https://cn.redux.js.org/api/createstore)

##  combineReducers

  [combineReducers(reducers)](https://cn.redux.js.org/api/combinereducers)
##  applyMiddleware
[applyMiddleware(...middlewares)](https://cn.redux.js.org/api/applymiddleware)
## bindActionCreators
[bindActionCreators(actionCreators, dispatch)](https://cn.redux.js.org/api/bindactioncreators)
## compose
[compose(...functions)](https://cn.redux.js.org/api/compose)

从右到左来组合多个函数。
```jsx
const test=first(second(third))=const test=compose(first,second,third)
```
这是函数式编程中的方法，为了方便，被放到了 Redux 里。  
当需要把多个 [store enhancers](https://cn.redux.js.org/understanding/thinking-in-redux/glossary#store-enhancer) 依次执行的时候，需要用到它。

#### 参数[​](https://cn.redux.js.org/api/compose#%E5%8F%82%E6%95%B0 "Direct link to heading")

1.  (_arguments_): 需要合成的多个函数。预计每个函数都接收一个参数。它的返回值将作为一个参数提供给它左边的函数，以此类推。例外是最右边的参数可以接受多个参数，因为它将为由此产生的函数提供签名。（译者注：`compose(funcA, funcB, funcC)` 形象为 `compose(funcA(funcB(funcC())))`）

#### 返回值[​](https://cn.redux.js.org/api/compose#%E8%BF%94%E5%9B%9E%E5%80%BC "Direct link to heading")

(_Function_): 从右到左把接收到的函数合成后的最终函数。

#### 示例[​](https://cn.redux.js.org/api/compose#%E7%A4%BA%E4%BE%8B "Direct link to heading")

下面示例演示了如何使用 `compose` 增强 [store](https://cn.redux.js.org/api/store)，这个 store 与 [`applyMiddleware`](https://cn.redux.js.org/api/applymiddleware) 和 [redux-devtools](https://github.com/reduxjs/redux-devtools) 一起使用。

```jsx
import { createStore, applyMiddleware, compose } from 'redux'
import thunk from 'redux-thunk'
import DevTools from './containers/DevTools'
import reducer from '../reducers'
const store = createStore(  reducer,  compose(    applyMiddleware(thunk),    DevTools.instrument()  ))
```

#### 小贴士[​](https://cn.redux.js.org/api/compose#%E5%B0%8F%E8%B4%B4%E5%A3%AB "Direct link to heading")

-   所有的 `compose` 做的只是让你在写深度嵌套的函数时，避免了代码的向右偏移（译者注：可以参考[上述的译者注](https://cn.redux.js.org/api/compose#%E5%8F%82%E6%95%B0)）。不要觉得它很复杂。