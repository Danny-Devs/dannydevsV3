<script setup>
// import associated .md files
import Lab000 from '../../components/content/lab000.md'

const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main container px-4 sm:px-8 lg:px-36 mx-auto min-h-screen mt-4 dark:text-cyan-300>
    <!-- header -->
    <div pt-1 sm:pt-4 pb-4 flex gap-4 justify-between items-center>
      <h2 text-2xl>
        lab000:
      </h2>
      <p text-center>
        July 25, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <!-- content -->

    <!-- copy -->
    <div md:mx-4 lg:mx-8 xl:mx-16 class="2xl:mx-28" mt-10>
      <p text-left mb-4>
        My interest in the scrolling web APIs was piqued by a Stack Overflow
      </p>
    </div>
    <!-- copy -->

    <!-- spacer for mobile footer -->
    <div my-12 />
    <!-- spacer for mobile footer -->
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
