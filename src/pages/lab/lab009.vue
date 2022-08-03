<script setup>
// import associated .md files
import Lab009 from '../../components/content/lab009.md'

const { x, y } = useWindowScroll()
const mCanvas = ref(null)
const isShowCanvas = ref(true)
const intervalFn = ref(null)
let context = {}

const katakana = 'アァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン'
const latin = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
const nums = '0123456789'

onMounted(() => {
  context = mCanvas.value.getContext('2d')

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
      context.fillStyle = 'rgba(0, 0, 0, 0.05)'
      context.fillRect(0, 0, mCanvas.value.width, mCanvas.value.height)

      context.fillStyle = '#0F0'
      context.font = `${fontSize}px monospace`

      for (let i = 0; i < rainDrops.length; i++) {
        const text = alphabet.charAt(Math.floor(Math.random() * alphabet.length))
        context.fillText(text, i * fontSize, rainDrops[i] * fontSize)

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
        lab009: Enter the Matrix
      </h2>
      <p text-center>
        Aug 2, 2022
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

    <Lab009 container />

    <!-- spacer for mobile footer -->
    <div py-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: matrix
</route>
