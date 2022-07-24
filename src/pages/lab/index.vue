<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main class="text-center text-gray-700 dark:text-cyan-300 min-h-screen">
    <h1 text-2xl my-6>
      Welcome to the lab!
    </h1>
    <p px-2 mb-4>
      Larger web projects:
    </p>
    <a href="https://merry-alpaca-3a7e8d.netlify.app/" target="_blank">
      <p text-xl pb-1 underline>
        Actionator
      </p>
    </a>

    <p px-2 mb-4 mt-6>
      Web dev experimental labs:
    </p>
    <router-link to="/lab/lab001">
      <p text-xl pb-1 underline>
        Lab001
      </p>
    </router-link>
    <router-link pb-1 to="/lab/lab002">
      <p text-xl underline>
        Lab002
      </p>
    </router-link>
    <router-link pb-1 to="/lab/lab003">
      <p text-xl underline>
        Lab003
      </p>
    </router-link>
    <router-link pb-1 to="/lab/lab004">
      <p text-xl underline>
        Lab004
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
