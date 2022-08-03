<script setup>
import Links from '../../components/content/links.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <div container mx-auto px-4 pt-6 pb-24 min-h-screen dark:text-cyan-300>
    <Links />
  </div>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: matrix
</route>
