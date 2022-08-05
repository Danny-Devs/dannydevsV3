<script setup>
// import associated .md files
import Lab009 from '../../components/content/lab009.md'

const { x, y } = useWindowScroll()
onMounted(() => {
  x.value = 0
  y.value = 0
})

// watchEffect(() => {
//   if (input.value) {
//     input.value.focus()
//   } else {
//     // not mounted yet, or the element was unmounted e.g. by v-if
//   }
// })
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab009: Let's get Focused
      </h2>
      <p text-center>
        Aug 3, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div>
        hi
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
  layout: home
</route>
