The pink rectangle you see above is the background of a `<canvas>` HTML element. This "canvas" provides you with a `context` for either 2D or WebGL (WebGL allows 3D). The context holds all sorts of properties that  can be used to make anything from animations to interactive experiences and games.

Notice that the code snippet below is wrapped within an `onMounted` function--a Vue 3 lifecycle hook that fires after the .vue component has been mounted to the DOM. Without this hook, any template refs will error out because there is no DOM element to connect with.

We then utilize the context, `ctx`, provided by the canvas API to create the looping green square animation as well as the row of blue squares.

```javascript
// template ref--canvas element must have id="myCanvas"
const myCanvas = ref(null)

// onMounted lifecycle hook
onMounted(() => {
  // after mount, it's safe to work with myCanvas--not before!
  myCanvas.value.style.background = 'violet'

  // get the appropriate context, '2d' or 'webgl'
  const ctx = myCanvas.value.getContext('2d')


  ctx.fillStyle = 'blue'

  // creates the row of blue squares
  for (let i = 1; i <= 10; i++) {
    alpha.value = i * 0.1
    ctx.globalAlpha = alpha.value

    ctx.fillRect(i * 50, 20, 40, 40)
  }

  ctx.fillStyle = 'green'
  ctx.fillRect(100, 100, 100, 100)

  // function to create the green square fading in and out
  const fadeOut = () => {
    // notice the recursive loop -- this is the animation loop, using the built-in function `requestAnimationFrame`
    requestAnimationFrame(fadeOut)
    ctx.clearRect(100, 100, myCanvas.value.width, myCanvas.value.height)
    ctx.globalAlpha = Math.sin(alpha.value)
    ctx.fillRect(100, 100, 100, 100)
    alpha.value += -0.05
  }
  fadeOut()
})
```

> Tip: when working with 3rd-party libraries that require template refs (connecting to the DOM the "Vue way" as opposed to vanilla JS DOM manipulation), be aware that you'll have to do the `onMounted` dance and wrangle any scoping issues that may come up when you're trying to access something that's inside `onMounted` and is therefore not accessible from the template.


