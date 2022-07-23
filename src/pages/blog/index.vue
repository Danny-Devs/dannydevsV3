<script setup>
import Blog001 from '../../components/content/blog001.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main flex justify-center text-center dark:text-cyan-300 min-h-screen container mx-auto>
    <!-- spacing goes below -->
    <div px-4 sm:px-9 pt-8 pb-24>
      <!-- insert splash image here -->
      <p text-2xl mb-8>
        Blog Posts
      </p>

      <div flex flex-col>
        <RouterLink underline text-xl pb-1 to="/blog/001">
          Blog 001
        </RouterLink>
        <RouterLink underline text-xl pb-1 to="/blog/002">
          Blog 002
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
