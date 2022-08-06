<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main class="text-center text-gray-700 dark:text-cyan-400 min-h-screen">
    <div flex justify-center>
      <h2 text-xl sm:text-lg mt-6 mb-3 border-b-2 sm:border-b-1 w-fit>
        Web projects:
      </h2>
    </div>
    <div class="sm:w-3/5 px-4" text-left mx-auto flex flex-col gap-2 items-start>
      <a href="https://cute-horse-892b24.netlify.app/" target="_blank">
        <p dark:text-cyan-400 text-cyan-600 text-2xl sm:text-xl pb-1 hover:underline>
          Responsive website with dark mode
        </p>
      </a>
      <a href="https://merry-alpaca-3a7e8d.netlify.app/" target="_blank">
        <p dark:text-cyan-400 text-cyan-600 text-2xl sm:text-xl pb-1 hover:underline>
          Actionator: Focus on your to-dos one at a time
        </p>
      </a>
    </div>
    <div flex justify-center>
      <h2 text-xl sm:text-lg mt-8 mb-4 border-b-2 sm:border-b-1 w-fit>
        Experiments:
      </h2>
    </div>
    <div class="sm:w-3/5 px-4" text-left mx-auto flex flex-col gap-2 items-start>
      <router-link to="/lab/lab009">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab009: Tip Calculator
        </p>
      </router-link>
      <router-link to="/lab/lab008">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab008: Enter the Canvas
        </p>
      </router-link>
      <router-link to="/lab/lab007">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          👁 Lab007: vueUse's useEyeDropper and the EyeDropper web API
        </p>
      </router-link>
      <router-link to="/lab/lab006">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab006: Composables, Composition, and vueUse
        </p>
      </router-link>
      <router-link to="/lab/lab005">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab005: A Very Important Matter(.js)
        </p>
      </router-link>
      <router-link to="/lab/lab004">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab004: Unwrapping the Scrolling Web APIs
        </p>
      </router-link>
      <router-link to="/lab/lab003">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab003: Having Fun with a Free Yes or No API
        </p>
      </router-link>
      <router-link to="/lab/lab002">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab002: Modals in Vue
        </p>
      </router-link>
      <router-link to="/lab/lab001">
        <p dark:text-cyan-400 text-cyan-600 text-xl hover:underline>
          Lab001: Animation in Vue
        </p>
      </router-link>
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
