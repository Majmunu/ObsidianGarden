---
UID: 20230313091754 
title: ThreeJs
tags: 
-- 进级
-- WeBGL
aliases: 
source: 
cssclass: 
created: 2023-03-13
Update: NaN
---

## 创建模板
> Running Locally 本地运行

Most of the benefits of `canvas-sketch` (MP4 export, `require()` statements, etc) are only usable when we run the CLI tool locally.  
`canvas-sketch` 的大多数优点（MP4导出、 `require()` 语句等）只有在本地运行CLI工具时才能使用。

You can install it with npm:  
您可以使用npm安装它：

`npm install canvas-sketch-cli -g`

> 💡 Notice the `-cli` part! This means we want to install the CLI tool, not just the JavaScript library.  
> 💡 注意 `-cli` 部分！这意味着我们要安装CLI工具，而不仅仅是JavaScript库。

Then, go into a new directory:  
然后，进入一个新目录：

`mkdir genart-workshop`
`cd genart-workshop`

And scaffold out our first artwork with the `three` template:  
用 `three` 模板搭建我们的第一幅作品：

`canvas-sketch src/sketch.js --new --template=three`

Now open [](http://localhost:9966/)[http://localhost:9966/](http://localhost:9966/) and start to edit `src/sketch.js`, and the browser should live reload.  
现在打开 [](http://localhost:9966/)[http://localhost:9966/](http://localhost:9966/) 并开始编辑 `src/sketch.js` ，浏览器应实时重新加载。
```js
const settings = {

  // 画布大小

  dimensions: "A4",
  // 画布单位

  units: "cm",
  // 画布比例

  scaleToView: true,

  // 画布像素密度

  pixelsPerInch: 300,
  // 画布方向

  orientation: "landscape",

  // Make the loop animated

  animate: true,

  // Get a WebGL canvas rather than 2D

  context: "webgl",

};
```
---
## THREEJS
###   THREE.Vector & THREE.Color 向量和颜色
ThreeJS uses a data types for "coordinates" called `THREE.Vector`:  
ThreeJS使用名为 `THREE.Vector` 的“坐标”数据类型：

-   [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2) (2D Coordinate)  三个矢量2（2D坐标）
-   [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3) (3D Coordinate)  三个矢量3（三维坐标）
-   [THREE.Vector4](https://threejs.org/docs/#api/en/math/Vector4) (4D Coordinate)  三个矢量4（4D坐标）

It also uses a data type for colors called `THREE.Color`:  
它还使用名为 `THREE.Color` 的颜色数据类型：

-   [THREE.Color](https://threejs.org/docs/#api/en/math/Color)

Here's one of our earlier demos but using ThreeJS data types instead of plain JavaScript objects.  
这是我们早期的一个演示，但是使用了 ThreeJS 数据类型而不是普通的 JavaScript 对象。
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/three.vector-and-three.color)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313110516.png)

---
### THREE.Geometry  几何图形
ThreeJS uses a [THREE.Geometry](https://threejs.org/docs/#api/en/core/Geometry) class to hold `vertices` (vertex positions) and `faces` (i.e. indices).  
ThreeJS使用THREE.Geometry类来保存 `vertices` （顶点位置）和 `faces` （即索引）。

Some of the built-in geometries are shown below, such as:  
一些内置几何图形如下所示，例如：

-   [THREE.PlaneGeometry](https://threejs.org/docs/#api/en/geometries/PlaneGeometry)
-   [THREE.BoxGeometry](https://threejs.org/docs/#api/en/geometries/BoxGeometry)
-   [THREE.SphereGeometry](https://threejs.org/docs/#api/en/geometries/SphereGeometry)
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/three.geometry)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313111038.png)

---
### THREE.Material 材料
ThreeJS uses a [THREE.Material](https://threejs.org/docs/#api/en/materials/Material) class to hold surface properties such as color, metalness, etc.  
ThreeJS使用THREE.material类来保存表面属性，如颜色、金属度等。

Some of the built-in materials are shown below, such as:  
一些内置材料如下所示，例如：

-   [THREE.MeshBasicMaterial](https://threejs.org/docs/#api/en/materials/MeshBasicMaterial)
-   [THREE.MeshNormalMaterial](https://threejs.org/docs/#api/en/materials/MeshNormalMaterial)
-   [THREE.MeshPhongMaterial](https://threejs.org/docs/#api/en/materials/MeshPhongMaterial)
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/three.material)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313111513.png)

---
### THREE.Mesh 组合
You can crete a [THREE.Mesh](https://threejs.org/docs/#api/en/objects/Mesh) by combining a `THREE.Geometry` and `THREE.Material`.  
您可以通过组合 `THREE.Geometry` 和 `THREE.Material` 来创建THREE.Mesh。

> _Hint:_ For performance, it's better to create one instance of `THREE.Geometry` and re-use it for many meshes.  
> 提示：为了提高性能，最好创建 `THREE.Geometry` 的一个实例，然后将其重用于多个网格。

![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313111707.png)

---
 
###   Position 位置
All objects in ThreeJS have a `position`, which is a [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3) that you can use to translate the object in space.  
ThreeJS 中的所有对象都有一个 `position` ，它是一个 THREE.Vector3，您可以使用它在空间中平移对象。
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/3d-transformations/position)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313113338.png)

> 还可以控制缩放大小可简写 （具体可查阅文档）
---
###  Rotation 旋转
Objects also have a `rotation`, which is a [THREE.Euler](https://threejs.org/docs/#api/en/math/Euler) that you can use to rotate an object.  
对象还有一个 `rotation` ，它是一个THREE.Euler，可用于旋转对象。

The class is very similar to `THREE.Vector3`, but values are in radians.  
该类与 `THREE.Vector3` 非常相似，但值以弧度为单位。
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/3d-transformations/rotation)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313113532.png)

---
### Scale 缩放
Objects also have a `scale`, which is a [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3) that stretches the mesh along the X, Y and Z axes.  
对象还有一个 `scale` ，它是一个 THREE.Vector3，用于沿着 X、Y 和 Z 轴拉伸网格。
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/3d-transformations/scale)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313114051.png)

---
### THREE.Scene 场景
The core of any ThreeJS application is its scenegraph, [THREE.Scene](https://threejs.org/docs/#api/en/scenes/Scene).  
任何ThreeJS应用程序的核心都是它的场景图THREE.Scene。

This container is what holds multiple meshes, lights, and other 3D objects.  
此容器用于保存多个网格、灯光和其他3D 对象。
[WebGL & GLSL — A Primer --- WebGL & GLSL—入门 (mattdesl.github.io)](https://mattdesl.github.io/workshop-webgl-glsl/#/threejs-basics/three.scene)
![](https://wcc-image.oss-cn-guangzhou.aliyuncs.com/image/20230313114147.png)

