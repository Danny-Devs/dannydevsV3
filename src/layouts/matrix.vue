<template>
  <main class=" h-screen">
    <!-- mobile header -->
    <Header />

    <RouterView />

    <!-- mobile bottom navbar disappears sm and up -->
    <div block sm:hidden absolute fixed bottom-0 w-full>
      <MobileNavbar />
    </div>

    <!-- desktop footer -->
    <DesktopFooter hidden sm:block />

    <!-- having issues with the footer behavior!!! -->
    <!-- <DesktopFooter class="left-1/2 transform -translate-x-1/2" hidden sm:block absolute bottom-0 w-full /> -->
  </main>
</template>
