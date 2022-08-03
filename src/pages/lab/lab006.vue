<script setup>
// import associated .md files
import Lab006 from '../../components/content/lab006.md'

const { x, y } = useWindowScroll()
onMounted(() => {
  x.value = 0
  y.value = 0
})
const { counter, pause, resume } = useInterval(200, { controls: true })
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab006: Composables, Composition, and vueUse
      </h2>
      <p text-center>
        July 29, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div flex flex-col items-center>
        <p mb-8 mt-4 text-2xl>
          Interval fired: {{ counter }}
        </p>
        <div flex gap-2 mb-10>
          <button class="dark:hover:bg-fuchsia-600" dark:bg-fuchsia-700 hover:bg-fuchsia-200 shadow-md active:translate-y-1 active:shadow-none transition bg-fuchsia-300 px-4 py-2 rounded-lg @click="pause()">
            pause
          </button>
          <button active:shadow-none class="dark:hover:bg-fuchsia-600" dark:bg-fuchsia-700 hover:bg-fuchsia-200 shadow-md active:translate-y-1 transition bg-fuchsia-300 px-4 py-2 rounded-lg @click="resume()">
            resume
          </button>
          <button active:shadow-none class="dark:hover:bg-fuchsia-600" dark:bg-fuchsia-700 hover:bg-fuchsia-200 shadow-md active:translate-y-1 transition bg-fuchsia-300 px-4 py-2 rounded-lg @click="counter = 0">
            reset
          </button>
        </div>
      </div>
    </div>
    <!-- lab demo -->

    <Lab006 container />

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
