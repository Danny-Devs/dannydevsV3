<template>
  <main class="h-screen relative bg-red-200">
    <div>
      <RouterView />
    </div>

    <div sm:hidden absolute bottom-0 bg-cyan-400 w-full>
      <MobileNavbar />
    </div>
  </main>
</template>
