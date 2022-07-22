<script setup>
import Blog001 from './blog001.md'

onMounted(() => {
  window.scrollTo(0, 0)
})
</script>

<template>
  <main flex justify-center dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <div px-4 sm:px-9 pt-6 pb-24>
      <!-- insert splash image here -->

      <Blog001 />
    </div>

    <!-- right sidebar -->
    <div bg-orange-200 m-4 rounded-lg lg:block hidden lg:w-72 xl:w-80 h-min>
      <p border-b-2 border-orange-600 pt-4 pb-1 w-full bg-orange-400 rounded-tl-lg rounded-tr-lg text-center>
        Contents:
      </p>
      <div px-6 py-6 >
        <div>
          <p mb-4>
            Notes
          </p>
          <p mb-4>
            Blog 001: How I made this blog post
          </p>
          <p mb-4>
            Blog 001: How I made this blog post
          </p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
