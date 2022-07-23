<script setup>
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
        lab002: Popups, Modals, and Menus
      </h2>
      <p text-center>
        July 22, 2022
      </p>
    </div>
    <hr>
    <!-- end header -->

    <Suspense>
      <template #default>
        <p>Default</p>
      </template>
      <template #fallback>
        Loading...
      </template>
    </Suspense>
  </main>
</template>

<style scoped>

</style>

<route lang="yaml">
meta:
  layout: home
</route>
