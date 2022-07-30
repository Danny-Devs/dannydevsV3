<script setup>
// import associated .md files
import Lab006 from '../../components/content/lab006.md'

const { x, y } = useWindowScroll()
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab006: The Magic of Pixi.js
      </h2>
      <p text-center>
        July 29, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- lab demo -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <div flex flex-col items-center>
        

      </div>
    </div>
    <!-- lab demo -->

    <Lab006 />

    <!-- spacer for mobile footer -->
    <div py-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
