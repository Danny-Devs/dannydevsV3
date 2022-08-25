<script setup>
// import associated .md files
import { onKeyDown, onKeyUp } from '@vueuse/core'
import Lab010 from '../../components/content/lab010.md'

const { x: myX, y: myY } = useWindowScroll()
onMounted(() => {
  myX.value = 0
  myY.value = 0
})

const canvasEl = ref(null)

onMounted(() => {
  const ctx = canvasEl.value.getContext('2d')

  // ------------START scale to all resolutions (prevent blurriness)-----------------
  // set display size (css pixels)
  const width = 480
  const height = 320
  canvasEl.value.style.width = `${width}px`
  canvasEl.value.style.height = `${height}px`

  // set actual size in memory (scaled to account for extra pixel density)
  const scale = window.devicePixelRatio
  canvasEl.value.width = Math.floor(width * scale)
  canvasEl.value.height = Math.floor(height * scale)

  // normalize coordinate system to use CSS pixels
  ctx.scale(scale, scale)
  // ------------END scale to all resolutions (prevent blurriness)-----------------

  // paddle props
  const paddleHeight = 10
  const paddleWidth = 75
  let paddleX = (parseInt(canvasEl.value.style.width) - paddleWidth) / 2

  const ballRadius = 10
  let ballColor = 'red'
  let x = parseInt(canvasEl.value.style.width) / 2 + paddleWidth / 2 + 1
  let y = ballRadius
  let dx = 0
  let dy = -2

  let rightPressed = false
  let leftPressed = false

  function drawPaddle() {
    ctx.beginPath()
    ctx.rect(paddleX, parseInt(canvasEl.value.style.height) - paddleHeight, paddleWidth, paddleHeight)
    ctx.fillStyle = 'blue'
    ctx.fill()
    ctx.closePath()
  }

  onKeyDown(['a', 'A', 'ArrowLeft'], (e) => {
    leftPressed = true
  }, { target: document })
  onKeyDown(['d', 'D', 'ArrowRight'], (e) => {
    rightPressed = true
  }, { target: document })
  onKeyUp(['a', 'A', 'ArrowLeft'], (e) => {
    leftPressed = false
  }, { target: document })
  onKeyUp(['d', 'D', 'ArrowRight'], (e) => {
    rightPressed = false
  }, { target: document })

  function changeBallColor() {
    // get random fill color
    ballColor = `rgb(${Math.floor(Math.random() * 256)}, ${Math.floor(Math.random() * 256)}, ${Math.floor(Math.random() * 256)})`
  }

  function drawBall(changeColor) {
    ctx.beginPath()
    ctx.arc(x, y, ballRadius, 0, Math.PI * 2)
    ctx.fillStyle = ballColor
    ctx.fill()
    ctx.closePath()
  }

  function draw() {
    ctx.clearRect(0, 0, parseInt(canvasEl.value.style.width), parseInt(canvasEl.value.style.height))
    drawBall()
    drawPaddle()

    // check if the ball has touched the top 'wall'
    if (y + dy < ballRadius) {
      dy = -dy
      changeBallColor()
    }
    // if the ball is below the top of the bar
    else if (y >= (parseInt(canvasEl.value.style.height) - paddleHeight - ballRadius)) {
      // and is within the bar's width, bounce it back up
      if (x >= paddleX && x <= paddleX + paddleWidth) {
        console.log('dy before: ', dy)
        dy = -2
      }
    }

    if (y > parseInt(canvasEl.value.style.height) + ballRadius) {
      alert('Game Over!')
      x = parseInt(canvasEl.value.style.width) / 2 + paddleWidth / 2 + 1
      y = ballRadius
    }

    // if the ball hits L or R walls, reflect the ball
    if (x + dx < ballRadius || x + dx > parseInt(canvasEl.value.style.width) - ballRadius) {
      dx = -dx
      changeBallColor()
    }

    if (rightPressed)
      paddleX = Math.min(paddleX + 2, parseInt(canvasEl.value.style.width) - paddleWidth)
    else if (leftPressed)
      paddleX = Math.max(paddleX - 2, 0)

    // move the ball
    x += dx
    y += dy

    requestAnimationFrame(draw)
  }

  requestAnimationFrame(draw)
})
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab010: Breakout Game with Vanilla JS
      </h2>
      <p text-center>
        Aug 24, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- lab demo -->
    <div mb-12 md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <canvas
        id="myCanvas"
        ref="canvasEl"
        class="bg-[#fff] block mx-auto"
      />
    </div>
    <!-- lab demo -->

    <Lab010 container />

    <!-- spacer for mobile footer -->
    <div py-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
