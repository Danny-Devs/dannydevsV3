<script setup>
// import associated .md files
import Lab008 from '../../components/content/lab008.md'

const { x, y } = useWindowScroll()

const alpha = ref(1)
const canvas1 = ref(null)

const drawRects = () => {

}

onMounted(() => {
  const canvas = canvas1.value
  canvas.style.background = "violet"
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
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
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
      <div>
        <canvas ref="canvas1" mx-auto width="550" height="220" />
      </div>
    </div>
    <!-- lab demo -->

    <Lab008 container />

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
