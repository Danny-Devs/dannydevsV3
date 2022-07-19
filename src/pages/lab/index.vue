<script setup>

</script>

<template>
  <main class="text-center text-gray-700 dark:text-gray-200">
    <div ml-4 mt-4 mb-4>
      <div i-carbon-home text-xl/>
    </div>
    <h1 text-2xl mb-6>
      Welcome to my lab!
    </h1>
    <p mb-4>You can check out my web dev experiments below:</p>
    <router-link to="/lab/lab001">

      <p text-xl hover:underline>Lab001</p>
    </router-link>
  </main>
</template>

<style scoped>

</style>
