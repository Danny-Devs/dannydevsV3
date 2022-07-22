<script setup>
const { x, y } = useWindowScroll()

onMounted(() => {
  x.value = 0
  y.value = 0
})
</script>

<template>
  <main class=" bg-red-50  dark:bg-slate-900 min-h-screen">
    <!-- mobile header -->
    <Header />

    <RouterView />

    <!-- mobile bottom navbar disappears sm and up -->
    <div block sm:hidden absolute fixed bottom-0 w-full>
      <MobileNavbar />
    </div>

    <!-- desktop footer -->
    <DesktopFooter hidden sm:block />
  </main>
</template>
