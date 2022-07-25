<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main class="text-center text-gray-700 dark:text-cyan-300 min-h-screen">
    <h2 text-xl mt-6 mb-3>
      Web projects:
    </h2>
    <a href="https://merry-alpaca-3a7e8d.netlify.app/" target="_blank">
      <p dark:text-cyan-400 text-cyan-600 text-xl pb-1 hover:underline>
        Actionator
      </p>
    </a>

    <h2 text-xl mt-6 mb-3>
      Experiments:
    </h2>
    <div class="sm:w-3/5 px-4" text-left mx-auto flex flex-col gap-2 items-start>
      <router-link to="/lab/lab001">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab001: Animation and Vue
        </p>
      </router-link>
      <router-link to="/lab/lab002">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab002: Modals in Vue
        </p>
      </router-link>
      <router-link to="/lab/lab003">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab003: Having fun with a Random Yes/No free API
        </p>
      </router-link>
    <!-- <router-link pb-1 to="/lab/lab004">
      <p text-cyan-600 text-xl hover:underline>
        Lab004
      </p>
    </router-link> -->
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
