<script setup>
const props = defineProps({
  color: {
    type: String,
    default: 'bg-cyan-400',
  },
})
</script>

<template>
  <main flex py-4 px-6 justify-between :class="color" dark:bg-cyan-500 bg-cyan-400>
    <router-link
      to="/"
      flex
      flex-col
      items-center
    >
      <p i-carbon-home text-xl />
      <p text-sm>
        Home
      </p>
    </router-link>
    <router-link to="/lab" flex flex-col items-center>
      <p text-xl i-carbon-chemistry />
      <p text-sm>
        Lab
      </p>
    </router-link>
    <router-link to="/blog" flex flex-col items-center>
      <p text-xl i-carbon-book />
      <p text-sm>
        Blog
      </p>
    </router-link>
    <router-link to="/about" flex flex-col items-center>
      <p text-xl i-carbon-user />
      <p text-sm>
        About
      </p>
    </router-link>
    <router-link to="/links" flex flex-col items-center>
      <p text-xl i-carbon-list />
      <p text-sm>
        Links
      </p>
    </router-link>
  </main>
</template>

<style scoped>

</style>
