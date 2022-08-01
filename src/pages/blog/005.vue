<script setup>
import Blog005 from '../../components/content/blog005.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main flex justify-center dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <div px-4 sm:px-9 pt-6 pb-24>
      <!-- insert splash image here -->
      <Blog005 />
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: blog
</route>
