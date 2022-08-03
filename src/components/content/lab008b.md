---
number: 008b
title: Enter the Canvas
description: Vue JS education
---

The element animated above was not a `<canvas>` element--it is just a plain old `<div>`. You can use `requestAnimationFrame` to animate an element's CSS properties. I find this fascinating--there are multiple approaches to animation on the web explore and evaluate.

> Be aware of continously running animation/game loops since they can take up a lot of resources. The code snippet below uses an `if` check to turn off the animation loop after 2 seconds.

```javascript
// template ref
const myDiv = ref(null)
// boolean flag
const isDone = ref(false)
// init
let start, previousTimeStamp
let scale = 1

// call this function with requestAnimationFrame
function step(timestamp) {
  if (start === undefined)
    start = timestamp

  const elapsed = timestamp - start

  if (previousTimeStamp !== timestamp) {
    const count = Math.min(0.1 * elapsed, 300)

    scale += 0.005
    scale = Math.min(scale, 2)

    myDiv.value.style.transform = `translateX(${count}px) scale(${scale})`

    if (count === 300)
      isDone.value = true
  }

  if (elapsed < 2000) {
    previousTimeStamp = timestamp
    if (!isDone.value)
      window.requestAnimationFrame(step)
  }
}

const animateDiv = () => window.requestAnimationFrame(step)
```

Between .svg and Lottie animations, the `<canvas>` 2d and webgl APIs, CSS animation, and requestAnimationFrame, animation on the web is multi-faceted and diverse. I will be continuing my expedition into canvas 2d, which serves as a foundation on top of which many excellent 3rd-party libraries have been written, including [pixi.js](https://pixijs.com/) (2D WebGL renderer), [matter.js](https://brm.io/matter-js/) (2D physics engine), [Phaser](https://phaser.io/) (2D game engine), and [Three.js](https://threejs.org/) (3D library). Until then, DannyDevs out!
