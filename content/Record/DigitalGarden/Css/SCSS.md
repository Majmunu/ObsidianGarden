---
UID: 20230307165231 
title: SCSS
tags: 
aliases: 
source: 
cssclass: 
created: 2023-03-07
Update: NaN
---

## ✍内容
## 混合（Mixins）

CSS 中的一些东西编写起来有点乏味，尤其是对于 CSS3 和存在的许多供应商前缀。mixin 允许您创建要在整个站点中重复使用的 CSS 声明组。您甚至可以传入值以使您的混合更加灵活。mixin 的一个很好的用法是用于供应商前缀。下面是 的示例。`transform`

-   [SCSS](https://sass.bootcss.com/guide#example-4-scss)
-   [SASS](https://sass.bootcss.com/guide#example-4-sass)
-   [.CSS](https://sass.bootcss.com/guide#example-4-css)

### SCSS

```SCSS
@mixin transform($property) {
  -webkit-transform: $property;
  -ms-transform: $property;
  transform: $property;
}
.box { @include transform(rotate(30deg)); }
```

### .CSS输出

```CSS
.box {
  -webkit-transform: rotate(30deg);
  -ms-transform: rotate(30deg);
  transform: rotate(30deg);
}

```

>要创建 mixin，请使用该指令并为其命名。我们命名了我们的混合蛋白。我们还在括号中使用变量，以便我们可以传入我们想要的任何变换。创建 mixin 后，您可以将其用作 CSS 声明，开头为后跟 mixin 的名称。`@mixin``transform``$property``@include`

%是 scss 中的一种特殊的选择器，用来定义一个占位符选择器（placeholder selector）。占位符选择器可以被其他选择器继承，但是不会被编译成 CSS 代码。这样可以避免生成多余的 CSS 代码，提高性能和可维护性。

## 扩展/继承

这是 Sass 最有用的功能之一。使用允许您从一个选择器共享一组 CSS 属性到另一个选择器。它有助于保持你的Sass非常干燥。在我们的示例中，我们将使用另一个功能为错误、警告和成功创建一系列简单的消息传递，该功能与扩展占位符类齐头并进。占位符类是一种特殊类型的类，仅在扩展时打印，可以帮助保持编译的 CSS 整洁干净。`@extend`

-   [南海](https://sass.bootcss.com/guide#example-5-scss)
-   [萨斯](https://sass.bootcss.com/guide#example-5-sass)
-   [.CSS](https://sass.bootcss.com/guide#example-5-css)

### scss语法

```scss
/* This CSS will print because %message-shared is extended. */
%message-shared
  border: 1px solid #ccc
  padding: 10px
  color: #333


// This CSS won't print because %equal-heights is never extended.
%equal-heights
  display: flex
  flex-wrap: wrap


.message
  @extend %message-shared


.success
  @extend %message-shared
  border-color: green


.error
  @extend %message-shared
  border-color: red


.warning
  @extend %message-shared
  border-color: yellow

```

```css
/* This CSS will print because %message-shared is extended. */
.message, .success, .error, .warning {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}

.error {
  border-color: red;
}

.warning {
  border-color: yellow;
}
```

上面的代码所做的是告诉 、、 和行为就像 .这意味着任何出现的地方，、、、和将会出现。神奇的事情发生在生成的 CSS 中，其中每个类都将获得与 相同的 CSS 属性。这有助于您避免在 HTML 元素上编写多个类名。`.message``.success``.error``.warning``%message-shared``%message-shared``.message``.success``.error``.warning``%message-shared`

除了 Sass 中的占位符类之外，您还可以扩展大多数简单的 CSS 选择器，但使用占位符是确保不会扩展嵌套在样式中其他位置的类的最简单方法，这可能会导致 CSS 中出现意外的选择器。

请注意，不会生成 中的 CSS，因为永远不会扩展。`%equal-heights``%equal-heights`