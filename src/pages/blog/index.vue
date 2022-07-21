<script setup>
import Blog001 from './blog001.md'
</script>

<template>
  <main dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <div px-9 pt-6 pb-24>
      <!-- insert splash image here -->

      <Blog001 />
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
