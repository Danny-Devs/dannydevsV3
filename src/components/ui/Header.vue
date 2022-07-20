<script setup>
const props = defineProps({
  color: {
    type: String,
    default: 'bg-cyan-400',
  },
})
</script>

<template>
  <main sm:px-6 container mx-auto dark:bg-slate-900 :class="color" flex justify-between items-center>
    <!-- logo -->
    <router-link to="/">
      <div pl-3 pt-7 pb-4 hover:-translate-y-2px hover:scale-101 sm:active:scale-108 transition>
        <img v-if="!isDark" w-48 src="/dannydevs-logo.png" alt="DannyDevs logo">
        <img v-if="isDark" w-48 src="/dannydevs-logo-cyan.png" alt="DannyDevs logo">
      </div>
    </router-link>
    <!-- end logo -->

    <div flex sm:mt-3 items-center>
      <!-- social links for mobile -->
      <div flex sm:hidden dark:text-cyan-300 mt-3>
        <a href="https://www.linkedin.com/in/danielahn47/" target="_blank" mr-1 text-2xl i-carbon-logo-linkedin />
        <a href="https://twitter.com/dannydevsss" target="_blank" mr-1 text-2xl i-carbon-logo-twitter />
      </div>

      <!-- navigation links for sm: and up -->
      <section hidden sm:block dark:text-cyan-400 mt-1>
        <div class="flex" text-xl>
          <router-link
            to="/lab"
            flex
            items-center
          >
            <p active:scale-110 px-3 py-1 rounded-lg mr-3 hover:bg-cyan-300 transition hover:-translate-y-2px hover:shadow-lg>
              Lab
            </p>
          </router-link>
          <router-link to="/blog" flex items-center>
            <p active:scale-110 px-3 py-1 rounded-lg mr-3 hover:bg-cyan-300 transition hover:-translate-y-2px hover:shadow-lg>
              Blog
            </p>
          </router-link>
          <router-link to="/about" flex items-center>
            <p active:scale-110 px-3 py-1 rounded-lg mr-3 hover:bg-cyan-300 transition hover:-translate-y-2px hover:shadow-lg>
              About
            </p>
          </router-link>
          <router-link to="/links" flex items-center>
            <p active:scale-110 px-3 py-1 rounded-lg mr-6 hover:bg-cyan-300 transition hover:-translate-y-2px hover:shadow-lg>
              Links
            </p>
          </router-link>
        </div>
      </section>
      <!-- end navigation links for sm: and up -->

      <!-- light/dark togle -->
      <div mt-3 sm:mt-0 hover:-translate-y-2px hover:scale-120 transition hover:cursor-pointer @click="toggleDark()">
        <div
          v-if="!isDark"
          mr-2
          text-xl
          i-carbon-moon
        />
        <div
          v-if="isDark"
          mr-2
          text-2xl
          i-carbon-sun
          text-cyan-400
        />
      </div>
      <!-- end light/dark toggle -->
    </div>
  </main>
</template>

<style scoped>
</style>
