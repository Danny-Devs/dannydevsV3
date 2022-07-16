<template>
  <main class="h-screen relative bg-red-200">
    <!-- mobile navbar disappears sm and up -->
    <div sm:hidden absolute bottom-0 bg-cyan-400 w-full>
      <MobileNavbar />
    </div>

    <!-- sm and up navbar, located at top -->

    <div>
      <RouterView />
    </div>
  </main>
</template>
