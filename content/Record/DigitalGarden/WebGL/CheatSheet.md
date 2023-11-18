---
UID: 20230403165429 
title: "CheatSheet"
tags:  webgl
aliases: 
source: 
cssclass: 
created: 2023-04-03
Update: NaN
---

## ✍内容
# Cheat Sheet

Here you will find some 'recipes' and patterns that you can use in creative coding and generative art.  
在这里，你会发现一些“食谱”和模式，你可以用在创造性的编码和生成艺术。

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#new-array)New Array

You can use `Array.from(new Array(count))` to create a dense array at a fixed size. For example, to generate an array of 20 random numbers:  
可以使用 `Array.from(new Array(count))` 创建固定大小的密集阵列。例如，要生成20个随机数的数组：

const count = 20;
const randoms = Array.from(new Array(count)).map(() => Math.random());

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#array-with-values-01-inclusive)Array with values `0...1` (inclusive)  
值为 `0...1` （含）的数组

Using `index / (listLength - 1)`, you can get a _t_ value between 0 and 1.  
使用 `index / (listLength - 1)` ，您可以获得介于0和1之间的t值。

Example:
```JS
const count = 20;
const values = Array.from(new Array(count)).map((_, i) => {
  const t = i / (count - 1);
  // Do something with the 't' param...
  return t;
});
```
To guard against a `count` of <= 1: ❗ 🔄

const count = 20;
const values = Array.from(new Array(count)).map((_, i) => {
  const t = count <= 1 ? 0 : (i / (count - 1));
  return t;
});

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#grids--uv-coordinates)Grids & UV Coordinates ❗ 🔄

During the workshop, when I say "UV coordinates" I am referring to coordinates that vary from `(0, 0)` (top left) to `(1, 1)` (bottom right).  
在研讨会期间，当我说“UV坐标”时，我指的是从 `(0, 0)` （左上角）到 `(1, 1)` （右下角）的坐标。

For example, to create a UV grid with nested for loops:  
例如，要创建具有嵌套for循环的UV栅格，请执行以下操作：

const count = 5;
const points = [];
for (let x = 0; x < count; x++) {
  for (let y = 0; y < count; y++) {
    const u = count <= 1 ? 0.5 : (x / (count - 1));
    const v = count <= 1 ? 0.5 : (y / (count - 1));
    points.push([ u, v ]);
  }
}

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#padding-with-margins-using-linear-interpolation)Padding with Margins using Linear Interpolation  
使用线性插值填充边距

If you have UV coordinates for a surface between `(0, 0)` (top left) and `(1, 1)` (bottom right), you can use linear interpolation to get back pixel values for each coordinate:  
如果曲面的UV坐标在 `(0, 0)` （左上）和 `(1, 1)` （右下）之间，则可以使用线性插值来获取每个坐标的像素值：

const { lerp } = require('canvas-sketch-util/math');

// ...

const x = lerp(minX, maxX, u);
const y = lerp(minY, maxY, v);

Let's say you want a margin of `20px` in your `[ width, height ]` artwork, you can do this:  
假设您想要 `[ width, height ]` 图稿中的 `20px` 边距，您可以执行以下操作：

const margin = 20;
const x = lerp(margin, width - margin, u);
const y = lerp(margin, height - margin, v);

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#noise-from-uv-coordinates)Noise from UV Coordinates 来自UV坐标的噪波

If you have UV coordinates between `0..1`, you can get back a _simplex noise_ signal from those coordinates that smoothly varies between `-1...1`. ❗ 🔄

const random = require('canvas-sketch-util/random');

const frequency = 1;
const amplitude = 1;

const n = amplitude * random.noise2D(u * frequency, v * frequency);

The `frequency` changes how chaotic the noise signal will be, and the `amplitude` can be used to scale the value to something smaller or larger than `-1..1` range. ❗ 🔄

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#animated-noise)Animated Noise

By using a higher dimension noise function, you can animate the noise by a `{ time }` or `{ playhead }` variable from `canvas-sketch` props. ❗ 🔄

