<script setup>
// import associated .md files
import Lab008 from '../../components/content/lab008.md'
import Lab008b from '../../components/content/lab008b.md'
import Lab008c from '../../components/content/lab008c.md'

const { x, y } = useWindowScroll()

const alpha = ref(1)
const canvas1 = ref(null)

const drawRects = () => {

}

onMounted(() => {
  const canvas = canvas1.value
  canvas.style.background = 'violet'
  const ctx = canvas.getContext('2d')

  const fadeOut = () => {
    requestAnimationFrame(fadeOut)
    ctx.clearRect(100, 100, canvas.width, canvas.height)
    ctx.globalAlpha = Math.sin(alpha.value)
    ctx.fillRect(100, 100, 100, 100)
    alpha.value += -0.05
  }

  ctx.fillStyle = 'blue'

  for (let i = 1; i <= 10; i++) {
    alpha.value = i * 0.1
    ctx.globalAlpha = alpha.value

    ctx.fillRect(i * 50, 20, 40, 40)
  }

  ctx.fillStyle = 'green'
  ctx.fillRect(100, 100, 100, 100)

  fadeOut()
})

const myDiv = ref(null)
let start, previousTimeStamp
const isDone = ref(false)
let scale = 1

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
  else {
    start = undefined
    previousTimeStamp = undefined
    scale = 1
  }
}

const animateDiv = () => window.requestAnimationFrame(step)

// matrix stuff
const mCanvas = ref(null)
const isShowCanvas = ref(true)
const intervalFn = ref(null)
let mContext = {}

const katakana = 'アァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン'
const latin = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
const nums = '0123456789'

onMounted(() => {
  mContext = mCanvas.value.getContext('2d')

  const enterTheMatrix = () => {
    isShowCanvas.value = true
    mCanvas.value.width = window.innerWidth
    mCanvas.value.height = window.innerHeight

    const alphabet = katakana + latin + nums

    const fontSize = 16
    const columns = mCanvas.value.width / fontSize

    const rainDrops = []

    for (let x = 0; x < columns; x++)
      rainDrops[x] = 1

    const draw = () => {
      mContext.fillStyle = 'rgba(0, 0, 0, 0.05)'
      mContext.fillRect(0, 0, mCanvas.value.width, mCanvas.value.height)

      mContext.fillStyle = '#0F0'
      mContext.font = `${fontSize}px monospace`

      for (let i = 0; i < rainDrops.length; i++) {
        const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length))
        mContext.fillText(text, i * fontSize, rainDrops[i] * fontSize)

        if (rainDrops[i] * fontSize > mCanvas.value.height && Math.random() > 0.975)
          rainDrops[i] = 0

        rainDrops[i]++
      }
    }

    intervalFn.value = setInterval(draw, 60)
  }

  enterTheMatrix()
})

const toggleMatrix = () => {
  isShowCanvas.value = !isShowCanvas.value
}
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- canvas matrix background -->
    <canvas v-show="isShowCanvas" ref="mCanvas" absolute top-0 left-0 class="z-1" @click="toggleMatrix" />

    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab008: Enter the Canvas
      </h2>
      <p text-center>
        Aug 1, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div text-center>
        <button bg-amber-400 px-6 py-2 rounded-lg shadow-lg hover:bg-amber-300 hover:shadow-none transition active:translate-y-1 @click="toggleMatrix">
          Bring back the Matrix
        </button>
      </div>
    </div>
    <!-- lab demo -->

    <Lab008 container />


    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10 mb-10>
      <div>
        <canvas ref="canvas1" mx-auto width="550" height="220" />
      </div>
    </div>
    <!-- lab demo -->

    <Lab008b container />

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-12 mb->
      <div>
        <div ref="myDiv" p-6 class="w-[200px]" text-center text-white text-xl height="100" bg-green-500 @click="animateDiv">
          <p>
            Click to animate this div
          </p>
        </div>
      </div>
    </div>
    <!-- lab demo -->

    <Lab008c container />

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
