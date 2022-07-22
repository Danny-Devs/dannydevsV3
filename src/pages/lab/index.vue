<script setup>
onMounted(() => {
  window.scrollTo(0, 0)
})
</script>

<template>
  <main class="text-center text-gray-700 dark:text-cyan-300 min-h-screen">
    <h1 text-2xl my-6>
      Welcome to my lab!
    </h1>
    <p mb-4>
      You can check out my web dev experiments below:
    </p>
    <router-link to="/lab/lab001">
      <p text-xl hover:underline>
        Lab001
      </p>
    </router-link>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