const settings = {
  // Enable animation & time props
  animate: true
};

canvasSketch(() => {
  return ({ context, time }) => {
    const frequency = 1;
    const amplitude = 1;

    // Use 3D instead of 2D noise
    const n = amplitude * random.noise3D(u * frequency, v * frequency, time);
  };
}, settings);

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#01-to--11)`0..1` to `-1...1`  
`0..1` 至 `-1...1`

If _t_ is between 0 and 1 (inclusive) and you want to map it to -1 to 1 (inclusive), you can use this: ❗ 🔄

const n = t * 2 - 1;

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#-11-to-01)`-1..1` to `0...1`  
`-1..1` 至 `0...1`

If _t_ is between -1 and 1 (inclusive) and you want to map it to 0 to 1 (inclusive), you can use this:  
如果t介于-1和1之间（含），并且你想将它映射到0到1（含），你可以使用这个：

const n = t * 0.5 + 0.5;

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#mapping-one-range-of-numbers-to-another)Mapping One Range of Numbers to Another  
将一个数字范围映射到另一个数字范围

You can also use the `mapRange` function in `canvas-sketch-util/math` to map one range of values to another:  
您还可以使用 `canvas-sketch-util/math` 中的 `mapRange` 函数将一个值范围映射到另一个值范围：

const { mapRange } = require('canvas-sketch-util/math');

// Our input lies between -1..1
const value = -0.25;

// Map the input range -1..1 to the output range 25..50
const n = mapRange(value, -1, 1, 25, 50);

This is equivalent to: 这相当于：

const { inverseLerp, lerp } = require('canvas-sketch-util/math');

// Get a 0..1 represenation of the value within the given range
const t = inverseLerp(-1, 1, value);

// Now interpolate that to our output range of 25..50
const n = lerp(25, 50, t);

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#fill-a-circle-in-canvas-2d)Fill a Circle in Canvas 2D  
在Canvas 2D中填充圆形

context.beginPath();
context.arc(x, y, radius, 0, Math.PI * 2, false);
context.fill();

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#rotating-shapes-in-canvas-2d)Rotating Shapes in Canvas 2D 在Canvas 2D中旋转图形

If you'd like to draw a shape rotated from its centre point, you need to first translate to the point you wish to draw the shape, then rotate, then offset by the center point of the shape. For example:  
如果你想画一个从它的中心点旋转的形状，你需要首先平移到你想画形状的点，然后旋转，然后偏移形状的中心点。例如：

// Draw a rotated rectangle
const x = 25;
const y = 50;
const rectWidth = 100;
const rectHeight = 30;
const rotation = Math.PI / 4;

context.save();
context.translate(x, y);
context.rotate(rotation);
context.translate(-rectWidth / 2, -rectHeight / 2);
context.fillRect(0, 0, rectWidth, rectHeight);
context.restore();

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#creating-a-2d-unit-vector-from-an-angle)Creating a 2D Unit Vector from an Angle  
从某个角度创建二维单位向量

A unit vector is a really handy construct for doing generative art. You can create one from an angle like so:  
单位向量对于生成艺术来说是一个非常方便的构造。你可以从这样的角度创建一个单位向量：

// angle is in radians
const normal = [ Math.cos(angle), Math.sin(angle) ];

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#creating-a-line-segment-from-a-2d-normal)Creating a Line Segment from a 2D Normal  
从二维法线创建线段

If you have a 2D unit normal (or an angle, see the previous recipe), you can create a line segment of a specific length and thickness like so:  
如果你有一个2D单位法线（或一个角度，见前面的食谱），你可以创建一个特定长度和厚度的线段，如下所示：

const { vec2 } = require('gl-matrix');

const normal = [ /* a 2D unit vector ... */ ];
const length = 2;
const thickness = 4;

// The center of the line segment
const center = [ 250, 100 ];

// Extrude in either direction
const line = [ -1, 1 ].map(dir => vec2.scaleAndAdd([], center, normal, dir * length));

