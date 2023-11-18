
## 一、为什么要用 less

less 是 css 的预处理语言，好处是支持嵌套写法，让整个样式结构更易读吗，此外还支持变量、Mixin、函数等新特性，可以让我们写的样式代码更加的健壮，可复用性也更高。

  

## 二、如何配置 less

- **首先需要引入 less 包**

```text
npm i less --save-dev
```

- **然后再引入 less 的 loade**r

```text
npm install less less-loader --save-dev
```

- **这时候应该就能看到 package.json 的 devDependencies 了**

![](https://pic3.zhimg.com/80/v2-43a01d5109f9adacef4c588aa01346ca_720w.webp)

- **接着我们需要让 webpack 暴露出来，因为 React 默认把 webpack 文件隐藏起来了,我们需要先初始化并 git 到本地仓库一下，然后再执行 eject。PS：如果先做了这一步再引入 less 包的话，可以在引入包之后再执行一下这几步 git**

```text
   git init
   git add .
   git commit -m ‘init'
   yarn eject
```

- **此时我们便可以看到 webpack 的 config 以及暴露出来了，里边包含了 webpack.config.js 这个文件**

![](https://pic1.zhimg.com/80/v2-c6f53128b15e97cfe2628adeb0b22ebc_720w.webp)

- **然后就可以在 webpack.config.js 内去配置 less 的全局变量以及 less-loader 加载器**

1. 对于 less 全局变量的配置，可以先搜索 `**sassModuleRegex**`，然后在它下面新增两行配置项

```text
    const lessRegex = /\.less$/;
    const lessModuleRegex = /\.module\.less$/;
```

2. 对于 less-loader 的配置，我们需要找到 `**getStyleLoaders**` 这个函数，然后在里边 require 一下 less 的 loader

![](https://pic4.zhimg.com/80/v2-507f1f7cab4edf69c876c01d63746ea3_720w.webp)

3. 接着我们搜索 `**oneOf**` ，然后再在这个数组内配置 less-loader

```text
{
        test: lessRegex,
        exclude: lessModuleRegex,
        use: getStyleLoaders(
          {
                importLoaders: 2,
                sourceMap: isEnvProduction
                  ? shouldUseSourceMap
                  : isEnvDevelopment,
          },
          'less-loader'
        ),
        sideEffects: true,
  },
  {
        test: lessModuleRegex,
        use: getStyleLoaders(
          {
                importLoaders: 2,
                sourceMap: isEnvProduction
                  ? shouldUseSourceMap
                  : isEnvDevelopment,
          },
          'less-loader'
        ),
        sideEffects: true,
  },
```

![](https://pic4.zhimg.com/80/v2-66e2f0abbbb7d245305c2f3aee27312f_720w.webp)

**最后，对于使用 React TS 的同学，还需要再做个全局的 declare 配置，因为 TS 不能直接识别 less 文件。**

- 目录：

![](https://pic4.zhimg.com/80/v2-58d7dcf43a86ac9d426d4ecb72177487_720w.webp)

- 配置项:

![](https://pic2.zhimg.com/80/v2-46fad04eaec74681257c959ea8b86dcd_720w.webp)

**以上方面全部配置完后便可以重新 start 一下项目，此时 less 的也全部配置完毕了～**

  

## 三、如何使用 less

**到了这步就很简单了，我们已经可以开始使用 less 来愉快的书写样式了**

![](https://pic2.zhimg.com/80/v2-c629b2c21e883da9fc93290c15243255_720w.webp)

![](https://pic3.zhimg.com/80/v2-6959e75a5f3c5b0e5887e6588f145f0e_720w.webp)