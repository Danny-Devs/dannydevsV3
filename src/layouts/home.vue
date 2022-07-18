<template>
  <main class="h-screen relative dark:bg-gray-800 bg-red-200">
    <!-- mobile header -->
    <MobileHeader />
    <!-- sm and up navbar, located at top -->

    <div>
      <RouterView />
    </div>

    <!-- mobile bottom navbar disappears sm and up -->
    <div sm:hidden absolute bottom-0 dark:bg-cyan-500 bg-cyan-400 w-full>
      <MobileNavbar />
    </div>
  </main>
</template>
