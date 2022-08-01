<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main flex justify-center text-center dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <div px-4 sm:px-9 pt-6 sm:pt-8 pb-24>
      <p text-xl sm:mb-6 mb-4>
        Posts
      </p>

      <div flex flex-col items-start text-left>
        <RouterLink hover:underline text-xl pb-1 dark:text-cyan-400 text-cyan-600 to="/blog/005">
          005: Become a Web Jedi with Vue 3
        </RouterLink>
        <RouterLink hover:underline text-xl pb-1 dark:text-cyan-400 text-cyan-600 to="/blog/004">
          004: Managing Different Screen Sizes with Responsive Design
        </RouterLink>
        <RouterLink hover:underline text-xl pb-1 dark:text-cyan-400 text-cyan-600 to="/blog/003">
          003: Branding DannyDevs: Art Asset Production and Management
        </RouterLink>

        <RouterLink hover:underline text-xl pb-1 dark:text-cyan-400 text-cyan-600 to="/blog/002">
          002: Why Vue 3 is Poised for a Golden Age
        </RouterLink>
        <RouterLink hover:underline text-xl pb-1 dark:text-cyan-400 text-cyan-600 to="/blog/001">
          001: How I made this blog post
        </RouterLink>
      </div>
    </div>

    <!-- right sidebar -->
    <!-- <div bg-orange-200 m-4 rounded-lg lg:block hidden lg:w-72 xl:w-80 h-min>
      <p border-b-2 border-orange-600 pt-4 pb-1 w-full bg-orange-400 rounded-tl-lg rounded-tr-lg text-center>
        Contents:
      </p>
      <div px-6 py-6>
        <div>
          <p mb-4>
            Notes
          </p>
          <p mb-4>
            Blog 001: How I made this blog post
          </p>
          <p mb-4>
            Blog 002: Why Vue 3 is Poised and Ready for its coming Golden Age
          </p>
        </div>
      </div>
    </div> -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: blog
</route>
