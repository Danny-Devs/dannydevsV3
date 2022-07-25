<script setup>

</script>

<template>
  <div container mx-auto bg-cyan-400 dark:bg-cyan-500>
    <div flex px-8 py-4 text-xl justify-between items-center>
      <div flex gap-3>
        <a dark:text-slate-900 hover:text-gray-700 target="_blank" href="https://www.linkedin.com/in/danielahn47/" i-carbon-logo-linkedin />
        <a dark:text-slate-900 hover:text-gray-700 target="_blank" href="https://twitter.com/dannydevsss" i-carbon-logo-twitter />
        <a dark:text-slate-900 hover:text-gray-700 target="_blank" href="https://github.com/Danny-Devs" i-carbon-logo-github />
        <a dark:text-slate-900 hover:text-gray-700 href="mailto:et3rnal.d@gmail.com?subject=From DannyDevs.com" i-carbon-email />
      </div>
      <p text-sm dark:text-slate-900>
        &copy; Daniel Ahn {{ new Date().getFullYear() }}
      </p>
    </div>
  </div>
</template>

<style scoped>

</style>
