> 首先可以先看一下Redux如何工作
<img src="https://cdn.jsdelivr.net/gh/chenchen2692/Gallery-Img/20230212105022.png"/>


```ad-note
store 负责存储数据，相当于仓库，action负责dispatch派发数据，reducer负责接收处理数据然后交给store（个人理解 可能有些偏差 欢迎交流斧正）
```

## 传统redux写法（旧）
```jsx
//reducer
const counterReducer = (state = { counter: 0 }, action) => {

    if (action.type === "increment") {

        return {

            counter: state.counter + 1,

        };

    }

    if (action.type === "increase") {

        return {

            counter: state.counter + action.amount,

        };

    }

    if (action.type === "decrement") {

        return {

            counter: state.counter - 1,

        };

    }

    return state;

}
//连接到store
const store = createStore(counterReducer)
```
## 使用reduxjs/toolkit（新）
> 新的写法主要体现在reducer的简化上
```jsx
//reducer
const countSlice= createSlice(

    {

        name: "counter",

        initialState: { counter: 0 },

        reducers: {

            increment(state) {

                state.counter++;//在redux中这种写法不被允许 在toolkit中被允许

            },

            decrement(state) {

                state.counter--;

            },

            increase(state, action) {

                state.counter += action.payload;

            },

  

        }

    }

)
  
//连接到store
const store = configureStore(

    {

        reducer: { counter: countSlice.reducer}//作为一个对象处理多reducer

    }

    )
```

## 简单使用步骤
1. 创建reducer文件
```jsx
import { createSlice } from '@reduxjs/toolkit';
1. 创建切片
const uiSlice = createSlice({
  name: 'ui',
  initialState: { cartIsVisible: false },
  reducers: {
    toggle(state) {
      state.cartIsVisible = !state.cartIsVisible;
    }
  }
});
3、将actions导出
export const uiActions = uiSlice.actions;
2、将切片导出
export default uiSlice;
```
2. 在store中引入reducer
```jsx
import { configureStore } from '@reduxjs/toolkit';

import uiSlice from './ui-slice';
import cartSlice from './cart-slice';
4 在store中引入切片
const store = configureStore({
  reducer: { ui: uiSlice.reducer, cart: cartSlice.reducer },
});

export default store;
```
3.  在index.js中包裹根组件
```jsx
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import store from './store/index';
import './index.css';
import App from './App';
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```
4. 在组件中使用dispatch派发actions
```jsx
import { useDispatch} from 'react-redux';
import { uiActions } from '../../store/ui-slice';
const dispatch = useDispatch();
const toggleCartHandler = () => {
dispatch(uiActions.toggle()); //5toggle 1步骤中reducer的action之一

};
```
5. 使用useSelecter接收数据
```jsx
import { useSelector } from 'react-redux';
const Cart = (props) => {
const cartItems = useSelector((state) => state.cart.items);
```