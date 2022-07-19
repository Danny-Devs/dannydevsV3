<template>
  <main class="h-screen bg-red50 relative dark:bg-slate-900">
    <!-- mobile header -->
    <Header />

    <div>
      <RouterView />
    </div>

    <!-- mobile bottom navbar disappears sm and up -->
    <div sm:hidden absolute fixed bottom-0 w-full>
      <MobileNavbar />
    </div>
  </main>
</template>
