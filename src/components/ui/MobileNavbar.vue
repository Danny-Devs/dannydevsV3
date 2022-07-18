<script setup>

</script>

<template>
  <main flex py-4 px-6 justify-between>
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
  </main>
</template>

<style scoped>

</style>