// Draw line segment
context.beginPath();
line.forEach(([ x, y ]) => context.lineTo(x, y));
context.lineWidth = thickness;
context.stroke();

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#looping-motion-in--11-range)Looping Motion in `-1..1` Range  
`-1..1` 范围内的活套运动

To create a looping motion from `-1..1` you can use `Math.sin()`, like so:  
要从 `-1..1` 创建循环运动，可以使用 `Math.sin()` ，如下所示：

const motionSpeed = 0.5;
const v = Math.sin(time * motionSpeed);

You can map this value into `0..1` space and/or interpolate it to another range.  
您可以将此值映射到 `0..1` 空间和/或将其插值到另一个范围。

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#ping-pong-motion-in-01-range)Ping-Pong Motion in `0..1` Range  
`0..1` 范围内的乒乓运动

When you have a defined sketch `{ duration }` and you are using the `{ playhead }` prop, you can use `Math.sin()` to get a ping-pong motion from `0..1` which slowly varies from 0, to 1, and then back to zero. ❗ 🔄

const v = Math.sin(playhead * Math.PI);

You can invert this with `1.0 - v` if you need it to vary from 1, to 0, and then back to 1. ❗ 🔄

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#isometric-threejs-camera)Isometric ThreeJS Camera 等距ThreeJS摄像机

In your setup, replace the perspective camera with: ❗ 🔄

const camera = new THREE.OrthographicCamera();

In the `resize` function, replace the perspective camera configuration with: ❗ 🔄

const aspect = viewportWidth / viewportHeight;

// Ortho zoom
const zoom = 1.0;

// Bounds
camera.left = -zoom * aspect;
camera.right = zoom * aspect;
camera.top = zoom;
camera.bottom = -zoom;

// Near/Far
camera.near = -100;
camera.far = 100;

// Set position & look at world center
camera.position.set(zoom, zoom, zoom);
camera.lookAt(new THREE.Vector3());

// Update the camera
camera.updateProjectionMatrix();

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#3d-coordinate-system)3D Coordinate System 三维坐标系

Here's a small reference you can use to remember XYZ axes in ThreeJS.  
这里有一个小的参考，你可以用它来记住ThreeJS中的XYZ轴。

[![](https://github.com/mattdesl/workshop-generative-art/raw/master/docs/images/xyz-1.png)](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/images/xyz-1.png) [![](https://github.com/mattdesl/workshop-generative-art/raw/master/docs/images/xyz-2.png)](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/images/xyz-2.png)

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#third-party-glsl-modules)Third-Party GLSL Modules 第三方GLSL模块

With [glslify](https://github.com/glslify/glslify) (built-in to canvas-sketch CLI), we can import GLSL modules and snippets directly form npm into our shader code.  
使用glslify（内置于canvas-sketch CLI），我们可以将GLSL模块和片段直接从npm导入到我们的着色器代码中。

For example, after running `npm install glsl-noise`, you can use this:  
例如，在运行 `npm install glsl-noise` 之后，您可以使用以下命令：

// Import glslify
const glsl = require('glslify');

// Wrap your GLSL string with glslify function
const frag = glsl(`
  precision highp float;
  // We can now import GLSL snippets from npm into this shader
  #pragma glslify: noise = require('glsl-noise/simplex/3d');
  uniform float time;
  varying vec2 vUv;
  void main () {
    float d = noise(vec3(vUv, time));
    vec3 color = vec3(d);
    gl_FragColor = vec4(color, 1.0);
  }
`);

## [](https://github.com/mattdesl/workshop-generative-art/blob/master/docs/cheat-sheet.md#looping-noise)Looping Noise

You can use the following to blend 2D noise seamlessly in a GIF/MP4 loop.  
您可以使用以下命令在GIF/MP4循环中无缝混合2D噪波。

function loopNoise (x, y, t, scale = 1) {
  const duration = scale;
  const current = t * scale;
  return ((duration - current) * random.noise3D(x, y, current) + current * random.noise3D(x, y, current - duration)) / duration;
}

