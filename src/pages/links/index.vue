<script setup>
import Links from '../../components/content/links.md'

onMounted(() => {
  window.scrollTo(0, 0)
})
</script>

<template>
  <div container mx-auto px-4 py-6 min-h-screen dark:text-cyan-300>
    <Links />
  </div>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
