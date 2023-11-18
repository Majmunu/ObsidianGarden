# 一、受控组件

**在HTML中**，表单元素的标签`<input>`、`<textarea>`、`<select>`等的值改变通常是根据用户输入进行更新。 **在React中**，可变状态通常保存在组件的状态属性中，并且只能使用 setState() 进行更新，而呈现表单的React组件也控制着在后续用户输入时该表单中发生的情况，以这种**由React控制的输入表单元素而改变其值**的方式，称为**受控组件**。 比如，给表单元素input绑定一个onChange事件，当input状态发生变化时就会触发onChange事件，从而更新组件的state。

```javascript
import React, { Component } from 'react'
export default class MyInput extends Component{
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    }
  }
  handleChange = (event)=>{
    this.setState({
        value: event.target.value
    })
  }
  render(){
    return(
      <div>
          <input
              type="text"
              value={this.state.value}
              onChange={this.handleChange}
           />
      </div>
    )
  }
}
```

复制

**受控组件更新state的流程** 1、 可以通过初始state中设置表单的默认值 2、每当表单的值发生变化时，调用onChange事件处理器 3、事件处理器通过事件对象event拿到改变后的状态，并更新组件的state 4、一旦通过setState方法更新state，就会触发视图的重新渲染，完成表单组件的更新

> React中数据是单项流动的，从示例中，可以看出表单的数据来源于组件的state，并通过props传入，这也称为**单向数据绑定**。然后又通过onChange事件处理器将新的数据写回到state，完成了**双向数据绑定**。

# 二、非受控组件

非受控组件指的是，表单数据由DOM本身处理。即不受setState()的控制，与传统的HTML表单输入相似，input输入值即显示最新值。 在非受控组件中，可以使用一个ref来从DOM获得表单值。

```javascript
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleSubmit(event) {
    console.log('A name was submitted: ' + this.input.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" ref={(input) => this.input = input} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

复制

非受控组件在底层实现时是在其内部维护了自己的状态state，这样表现出用户输入任何值都能反应到元素上。

# 三、异同和使用场景

1、受控组件 受控组件依赖于状态 受控组件的修改会实时映射到状态值上，此时可以对输入的内容进行校验 受控组件只有继承React.Component才会有状态 受控组件必须要在表单上使用onChange事件来绑定对应的事件 2、非受控组件 非受控组件不受状态的控制 非受控组件获取数据就是相当于操作DOM 非受控组件可以很容易和第三方组件结合，更容易同时集成 React 和非 React 代码

**总的来说：**

-   共同点，都是指表单元素，或者表单组件
-   不同点，被react的state控制，就是受控组件。不会state控制，就是非受控。
-   受控组件的实现方式，就是设置state，使用事件调用setstate，更新数据和视图。
-   非受控组件，避开state，使用ref等等方式，更新数据和视图。

**选择受控组件还是非受控组件** 1、受控组件使用场景：一般用在需要动态设置其初始值的情况。例如：某些form表单信息编辑时，input表单元素需要初始显示[服务器](https://cloud.tencent.com/product/cvm?from=10680)返回的某个值然后进行编辑。 2、非受控组件使用场景：一般用于无任何动态初始值信息的情况。例如：form表单创建信息时，input表单元素都没有初始值，需要用户输入的情况。