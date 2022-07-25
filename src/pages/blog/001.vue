<script setup>
import Blog001 from '../../components/content/blog001.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main flex justify-center dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <BlogWrapper>
      <!-- insert splash image here -->
      <Blog001 />
    </BlogWrapper>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: blog
</route>
