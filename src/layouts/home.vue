<template>
  <main class="h-screen relative bg-red-200">
    <div>
      <RouterView />
    </div>

    <div sm:hidden absolute bottom-0 bg-gray-500 w-full>
      <MobileNavbar />
    </div>
  </main>
</template>
